Patient Management System API 🩺
A simple and efficient RESTful API built with FastAPI to manage patient records. It provides full CRUD (Create, Read, Update, Delete) functionality and stores data in a local JSON file.

This project automatically calculates a patient's Body Mass Index (BMI) and provides a health verdict based on the result.

Features ✨
Create Patient: Add new patient records to the system.

View Patients: Retrieve a list of all patients or a single patient by ID.

Update Patient: Modify the details of an existing patient.

Delete Patient: Remove a patient record from the system.

Automatic BMI Calculation: The API automatically computes the BMI (bmi) and a health verdict (verdict) for each patient.

Sort Records: Sort patients based on height, weight, or bmi in ascending or descending order.

Data Validation: Uses Pydantic for robust data validation and type checking.

Interactive Docs: Automatic, interactive API documentation provided by FastAPI (via Swagger UI and ReDoc).

Technologies Used
Python 3.11+

FastAPI: The core web framework.

Pydantic: For data validation and settings management.

Uvicorn: An ASGI server to run the application.

Setup and Installation
Follow these steps to get the project running on your local machine.

1. Prerequisites
Make sure you have Python 3.8 or newer installed.

2. Clone the Repository
Bash

git clone https://github.com/your-username/fastapi-patient-api.git
cd fastapi-patient-api
3. Create a Virtual Environment
It's highly recommended to use a virtual environment to manage project dependencies.

On macOS/Linux:

Bash

python3 -m venv venv
source venv/bin/activate
On Windows:

Bash

python -m venv venv
.\venv\Scripts\activate
4. Install Dependencies
First, create a requirements.txt file with the necessary packages:

# requirements.txt
fastapi
uvicorn[standard]
Now, install them using pip:

Bash

pip install -r requirements.txt
5. Create the Data File
The API uses a patients.json file to store data. Create this file in the root directory of the project with an empty JSON object.

JSON

{}
6. Run the Server
Start the development server using Uvicorn. Assuming your Python file is named main.py:

Bash

uvicorn main:app --reload
The --reload flag makes the server restart automatically after code changes. The API will now be running at http://127.0.0.1:8000.

API Endpoints
You can interact with the API using the following endpoints. For a hands-on experience, navigate to http://127.0.0.1:8000/docs to use the interactive Swagger UI.

Method	Endpoint	Description
GET	/	Displays a welcome message for the API.
GET	/view	Retrieves all patient records from the database.
GET	/patient/{patient_id}	Retrieves a single patient by their unique ID.
GET	/sort	Sorts all patients. Requires query parameters: sort_by (height, weight, or bmi) and order (asc or desc).
POST	/create	Creates a new patient record. The request body must contain the patient's data.
PUT	/edit/{patient_id}	Updates the details of an existing patient by their ID.
DELETE	/delete/{patient_id}	Deletes a patient record by their ID.

Export to Sheets
Example: Creating a Patient
Send a POST request to /create with the following JSON body:

JSON

{
  "id": "P001",
  "name": "John Doe",
  "city": "New York",
  "age": 35,
  "gender": "male",
  "height": 1.75,
  "weight": 75
}
Example: Viewing a Patient
Send a GET request to /patient/P001. The response will include the computed fields:

JSON

{
  "name": "John Doe",
  "city": "New York",
  "age": 35,
  "gender": "male",
  "height": 1.75,
  "weight": 75,
  "bmi": 24.49,
  "verdict": "Normal"
}
