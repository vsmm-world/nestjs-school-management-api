# Learn NestJS — School Management API

A learning project built to get hands-on with [NestJS](https://nestjs.com/), Prisma, and MongoDB by modeling a small school management system: students, teachers, classes, subjects, timetables, and attendance.

## Features

- **Auth** — JWT-based authentication with OTP email verification (Postmark/Mailgun/SendGrid)
- **User** — account management with soft-delete (`isDeleted`) and audit fields (`createdBy`/`updatedBy`/`deletedBy`) on every entity
- **Student** — CRUD, linked to a class
- **Teacher** — CRUD, linked to a subject and a favorite student
- **Class** (`School_class`) — groups students, has a timetable and attendance records
- **Subjects** — CRUD, assignable to teachers
- **Timetable** — per-class, per-day schedule linking teachers to classes
- **Attendance** — per-student, per-class attendance records by date
- **Task** — misc scheduled/background task handling
- **Swagger** — interactive API docs generated from decorators

## Tech Stack

- [NestJS 10](https://nestjs.com/) (TypeScript)
- [Prisma](https://www.prisma.io/) ORM on **MongoDB**
- Passport + `@nestjs/jwt` for authentication
- Postmark / Mailgun / SendGrid for transactional email (OTP delivery)
- Swagger (`@nestjs/swagger`) for API documentation
- Jest for unit/e2e testing

## Project Structure

```
src/
├── auth/         # login, JWT strategy, OTP verification
├── user/         # user accounts
├── student/      # student CRUD
├── teacher/      # teacher CRUD
├── class/        # school classes
├── subjects/     # subjects CRUD
├── timetable/    # class timetables
├── attendance/   # attendance records
├── task/         # background/scheduled tasks
├── validator/    # custom DTO validators
└── prisma/       # Prisma service/module
prisma/
└── schema.prisma # data model (MongoDB)
```

## Getting Started

### Prerequisites
- Node.js 18+
- A MongoDB connection string (Prisma requires a replica-set enabled MongoDB instance)
- A Postmark API key (used for OTP emails)

### Setup

```bash
git clone https://github.com/vsmm-world/Learn-Nestjs-from-Starting.git
cd Learn-Nestjs-from-Starting
npm install
```

Create a `.env` file in the project root:

```bash
DATABASE_URL="mongodb+srv://<user>:<password>@<cluster>/<db>?retryWrites=true&w=majority"
POST_MARK_API_KEY="your-postmark-api-key"
```

Generate the Prisma client and sync the schema:

```bash
npm run prisma-all
```

Run the app:

```bash
npm run start:dev
```

The API will be available at `http://localhost:3000`, with Swagger docs at `http://localhost:3000/api`.

### Tests

```bash
npm run test        # unit tests
npm run test:e2e     # e2e tests
npm run test:cov     # coverage report
```

## Author

**Ravindra Valand**
- GitHub: [@vsmm-world](https://github.com/vsmm-world)
- LinkedIn: [Ravindra Valand](https://in.linkedin.com/in/ravindra-valand)
- Instagram: [@ravindra_valand](https://www.instagram.com/ravindra_valand/)

## License

UNLICENSED — personal learning project, not intended for production use.
