# URO Flood Lab Web Platform

A full-stack web application for running and visualizing flood simulation models. This platform provides a user-friendly interface for researchers to upload data, execute complex models, and analyze the results.

## Features

-   **User Authentication:** Secure user registration and login.
-   **Admin Panel:** For user and feedback management.
-   **Model Execution:** Supports various flood models (Inundation, Storm Surge, etc.) via a dedicated worker service.
-   **Result Visualization:** Interactive plots of simulation results using Plotly.js.
-   **Simulation History:** Tracks user's past simulations.
-   **Feedback System:** Allows users to submit feedback.

## System Architecture

The application uses a microservices-oriented architecture:
1.  **Frontend:** A React single-page application for the user interface.
2.  **Backend:** A Node.js/Express server for API, auth, and managing model requests.
3.  **Model Worker:** A separate Node.js service that accepts model execution requests via HTTP and runs the heavy computation.

## Technologies Used

-   **Frontend:** React, React Router, Axios, Plotly.js, Tailwind CSS, Vite
-   **Backend:** Node.js, Express, MongoDB, Mongoose, JWT, Multer
-   **Model Worker:** Node.js, Express, `child_process`
-   **Database:** MongoDB

## Prerequisites

-   Node.js (v14+)
-   npm (v6+)
-   MongoDB

## Installation

1.  Clone the repository:
    ```bash
    git clone [https://github.com/your-username/URO-Flood-Lab-Web-Platform.git](https://github.com/your-username/URO-Flood-Lab-Web-Platform.git)
    cd URO-Flood-Lab-Web-Platform
    ```

2.  **Setup Backend:**
    ```bash
    cd backend
    npm install
    # Create a .env file with:
    # PORT=5000
    # MONGODB_URI=your_mongodb_connection_string
    # JWT_SECRET=your_jwt_secret
    # MODEL_WORKER_URL=http://localhost:5001
    ```

3.  **Setup Frontend:**
    ```bash
    cd ../frontend
    npm install
    # Create a .env file with VITE_BACKEND_API_URL=http://localhost:5000/api
    ```

4.  **Setup Model Worker:**
    ```bash
    cd ../model-worker
    npm install
    # Create a .env file with:
    # PORT=5001
    # FLOOD_MODEL_EXE_PATH=path/to/your/flood_model.exe
    ```

## Running the Application

Start each service in a separate terminal:

1.  **Backend:** `cd backend && npm start`
2.  **Frontend:** `cd frontend && npm run dev`
3.  **Model Worker:** `cd model-worker && npm start`

Access the web app via the frontend URL (usually `http://localhost:5173`).

## Project Structure
```
URO-Flood-Lab-Web-Platform/
├── backend/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   └── server.js
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/
│       ├── pages/
│       └── ...
└── model-worker/
├── FloodModel/       # Contains the executable and input templates
└── worker.js         # Express server that runs the model executable
```

## API Endpoints

Key endpoints are prefixed with `/api`.
-   `POST /api/users/signup`
-   `POST /api/users/login`
-   `POST /api/model/run` (Executes the simulation and returns results directly)
-   `GET /api/history/:modelName`
-   `POST /api/feedback`

## Contributing

Contributions are welcome. Please fork the repository and submit a pull request.
