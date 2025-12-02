# **GymTech Backend**

The **GymTech Backend** is a robust Spring Boot application designed to manage a complete gym registration and scheduling system. It provides APIs for handling members, owners, training sessions, and registration workflows. The system follows a clean layered architecture—Controller → Service → Repository → Model—ensuring scalability, maintainability, and clean separation of concerns.

This backend is suitable for any gym, fitness club, or training center workflow, and can serve as the foundation for a production-grade fitness management software.

---

## ⚙️ **Key Functionalities**

### **1. Member Management**

* Register new members
* Update existing member profiles
* Fetch member details using unique identifiers
* Validate inputs and prevent invalid operations
* Remove members safely with referential checks

### **2. Owner Management**

* Create and manage gym owners
* Link owners to the gym system
* Ensure owners are handled separately from normal members
* Serve administrative or elevated roles

### **3. Session Scheduling & Booking**

* Create gym training sessions
* Define session timings, available slots, and trainers
* Register members for sessions
* Prevent:

  * Overlapping sessions
  * Duplicate bookings
  * Exceeding maximum capacity

### **4. Complete REST API Layer**

* Clean, predictable API design
* JSON-based request/response handling
* Works seamlessly with any frontend (React, Flutter, Android, etc.)
* Request validation and standardized responses

### **5. Exception Handling Framework**

* Centralized exception handling using:

  * `GRSException`
  * `GRSExceptionHandler`
* Clear error messages for:

  * Invalid inputs
  * Business logic violations
  * Missing resources

### **6. Persistence & Database Architecture**

* Spring Data JPA repositories
* Database-agnostic configuration
* Entity relationships for Session ↔ Member mapping
* Automatic schema management via Hibernate

### **7. CORS Enabled for Frontend Integration**

* Global CORS configuration using:

  * `CorsConfig.java`
* Enables smooth communication with any frontend domain

### **8. Full Test Coverage**

* Unit tests for service logic
* Integration tests combining service + repository
* Test suite ensures:

  * Validation logic
  * Session booking constraints
  * CRUD operations

---

## 🏗 **Technology Stack**

| Layer             | Technology / Tool                    |
| ----------------- | ------------------------------------ |
| Backend Framework | Spring Boot                          |
| Language          | Java                                 |
| Build Tool        | Gradle                               |
| Persistence Layer | Spring Data JPA + Hibernate          |
| Database          | Configurable (H2, MySQL, PostgreSQL) |
| Testing Framework | JUnit + Mockito                      |
| API Style         | RESTful Architecture                 |

---

## 📁 **Project Directory Structure (Detailed)**

```
src/
└── main/
    ├── java/
    │   └── ca/mcgill/ecse321/gymregistration/
    │       ├── controller/     # REST endpoints for Person, Owner, Session
    │       ├── service/        # Business logic & validation rules
    │       ├── repository/     # JPA repositories for data access
    │       ├── model/          # Entity models: Person, Owner, Session, etc.
    │       ├── dto/            # Request/response data transfer objects
    │       ├── config/         # CORS configuration
    │       └── exception/      # Custom exceptions + global handlers
    │
    └── resources/
        ├── application.properties  # DB config, ports, Hibernate settings
        └── static/                 # Static resources (if needed)
        
tests/
└── java/
    └── ca/mcgill/ecse321/gymregistration/
        ├── service/         # Service-level unit tests
        └── repository/      # Database integration tests
```

---

## 🚀 **How to Run the Backend**

### **1. Prerequisites**

* Java 17 or higher
* Gradle (or use included `./gradlew`)
* A database (H2, MySQL, or PostgreSQL)

### **2. Clone the Repository**

```bash
git clone https://github.com/wittyswayam/GymTech-Automation.git
cd GymTech-Automation
```

### **3. Run the Application**

```bash
./gradlew bootRun
```

### **4. Access the Backend**

```
http://localhost:8080
```

---

## 🔧 **Configuration Guide**

The file `src/main/resources/application.properties` contains all configurations.

### **Database Configuration Example**

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/gymtech
spring.datasource.username=root
spring.datasource.password=yourpassword

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### **Port Configuration**

```properties
server.port=8080
```

### **CORS Configuration**

Handled in `CorsConfig.java`:

* Accepts all frontend domains
* Can be customized based on environment

---

## 🔗 **API Overview (Detailed)**

### **Person / Member API**

| Method | Endpoint        | Description           |
| ------ | --------------- | --------------------- |
| POST   | `/persons`      | Create a new member   |
| GET    | `/persons/{id}` | Fetch member by ID    |
| PUT    | `/persons/{id}` | Update member details |
| DELETE | `/persons/{id}` | Delete a member       |

---

### **Session API**

| Method | Endpoint                                    | Description                     |
| ------ | ------------------------------------------- | ------------------------------- |
| POST   | `/sessions`                                 | Create a new training session   |
| GET    | `/sessions`                                 | Get all sessions                |
| GET    | `/sessions/{id}`                            | Get a single session            |
| POST   | `/sessions/{sessionId}/register/{personId}` | Register a member for a session |

---

### **Owner API**

| Method | Endpoint       | Description            |
| ------ | -------------- | ---------------------- |
| POST   | `/owners`      | Create a new owner     |
| GET    | `/owners/{id}` | Retrieve owner details |

---

## 🧪 **Testing Instructions**

### **Run All Tests**

```bash
./gradlew test
```

### **What the Tests Cover**

* Person service CRUD logic
* Owner service validations
* Session booking constraints
* Database read/write behavior
* Exception mapping and error flow

---

## 🤝 **Contributions & Extensibility**

You may extend this backend by adding:

* Authentication (JWT, OAuth2)
* Admin dashboards
* Payment integration
* Attendance tracking
* Trainer profiles
* Membership plans

The architecture is designed to scale smoothly.

---
