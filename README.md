# LifeHub - Django Web Application

## Deployment Guide

### Requirements
- Python 3.11+
- PostgreSQL (for production)
- Gunicorn
- WhiteNoise

### Local Development

1. **Clone the repository**
```bash
git clone https://github.com/yahyobek2013/LifeHub.git
cd LifeHub
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# or
venv\Scripts\activate  # Windows
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Create .env file**
```bash
cp .env.example .env
# Edit .env file with your settings
```

5. **Run migrations**
```bash
python manage.py migrate
```

6. **Create superuser**
```bash
python manage.py createsuperuser
```

7. **Run development server**
```bash
python manage.py runserver
```

### Production Deployment (Heroku/Similar Platforms)

1. **Set environment variables**
```bash
# In your server environment, set these variables:
SECRET_KEY=your-secret-key-here
DEBUG=False
ALLOWED_HOSTS=yourdomain.com,www.yourdomain.com
DATABASE_URL=postgres://user:password@host:port/dbname
SECURE_SSL_REDIRECT=True
SESSION_COOKIE_SECURE=True
CSRF_COOKIE_SECURE=True
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Collect static files**
```bash
python manage.py collectstatic --noinput
```

4. **Run migrations**
```bash
python manage.py migrate
```

5. **Start Gunicorn server**
```bash
gunicorn config.wsgi:application
```

### Security Notes

- **Never commit .env file** - it contains sensitive information
- **Change SECRET_KEY** before production deployment
- **Use PostgreSQL** in production, not SQLite
- **Set DEBUG = False** in production
- **Configure ALLOWED_HOSTS** with your actual domain

### Project Structure

```
LifeHub/
├── admin_panel/          # Admin panel app
├── users/               # User authentication app
├── config/              # Project configuration
├── templates/           # HTML templates
├── static/              # Static files (CSS, JS, Images)
├── media/               # User uploaded files
├── requirements.txt     # Python dependencies
├── Procfile            # Heroku deployment
├── runtime.txt         # Python version
└── .env.example        # Environment variables template
```

### Features

- User authentication (login, register, logout)
- Dashboard with multiple modules:
  - Calendar
  - Notes
  - Tasks
  - Goals
  - Expenses
  - Shopping List
  - Wishlist
  - Health Reminders
  - Documents
  - Gallery
  - Contacts
  - Important Dates
  - Links
  - Password Vault
  - Statistics
- Admin panel
- PDF generation
- Responsive design