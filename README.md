# 🏡 Airbnb Clone Project

## 📘 Overview
The Airbnb Clone project is a full-featured web application designed to emulate the core functionality of the Airbnb platform.  
It allows users to book stays, list properties, and manage reservations through a modern and responsive interface.  
This project is intended as a learning and portfolio-building tool for aspiring full-stack developers and software engineers.

## 🎯 Project Goal
The goal of this project is to replicate the primary features of Airbnb by implementing a robust backend system,  
efficient API layer, and scalable services using industry-standard tools and practices.  
It also focuses on implementing asynchronous task handling, data caching, containerized environments,  
and continuous integration/deployment pipelines.

---

## 👥 Team Roles

Understanding the different roles within a software project team is crucial for clear communication and successful collaboration.  
Below are the primary roles involved in the Airbnb Clone project and their responsibilities:

### 🧠 Project Manager
Coordinates the entire project lifecycle including planning, execution, and delivery.  
Ensures milestones are met and maintains communication between team members.

### 🛠 Backend Developer
Responsible for creating and managing server-side logic, RESTful APIs, and integrating with the database.  
Implements business logic and security layers.

### 🎨 Frontend Developer
Implements user-facing features using modern UI libraries or frameworks.  
Ensures the interface is responsive, intuitive, and consumes backend APIs effectively.

### 🗃️ Database Administrator (DBA)
Designs, maintains, and optimizes the relational database schema.  
Ensures data integrity, availability, and performance tuning.

### 🔗 DevOps Engineer
Manages CI/CD pipelines, containerization, and deployment workflows.  
Ensures the infrastructure is stable, secure, and scalable.

### 🚀 QA Engineer
Tests functionality across the system, ensuring features work as intended.  
Responsible for writing and running unit, integration, and end-to-end tests.

### 🧪 API Integration Specialist
Works closely with frontend and backend developers to ensure seamless and well-documented API usage.

### 🔁 Task Scheduler / Async Engineer
Implements background task handling using tools like Celery and Redis.  
Handles non-blocking operations such as email notifications and payment processing.

---

## 🧰 Technology Stack

This project utilizes a modern, scalable tech stack to deliver efficient backend performance and development workflows:

- **Django**: A high-level Python web framework used for building the RESTful API and handling backend logic.
- **Django REST Framework**: A powerful toolkit that simplifies the creation of REST APIs in Django.
- **PostgreSQL**: A robust relational database system used for persistent data storage and complex queries.
- **GraphQL**: Provides a flexible approach to querying data and helps reduce over-fetching or under-fetching of data in APIs.
- **Celery**: A distributed task queue used for handling asynchronous operations like email delivery and background tasks.
- **Redis**: Serves as a fast in-memory data store used for caching, queuing, and session management.
- **Docker**: Ensures consistency across development, testing, and production environments through containerization.
- **CI/CD Pipelines (e.g., GitHub Actions)**: Automates code testing, building, and deployment to speed up development and reduce human error.

---

## 🗄️ Database Design

This section outlines the key entities and their relationships for the Airbnb Clone project.  
The database is designed to support scalability, integrity, and efficient querying across all core functionalities.

### 🔐 Users
Represents both guests and hosts using the platform.

**Fields:**
- `id` (Primary Key)
- `name` (String)
- `email` (Unique String)
- `password` (Hashed String)
- `is_host` (Boolean)

**Relationships:**
- A user can own multiple properties.
- A user can make multiple bookings.
- A user can leave multiple reviews.

---

### 🏠 Properties
Represents listings made by hosts.

**Fields:**
- `id` (Primary Key)
- `title` (String)
- `description` (Text)
- `price_per_night` (Decimal)
- `owner_id` (Foreign Key → Users)

**Relationships:**
- A property is owned by one user (host).
- A property can have multiple bookings.
- A property can receive multiple reviews.

---

### 📅 Bookings
Represents reservation details for stays.

**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `check_in_date` (Date)
- `check_out_date` (Date)

**Relationships:**
- A booking is made by one user.
- A booking belongs to one property.

---

### 📝 Reviews
Captures user feedback about a property.

**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `property_id` (Foreign Key → Properties)
- `rating` (Integer: 1–5)
- `comment` (Text)

**Relationships:**
- A review is written by a user.
- A review is for one property.

---

### 💳 Payments
Stores payment transaction data.

**Fields:**
- `id` (Primary Key)
- `user_id` (Foreign Key → Users)
- `booking_id` (Foreign Key → Bookings)
- `amount` (Decimal)
- `status` (Enum: Pending, Completed, Failed)

**Relationships:**
- A payment is associated with a booking.
- A payment is made by one user.

---

### 🔄 Entity Relationship Summary

- **User ↔ Properties**: One-to-Many (Host can list multiple properties)  
- **User ↔ Bookings**: One-to-Many (User can make multiple bookings)  
- **User ↔ Reviews**: One-to-Many (User can leave multiple reviews)  
- **Property ↔ Bookings**: One-to-Many (Property can be booked many times)  
- **Property ↔ Reviews**: One-to-Many (Property can have many reviews)  
- **Booking ↔ Payments**: One-to-One (Each booking has a single payment)
