# Smart Task & Team Management System

A modern web application for managing projects, tasks, and team collaboration. Built with Flask backend and React frontend.

## 🎯 Features

- **User Authentication**: Secure login/registration with JWT tokens
- **Project Management**: Create and manage multiple projects
- **Task Management**: Create, assign, and track tasks with status updates
- **Team Collaboration**:
  - Add team members to projects
  - Assign tasks to team members
  - Comments on tasks
  - File attachments
- **Analytics Dashboard**: 
  - Admin dashboard with project/task statistics
  - User dashboard with personal task overview
- **Role-Based Access**: Admin and User roles with different permissions
- **File Upload**: Attach files to tasks and comments

## 🛠️ Tech Stack

### Backend
- **Framework**: Flask 3.0.3
- **Database**: MySQL
- **ORM**: SQLAlchemy (Flask-SQLAlchemy)
- **Authentication**: JWT (Flask-JWT-Extended)
- **CORS**: Flask-CORS

### Frontend
- **Framework**: React 18
- **Build Tool**: Vite
- **Routing**: React Router
- **HTTP Client**: Axios

## 📦 Project Structure

```
.
├── backend/                  # Flask backend
│   ├── app.py              # Main Flask app
│   ├── config.py           # Configuration
│   ├── requirements.txt     # Python dependencies
│   ├── controllers/        # Request handlers
│   ├── models/             # Database models
│   ├── routes/             # API endpoints
│   ├── middleware/         # Auth middleware
│   ├── utils/              # Helper functions
│   └── myvenv/             # Virtual environment
│
├── frontend/               # React frontend
│   ├── src/
│   │   ├── components/     # React components
│   │   ├── pages/          # Page components
│   │   ├── context/        # Auth context
│   │   ├── services/       # API service
│   │   └── assets/         # Static assets
│   ├── package.json        # Node dependencies
│   └── vite.config.js      # Vite configuration
│
└── README.md               # This file
```

## 🚀 Quick Start

### Prerequisites
- Python 3.9+
- Node.js 16+
- MySQL Server

### Backend Setup

1. **Navigate to backend folder**
   ```bash
   cd backend
   ```

2. **Activate virtual environment**
   ```bash
   # Windows
   myvenv\Scripts\activate
   
   # macOS/Linux
   source myvenv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure database** (Update in `config.py`)
   ```python
   SQLALCHEMY_DATABASE_URI = 'mysql+pymysql://user:password@localhost/database_name'
   ```

5. **Create admin user**
   ```bash
   python seed_admin.py
   ```

6. **Run backend server**
   ```bash
   python app.py
   ```
   Backend runs on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend folder**
   ```bash
   cd frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run development server**
   ```bash
   npm run dev
   ```
   Frontend runs on `http://localhost:5173`

### Quick Start Batch Files (Windows)

```bash
# Terminal 1 - Backend
start-backend.bat

# Terminal 2 - Frontend
start-frontend.bat

# Seed admin user
seed-admin.bat
```

## 📚 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user

### Projects
- `GET /api/projects` - List all projects
- `POST /api/projects` - Create project
- `GET /api/projects/<id>` - Get project details
- `PUT /api/projects/<id>` - Update project
- `DELETE /api/projects/<id>` - Delete project

### Tasks
- `GET /api/tasks` - List tasks
- `POST /api/tasks` - Create task
- `GET /api/tasks/<id>` - Get task details
- `PUT /api/tasks/<id>` - Update task
- `DELETE /api/tasks/<id>` - Delete task

### Comments
- `POST /api/comments` - Add comment to task
- `GET /api/comments/task/<task_id>` - Get task comments
- `DELETE /api/comments/<id>` - Delete comment

### Analytics
- `GET /api/analytics/dashboard` - Dashboard data (admin/user specific)

## 🔐 Default Admin Account

After running `seed_admin.py`:
- **Email**: admin@example.com
- **Password**: admin123

⚠️ Change these credentials in production!

## 📝 Database Models

### User
- Stores user information and roles (admin/user)
- Relationships: projects created, tasks assigned, comments, attachments

### Project
- Project information with description and deadline
- Many-to-many relationship with users (members)
- One-to-many with tasks

### Task
- Task details with status (todo/in_progress/completed)
- Priority levels (low/medium/high)
- Assigned to users
- Has comments and attachments

### Comment
- Task comments with author information
- Supports file attachments

### Attachment
- File uploads linked to tasks or comments

## 🔧 Configuration

Update `backend/config.py` for:
- Database connection
- JWT secret key
- Upload folder path
- CORS origins

```python
# Example
SQLALCHEMY_DATABASE_URI = 'mysql+pymysql://root:password@localhost/task_db'
JWT_SECRET_KEY = 'your-secret-key'
UPLOAD_FOLDER = os.path.join(os.path.dirname(__file__), 'uploads')
```

## 📁 File Upload

- Uploaded files are stored in `backend/uploads/`
- Configure max file size in config
- Supported: All file types (configure as needed)

## 🐛 Troubleshooting

**Dashboard crashes?**
- Ensure all database models are properly defined
- Check that JWT token is valid
- Verify database connection

**CORS errors?**
- Check that frontend URL is in allowed origins
- Verify credentials are being sent with requests

**Module not found?**
- Activate virtual environment
- Run `pip install -r requirements.txt`

## 📝 Environment Variables

Create `.env` file in backend:
```
DATABASE_URL=mysql+pymysql://user:pass@localhost/db
JWT_SECRET_KEY=your_secret_key
UPLOAD_FOLDER=./uploads
```

## 🎓 Learning Resources

- [Flask Documentation](https://flask.palletsprojects.com/)
- [SQLAlchemy ORM](https://docs.sqlalchemy.org/)
- [React Documentation](https://react.dev/)
- [JWT Authentication](https://flask-jwt-extended.readthedocs.io/)

## 📄 License

This project is open source and available under the MIT License.

## 👥 Contributing

Feel free to fork this repository and submit pull requests for any improvements.

## 📞 Support

For issues or questions, please create an issue in the repository.

---

**Last Updated**: March 2026
