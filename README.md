# 🎟️ EventBookingApp

**EventBookingApp** is a full-stack microservices-based event booking system built with **Spring Boot**, **React**, **Stripe**, **RabbitMQ**, **MySQL**, and **Redis**. 
It allows users to browse events, book tickets (REGULAR/VIP), make payments, and receive real-time notifications.

---

## 🧩 Architecture Overview

The application is built with a **microservice architecture** using:

- **Spring Boot** for backend services
- **React.js** for the frontend
- **RabbitMQ** for asynchronous event-driven communication
- **Stripe** for secure online payments
- **MySQL** for persistent data storage
- **Redis** for caching

---

## 🏗️ Microservices

| Service             | Responsibility                                             |
|---------------------|-------------------------------------------------------------|
| **Event Service**   | Manage events, seat types, pricing (including surge logic) |
| **Booking Service** | Handle ticket reservations, status updates                 |
| **Payment Service** | Stripe payment integration, transaction handling           |
| **Notification Service** | Email/SMS/push notifications post-booking/payment      |
| **API Gateway**     | Route requests to appropriate services                     |

---

## 🔑 Features

- 🗓️ Create, update, view, and cancel events
- 🎟️ Book tickets (VIP/Regular), view availability
- 💳 Secure Stripe payment integration
- 📬 Real-time notifications (email, SMS, push)
- 📈 Surge pricing based on demand
- 🔁 Event-driven flow via RabbitMQ
- 🛡️ JWT-based authentication and authorization
- ⚡ Redis caching for event listings

---

## ⚙️ Tech Stack

- **Backend**: Java 17, Spring Boot 3, Spring Data JPA, Spring Security
- **Frontend**: React.js, Axios, TailwindCSS
- **Database**: MySQL, Redis
- **Queue**: RabbitMQ
- **Payments**: Stripe
- **Other**: Lombok, MapStruct, Docker, Swagger

---

## 🧪 Setup Instructions

### 🔧 Prerequisites
- Java 17
- Node.js + npm
- Docker + Docker Compose
- MySQL & Redis (or run via Docker)

### 🚀 Run Backend Services


# Start RabbitMQ, MySQL, Redis (optional: use docker-compose)
docker-compose up -d

# Run each service
cd event-service
./mvnw spring-boot:run

cd booking-service
./mvnw spring-boot:run

cd payment-service
./mvnw spring-boot:run

cd notification-service
./mvnw spring-boot:run

cd api-gateway
./mvnw spring-boot:run


***RabbitMQ Event Flows***
BookingService → [BookingCreatedEvent] → PaymentService
PaymentService → [PaymentStatusEvent] → BookingService
BookingService → [BookingConfirmedEvent] → NotificationService

