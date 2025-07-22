# MIC Project Cycle Demo - Docker Compose Setup

This repository contains a **sample Docker Compose-based development environment** for the **AI Resume Builder project** and **AI Academic Assistant** under the MIC project cycle. It sets up multiple services—FastAPI, Flask, Node.js, PostgreSQL, MySQL, and Redis—using Docker for easy local development and team collaboration.

---

## 📁 Project Structure
```
docker-setup-test/
├── backend/
│ ├── fastapi/
│ │ ├── app.py
│ │ ├── requirements.txt
│ │ └── Dockerfile
│ ├── flask/
│ │ ├── app.py
│ │ ├── requirements.txt
│ │ └── Dockerfile
├── frontend/
│ ├── app.js
│ ├── package.json
│ └── Dockerfile
├── docker-compose.yaml
```
## What is a Docker Compose File?

A `docker-compose.yaml` file defines and runs **multi-container Docker applications**. Instead of running each container manually, Docker Compose lets you **define all services in one place** and bring them up with a single command.

In this setup, Docker Compose:

- Builds and runs containers for FastAPI, Flask, and Node.js
- Sets up Redis, PostgreSQL, and MySQL databases
- Creates persistent volumes for database data
- Manages service dependencies and networking

---

## Services Included

| Service   | Tech        | Port    | Description                             |
|-----------|-------------|---------|-----------------------------------------|
| `frontend`| Node.js     | `3000`  | Simple HTTP server                      |
| `fastapi` | FastAPI     | `8001`  | Backend API (Python)                    |
| `flask`   | Flask + Redis | `8000`| Hit counter with Redis integration      |
| `postgres`| PostgreSQL  | `5432`  | Relational DB for FastAPI               |
| `mysql`   | MySQL       | `3306`  | Alternative relational DB               |
| `redis`   | Redis       | `6379`  | In-memory store for Flask hit counter   |

---
## How to Clone and Run

### ✅ Step-by-step for All Operating Systems:

---
1. Install Docker from:
   ```https://docs.docker.com/compose/install/```

Confirm Docker is working:

```
docker --version
docker compose version
```

### Linux / macOS

2. **Clone the repository:**

```
git clone https://github.com/sanjaydinesh19/docker-setup-test.git
cd docker-setup-test
```
3. Start Services
```
docker compose up --build
```
4. Visit
   ```
   -> http://localhost:3000 → Node.js

   -> http://localhost:8000 → Flask

   -> http://localhost:8001 → FastAPI
   ```

### Windows

⚠️ Make sure Docker Desktop is running and WSL 2 is properly configured.
Follow the same instructions as above to clone the repo and start services

### Persistent Volumes

Docker volumes are used to persist data for PostgreSQL and MySQL across container restarts:
```
volumes:
  pgdata:
  mysqldata:
```
These volumes are automatically created when you run Docker Compose and store database data even if containers are stopped or rebuilt.

### 📌 Notes

    This is a test environment and not production-optimized.

    You can expand this setup to integrate OpenAI Agent SDK inside FastAPI.

    Suitable for cross-platform development (Ubuntu, macOS, Windows).


