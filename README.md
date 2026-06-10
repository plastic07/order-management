# Order Management System

A secure REST API backend built with Django REST Framework, featuring Google OAuth 2.0 authentication and structured data management endpoints.

**Stack:** Python · Django REST Framework · Google OAuth 2.0 · SQLite

---

## Features

- **Google OAuth 2.0** — Secure login via Google; handles access and refresh token storage
- **Protected endpoints** — All data operations require authentication
- **Data entry** — Add structured entries (title + description) via POST
- **Filtered retrieval** — Query entries by title via GET parameters

---

## Setup

```bash
# 1. Clone and enter
git clone https://github.com/plastic07/myproject.git
cd myproject

# 2. Create virtual environment
python3 -m venv venv
source venv/bin/activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Add Google OAuth credentials
# Go to Google Cloud Console → Create OAuth 2.0 Client ID
# Download client_secret.json → place in root directory
# (already excluded by .gitignore)

# 5. Apply migrations and run
python manage.py migrate
python manage.py runserver
```

---

## API Reference

### Authenticate
```
GET /oauth2callback/
```
Initiates Google OAuth flow. Visit in browser or trigger via Postman.

### Add entry
```
POST /api/data/
Content-Type: application/json

{
  "title": "Sample Entry",
  "description": "This is a test description."
}
```

### Retrieve entries
```
GET /api/data/?title=Sample
```
Returns all entries matching the title query. Requires authentication.

---

## Project Structure

```
myproject/
├── manage.py
├── myapp/
│   ├── models.py
│   ├── views.py
│   └── urls.py
├── myproject/
│   ├── settings.py
│   └── urls.py
├── requirements.txt
├── .gitignore
└── client_secret.json   ← excluded, add manually
```
