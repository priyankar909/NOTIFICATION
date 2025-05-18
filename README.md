This is a complete Notification Service built using Spring Boot, supporting the following types of notifications:

✅ Email (via JavaMail)

✅ SMS (via Twilio)

✅ In-App/WebSocket (via STOMP over WebSocket)

It also provides a REST API to send and fetch notifications.

🛠 Technologies Used

Java 17

Spring Boot 3.x

Spring Web

Spring WebSocket

Spring Mail

Twilio SDK

SockJS & STOMP

Postman / cURL for API testing

📦 Setup & Configuration

1. Clone the Repository

git clone https://github.com/your-username/notification-service.git
cd notification-service

2. Update Configuration

Edit application.properties:

🔐 Twilio (for SMS)

twilio.account.sid=YOUR_TWILIO_ACCOUNT_SID
twilio.auth.token=YOUR_TWILIO_AUTH_TOKEN
twilio.from.phone=+1XXXXXXXXXX

📧 Gmail (for Email)

spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your_email@gmail.com
spring.mail.password=your_app_password
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
spring.mail.properties.mail.smtp.starttls.required=true
spring.mail.properties.mail.smtp.ssl.trust=smtp.gmail.com

⚠️ Use App Password from Gmail if 2FA is enabled.

🚀 Running the Application

./mvnw spring-boot:run

Default port: 9090

📡 WebSocket Test

Open your test HTML client or React app and connect to:

/ws

Subscribe to:

/topic/notifications/{userId}

📘 REST API Documentation

✅ 1. Send a Notification

POST /notifications

{
  "userId": "+91xxxxxxxxxx",    // or email or userId
  "message": "Hello from the app!",
  "type": "SMS"                  // SMS, EMAIL, IN_APP
}

✅ 2. Get All Notifications for a User

GET /users/{userId}/notifications

Example:

GET http://localhost:9090/users/user123/notifications

🧪 Testing With Postman

POST /notifications with type: EMAIL, SMS, or IN_APP

GET /users/{userId}/notifications to view past messages

Use WebSocket client (SockJS + STOMP) for in-app messages
