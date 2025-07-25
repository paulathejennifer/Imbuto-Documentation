# Technical Information

## System Architecture Overview

The Imbuto platform is designed as a **web and mobile application architecture** that supports data management for dairy cooperative operations. It separates concerns between front-end user interfaces, backend services, daily data storage, and external integrations.

### Key Components

- **Mobile App (Farmers):**  
  A React-based mobile application allowing farmers to input milk delivery records, update profiles, receive notifications, and track payments. It communicates with backend APIs over the internet.

- **Web Application (Cooperative Officials):**  
  A React.js application accessed via web browsers. It facilitates membership management, milk record entry, payment processing, and progress tracking dashboards.

- **Backend API Layer:**  
  Developed using Django (Python), the backend has RESTful APIs that provide business logic including user authentication, membership management, milk record handling, payment scheduling, notifications, and data analytics.

- **Database:**  
  SQLite3 serves as the primary relational database storing user profiles, membership details, milk delivery records, payment transactions, and progress tracking data.

- **Notification Services:**  
  SMS APIs are integrated to notify farmers about deliveries and payments.

- **Payment Integration:**  
  The platform integrates with Mpesa Mobile Money (Daraja) API to automate farmer payment disbursements every 15 days, handling transaction initiation, verification, and status updates.

### Data Flow Example (Milk Record Management)

1. Cooperative officials input daily milk deliveries via the web app.  
2. Data is stored in the `milkrecords` table in the SQLite3 database.  
3. Backend triggers an SMS and/or push notification to the farmer with delivery details.  
4. Farmer responds via the mobile app to confirm or dispute.  
5. Backend updates delivery status accordingly, visible in both farmer app and official dashboard.

---

## Technology Stack

| Layer               | Technology / Tools                         | Purpose                                      |
|---------------------|--------------------------------------------|----------------------------------------------|
| Frontend Mobile App  | Android JetPack Compose                    | Farmer interface for milk entries & payments |
| Frontend Web App     | React.js                                   | Cooperative official dashboard & management  |
| Backend API          | Django Rest Framework (Python)             | Business logic, authentication, APIs          |
| Database             | SQLite3                                    | Relational DB for persistent application data|
| Payment Gateway      | Mpesa Mobile Money (Daraja) API integration| Mobile money payment processing                |
| Hosting / Infrastructure | Heroku                                 | Hosting backend APIs, databases, static files |
| Version Control      | Git + GitHub                              | Source code management and deployment          |

---

## Security and Data Privacy

- All communications between app clients and backend APIs use HTTPS for encryption.  
- User data and passwords are securely stored and hashed in the database.  
- Role-based access control ensures cooperative officials have admin rights while farmers have limited, profile-specific access.  
- Password recovery links expire after a controlled period (3 minutes) to enhance security.

---
