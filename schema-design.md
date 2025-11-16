# schema design of Smart Clinic Management System

## MySQL database design section
Include at least 4 tables (e.g., patients, doctors, appointments, and admin)
For each table, specify column names, data types, primary and foreign keys, and constraints (e.g., NOT NULL, UNIQUE)

### Table: patients
- id: INT, Primary Key, Auto Increment 
- patient_name: String, Not Null
- status: INT (0 = Enabled, 1 = disabled)

### Table: doctors
- id: INT, Primary Key, Auto Increment 
- doctor_name: String, Not Null
- status: INT (0 = Enabled, 1 = disabled)

### Table: appointments
- id: INT, Primary Key, Auto Increment
- doctor_id: INT, Foreign Key → doctors(id)
- patient_id: INT, Foreign Key → patients(id)
- appointment_time: DATETIME, Not Null
- status: INT (0 = Scheduled, 1 = Completed, 2 = Cancelled)

### Table: admin
- id: INT, Primary Key, Auto Increment 
- admin_name: String, Not Null
- status: INT (0 = Enabled, 1 = Disabled)

### Table: doctor_availability
- id: INT, Primary Key, Auto Increment
- doctor_id: INT, Foreign Key → doctors(id)
- work_time: DATETIME, Not Null
- status: INT (0 = Available, 1 = Unavailable)

## MongoDB collection design section
Choose a suitable document collection (e.g., prescriptions, feedback, and logs)
Provide a realistic JSON example of a document with nested fields or arrays.

### Collection: prescriptions

```json
{
  "_id": "ObjectId('64abc123456')",
  "patientName": "John Smith",
  "appointmentId": 51,
  "medication": "Paracetamol",
  "dosage": "500mg",
  "doctorNotes": "Take 1 tablet every 6 hours.",
  "refillCount": 2,
  "pharmacy": {
    "name": "Walgreens SF",
    "location": "Market Street"
  }
}
```json

### Collection: feedback

```json
{
  "_id": "ObjectId('64abc223456')",
  "patientName": "John Smith",
  "appointmentId": 51,
  "feedbackDetail": "The doctor Jim Terry was not patient enough." 
}

### Collection: logs

```json
{
  "_id": "ObjectId('64abc323456')",
  "logDetail": "a sample log details." 
}


### Collection: messages

```json
{
  "_id": "ObjectId('64abc423456')",
  "time": "2025-11-16 16:00:00"
  "from": "John Smith",
  "to": "Jim Terry" 
  "message": "My leg is still paint after a week of medication. Any suggestion?" 
}
