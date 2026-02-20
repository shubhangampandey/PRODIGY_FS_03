

## What technologies are used for this project?

This project is built with:

- Vite
- TypeScript
- React
- shadcn-ui
- Tailwind CSS
- mongodb
- cloudinary 

# Udrcraft Backend

Express + Mongoose backend for the UDRcraft e-commerce platform.

## Setup

```bash
cd server
npm install
```

## Configure in backend .env

.env - fill in your MongoDB URI and JWT secret.
MONGO_URI=
JWT_SECRET=maison_jwt_secret_2026_change_in_production
PORT=5000
CLOUD_NAME=
CLOUD_API_KEY=
CLOUD_API_SECRET=


## Seed Database

```bash
npm run seed
```

This creates demo users, products, and orders.

### Demo Credentials
| Role     | Email                      | Password    |
|----------|----------------------------|-------------|
| Admin    | admin@maison.com           | admin123    |
| Vendor   | vendor@nordicliving.com    | vendor123   |
| Vendor   | vendor@atelier.com         | vendor123   |
| Customer | customer@example.com       | customer123 |

## Run

```bash
npm run dev   # development with nodemon
npm start     # production
```

Server runs on `http://localhost:5000` by default.

## API Endpoints

### Auth
- `POST /api/auth/register` — Register user
- `POST /api/auth/login` — Login, returns JWT
- `GET /api/auth/me` — Get current user (auth required)
- `PUT /api/auth/profile` — Update profile (auth required)

### Products
- `GET /api/products` — List approved products (public)
- `GET /api/products/all` — List all products (admin)
- `GET /api/products/vendor/:vendorId` — Vendor's products (auth)
- `GET /api/products/:id` — Single product (public)
- `POST /api/products` — Create product with image upload (vendor)
- `PUT /api/products/:id` — Update product (auth)
- `DELETE /api/products/:id` — Delete product (auth)
- `PUT /api/products/:id/approve` — Toggle approval (admin)

### Orders
- `GET /api/orders` — All orders (admin)
- `GET /api/orders/customer/:id` — Customer orders (auth)
- `GET /api/orders/vendor/:id` — Vendor orders (auth)
- `GET /api/orders/track/:orderId` — Track order (public)
- `POST /api/orders` — Create order (auth)
- `PUT /api/orders/:id/status` — Update status (auth)

### Users (Admin)
- `GET /api/users` — List all users
- `PUT /api/users/:id/status` — Update user status
- `PUT /api/users/:id/role` — Update user role
- `DELETE /api/users/:id` — Delete user

### Analytics
- `GET /api/analytics/admin` — Platform stats (admin)
- `GET /api/analytics/vendor/:id` — Vendor stats (auth)

### Search
- `GET /api/search?q=term` — Search products (public)

## Deploy

Deploy to Railway, Render, or any Node.js host. Set environment variables:
- `MONGO_URI`
- `JWT_SECRET`
- `PORT` (optional, defaults to 5000)

