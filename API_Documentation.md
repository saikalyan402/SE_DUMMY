
# API Documentation

## Integrated APIs
These APIs are designed to manage projects, users, and PDF-based milestones.

### GET /api/projects
**Description:** Retrieve all projects.

**Response:**
- 200 OK
  ```json
  [
      {
          "id": 1,
          "project_name": "Project Name",
          "ta_name": "TA Name",
          "ta_role": "TA Role",
          "ta_email": "ta@example.com"
      }
  ]
  ```

### POST /api/projects
**Description:** Create a new project.

**Request Body:**
```json
{
    "project_name": "Project Name",
    "ta_name": "TA Name",
    "ta_role": "TA Role",
    "ta_email": "ta@example.com"
}
```

**Response:**
- 201 Created
  ```json
  {
      "id": 1
  }
  ```

### POST /upload_pdf/<project_id>
**Description:** Upload a PDF file for a specific project.

**Request:** Form-data with key `pdf` and the file to upload.

**Response:**
- 200 OK
  ```json
  {
      "message": "File uploaded successfully",
      "filename": "uploaded_file.pdf"
  }
  ```

- 400 Bad Request
  ```json
  {
      "error": "Invalid file type. Only PDFs are allowed."
  }
  ```

### POST /generate_milestones/<project_id>
**Description:** Generate milestones based on the uploaded PDF file.

**Response:**
- 200 OK
  ```json
  {
      "message": "Milestones generated and saved successfully",
      "milestones": [
          "Milestone 1",
          "Milestone 2"
      ]
  }
  ```

- 400 Bad Request
  ```json
  {
      "error": "No PDF file associated with this project"
  }
  ```

- 500 Internal Server Error
  ```json
  {
      "error": "Failed to read PDF: [error details]"
  }
  ```
