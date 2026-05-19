# StudyNook – Library Study Room Booking

A full-stack web application where students and library users can list and book study rooms. Built with React, Node.js, Express, and MongoDB.

🌐 **Live Site URL**: [https://studynook.vercel.app](https://studynook.vercel.app)

## Features

- **Room Listings** – Browse, search, and filter available study rooms by name, amenities, and price range
- **Booking System** – Book rooms for specific dates and time slots with real-time conflict detection to prevent double-booking
- **User Authentication** – Secure JWT-based authentication stored in HTTP-only cookies, with email/password and Google OAuth support
- **Room Management** – Room owners can add, edit, and delete their own listings with full CRUD operations
- **Dark/Light Theme** – Toggle between dark and light modes with persistent preference saved in localStorage

## Tech Stack

### Frontend
- React 19 + Vite
- React Router DOM v7
- Tailwind CSS v4
- Framer Motion (animations)
- React Hot Toast (notifications)
- React Icons

### Backend
- Node.js + Express 5
- MongoDB + Mongoose
- JSON Web Token (JWT) + HTTP-only cookies
- BcryptJS (password hashing)
- Google Auth Library

## Getting Started

### Prerequisites
- Node.js 18+
- MongoDB (local or Atlas)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/studynook.git
cd studynook
```

2. Install server dependencies:
```bash
cd server
npm install
```

3. Install client dependencies:
```bash
cd ../client
npm install
```

4. Create `.env` files:

**server/.env**
```
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLIENT_URL=http://localhost:5173
GOOGLE_CLIENT_ID=your_google_client_id
```

**client/.env**
```
VITE_API_URL=http://localhost:5000/api
```

5. Start the server:
```bash
cd server
npm run dev
```

6. Start the client:
```bash
cd client
npm run dev
```

## Project Structure

```
├── client/                 # React frontend
│   └── src/
│       ├── api/            # Axios configuration
│       ├── components/     # Reusable components
│       ├── context/        # Auth & Theme contexts
│       ├── layouts/        # Public/Private layouts
│       └── pages/          # Page components
├── server/                 # Node.js backend
│   ├── config/             # DB configuration
│   ├── middleware/         # Auth middleware
│   ├── models/             # Mongoose models
│   └── routes/             # Express routes
└── README.md
```

## API Endpoints

### Auth
- `POST /api/auth/register` – Register new user
- `POST /api/auth/login` – Login user
- `POST /api/auth/google` – Google OAuth login
- `GET /api/auth/me` – Get current user
- `POST /api/auth/logout` – Logout user

### Rooms
- `GET /api/rooms` – Get all rooms (with search/filter)
- `GET /api/rooms/latest` – Get latest 6 rooms
- `GET /api/rooms/:id` – Get room by ID
- `POST /api/rooms` – Create room (auth required)
- `PUT /api/rooms/:id` – Update room (owner only)
- `DELETE /api/rooms/:id` – Delete room (owner only)

### Bookings
- `GET /api/bookings/my-bookings` – Get user's bookings (auth required)
- `POST /api/bookings` – Create booking (auth required)
- `PATCH /api/bookings/:id/cancel` – Cancel booking (auth required)
