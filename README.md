# config-server

> **Student Name:** \<Your Full Name\>
> **Student Number:** \<Your Student Number\>
> **Slack Handle:** \<optional\>
> **GCP Project ID:** \<your-gcp-project-id\>

## Project Description

Spring Cloud Config Server for the Hotel Booking microservices system. It
centralizes and externalizes configuration (ports, datasource URLs, Eureka
addresses, GCS bucket names, gateway routes, etc.) for every other
microservice so that none of them hardcode environment-specific values.
Configuration is served from the bundled [`config-repo`](./src/main/resources/config-repo)
directory (native profile) — see `application.yml` for how to switch it to a
real Git-backed repository instead.

## Technology Stack

- Java 25
- Spring Boot 4.1.0
- Spring Cloud Config Server 2025.1.2
- Spring Boot Actuator
- Maven Wrapper

## Setup / Getting Started

```bash
./mvnw spring-boot:run
```

Runs on **port 8888** by default. Verify a client config is served:

```bash
curl http://localhost:8888/eureka-server/default
curl http://localhost:8888/api-gateway/default
```

### Build & run the jar (as used by PM2 in production)

```bash
./mvnw clean package -DskipTests
java -jar target/config-server-0.0.1-SNAPSHOT.jar
```

### Key environment variables

| Variable | Purpose | Default |
|---|---|---|
| `SERVER_PORT` | HTTP port | `8888` |
| `CONFIG_REPO_URI` | Git URL to back config with (optional; native/bundled files are used otherwise) | *(empty)* |
