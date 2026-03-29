# ⚙️ GoDrive - Centralized Config Server

## 1. Overview
This repository serves as the **Spring Cloud Config Server** for the **GoDrive** microservice ecosystem. It acts as a centralized source for externalized configuration properties across different environments (e.g., development, production).

## 2. Role in Architecture
* **Centralized Configuration:** Provides a single location to manage properties for all microservices in the system.
* **Environment Management:** Supports environment-specific profiles such as default, dev, and prod.
* **Dynamic Updates:** Allows microservices to refresh their configurations without requiring a full system restart.

---

## 3. Technology Stack
* **Language:** Java 25
* **Framework:** Spring Boot
* **Config Engine:** Spring Cloud Config Server
* **Storage Backend:** Git (used to store and version control configuration files)

---

## 4. Configuration Structure
The repository contains specialized configuration properties for the following services:
* `api-gateway.properties` - Routing and security configurations.
* `service-registry.properties` - Eureka server specific settings.
* `vehicle-service.properties` - Database and storage bucket configurations.
* `application.properties` - Common configurations shared across all microservices.

---

## 5. Client Connection (Bootstrap)
Client microservices in the GoDrive ecosystem connect to this server using their `bootstrap.properties` file. This file specifies the Config Server's URI and the application name to fetch the correct configuration at startup.

---

## 6. How to Access
Once the Config Server is deployed and running, the configurations can be accessed via the following URL pattern:
`http://<config-server-ip>:<port>/<service-name>/<profile>`

Example:
`http://localhost:8888/vehicle-service/default`

---

## 7. Reliability & Maintenance
* **Process Management:** Managed by **PM2** to ensure the server starts automatically on VM reboot and restarts if a failure occurs.
* **Fault Tolerance:** Deployed as part of the platform layer with high availability considerations to ensure constant access to configurations for all microservices.
