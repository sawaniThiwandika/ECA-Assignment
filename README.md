- Reg No- 2301671045
- Name- Sawani Thiwandika 

# ☁️ Cloud Enabled Deployment In Action with AWS

This repository contains four projects:

- **course-service** (Spring Boot + MySQL)  
- **student-service** (Spring Boot + MongoDB)  
- **media-service** (Spring Boot + Local file storage, can be extended to S3/MinIO)  
- **frontend-app** (React + TypeScript + MUI + Axios + Vite)

---

## Backend Services

### 1. course-service
- **Entity:** Course(id, name, duration)  
- **Endpoints:**
  - GET /courses
  - GET /courses/{id}
  - POST /courses
  - DELETE /courses/{id}  
- **Default port:** 8081  
- **Configuration:** Configure MySQL settings in `application-<profile>.properties`

### 2. student-service
- **Document:** Student(registrationNumber, fullName, address, contact, email)  
- **Endpoints:**
  - GET /students
  - GET /students/{id}
  - POST /students
  - DELETE /students/{id}  
- **Default port:** 8082  
- **Configuration:** Configure MongoDB settings in `application-<profile>.properties`

### 3. media-service
- **Resource:** files  
- **Endpoints:**
  - POST /files (multipart/form-data: file)
  - GET /files (list)
  - GET /files/{id} (fetch)
  - DELETE /files/{id} (delete)  
- **Default port:** 8083  
- **Storage:** Uses local disk at `./data/media` by default (override with env var `MEDIA_STORAGE_DIR`)

---

## Frontend (frontend-app)
- **Tech Stack:** React + TypeScript + MUI + Axios + Vite  
- **Sections:** Courses, Students, Media  
- **Scripts:**
```bash
npm run dev      # Start Vite dev server
npm run build    # Build production bundle
npm run preview  # Preview built app
````

---

## Build Instructions

### Backend

```bash
mvn -q -e -DskipTests package
```

### Frontend

```bash
cd frontend-app
npm install
npm run dev
```

---

## Switching Environments (Spring Profiles)

Each backend service can run in different environments:

* **dev** – Local/Docker development
* **gcp** – Google Cloud Platform
* **aws** – AWS deployment

> Select the desired profile—aws, gcp, or dev—based on the environment where you want each service (course-service, student-service, and media-service) to run.

### Set active profile

**Via application.properties:**

```properties
spring.profiles.active=gsp
```

## Notes

GCP Database Security
> If you're using Google Cloud Platform, you'll first need to create a managed Cloud SQL database instance. Once it's set up, you have to configure a crucial security setting. To allow your application to connect, you must explicitly whitelist your public IP address in the database's Networking tab. This acts as a firewall, ensuring that only your designated machine can establish a connection.

AWS Database Security
>If you're using Amazon Web Services (AWS), you'll first need to create a managed database instance using Amazon RDS (Relational Database Service). Once it's set up, you have to configure a crucial security setting. To allow your application to connect, you must explicitly configure the database's security group by adding an inbound rule for your public IP address. This acts as a virtual firewall, ensuring that only your designated machine can establish a connection.
---

##🎥 Video

Watch assignment demonstration here:
https://drive.google.com/file/d/1-5_DuWxb6nZr79Ppzw2Ydm1Ohwm3pENZ/view?usp=drive_link

---

