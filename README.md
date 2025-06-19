# springboot-google-drive-file-downloader

# 📽️ Google Drive Video Downloader (Spring Boot)

This Spring Boot application allows you to **download videos from Google Drive** using a **service account**. It connects to Google Drive API securely and streams the requested file to the client.

---

## 🚀 Features

- Connects to Google Drive API with Service Account
- Downloads video or any file by its File ID
- Streams file directly via HTTP response
- Uses Google API client libraries

---

## 📁 Project Structure

```
src/
 └── main/
     ├── java/
     │   └── com.example.demo/
     │       ├── controller/
     │       │   └── DownloadController.java
     │       └── service/
     │           └── GoogleDriveService.java
     └── resources/
         └── service_account.json  <-- 🔑 Google credentials
```

---

## 🧰 Prerequisites

- Java 17+
- Maven
- Google Cloud Project with Drive API enabled

---

## 🔧 Setup Steps

### 1. Create Google Cloud Project

- Visit [Google Cloud Console](https://console.cloud.google.com/)
- Click **New Project** → Give it a name → Click **Create**

### 2. Enable Drive API

- Go to **APIs & Services > Library**
- Search **Google Drive API**
- Click **Enable**

### 3. Create Service Account

- Navigate to **IAM & Admin > Service Accounts**
- Click **Create Service Account**
- Name: `spring-boot-drive-access`
- Click **Create and Continue**
- Skip roles or assign **Viewer**
- Click **Done**

### 4. Generate and Download JSON Key

- In Service Account > **Keys** tab → Add Key > **Create new key** → Select **JSON**
- Move downloaded `service_account.json` to:  
  `src/main/resources/service_account.json`

### 5. Share File with Service Account

- Go to Google Drive > Right-click file > **Share**
- Add service account email:  
  `spring-boot-drive-access@your-project.iam.gserviceaccount.com`
- Set permission to **Viewer**

---

## ▶️ How to Run

```bash
mvn spring-boot:run
```

Then visit in browser or use Postman:

```
GET http://localhost:8080/video/download/{fileId}
```

Replace `{fileId}` with the actual Google Drive File ID.

---

## 🛠️ Technologies Used

- Java 17
- Spring Boot 3.5.0
- Google Drive API v3
- Maven

---

## 📦 Dependencies

```xml
<dependencies>
    <!-- Spring Web -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- Google API Dependencies -->
    <dependency>
        <groupId>com.google.api-client</groupId>
        <artifactId>google-api-client</artifactId>
        <version>2.2.0</version>
    </dependency>
    <dependency>
        <groupId>com.google.auth</groupId>
        <artifactId>google-auth-library-oauth2-http</artifactId>
        <version>1.19.0</version>
    </dependency>
    <dependency>
        <groupId>com.google.http-client</groupId>
        <artifactId>google-http-client-gson</artifactId>
        <version>1.44.1</version>
    </dependency>
    <dependency>
        <groupId>com.google.apis</groupId>
        <artifactId>google-api-services-drive</artifactId>
        <version>v3-rev197-1.25.0</version>
    </dependency>
</dependencies>
```

---

## 👨‍💻 Author

Developed by [Sharad Kamble](https://github.com/sharad-kamble)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
