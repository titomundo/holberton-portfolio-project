# API Endpoints
**Note:** All API endpoints listed here must have the following prefix: `api/v<api_version_number>/`. \
For example: `/api/v1/auth/register`. 

## Auth Endpoints
### Register User
- Method: GET
- URL: `/auth/register`

**Input Format:**
```javascript
{
    "first_name": "John",
    "last_name": "Doe",
    "email" "johndoe@mail.com",
    "password": "12345",
}
```
**Response:**
```javascript
{
    "id" "some_uuid",
    "first_name": "John",
    "last_name": "Doe",
    "email" "johndoe@mail.com",
    "is_admin": true
}
```

### Login User
- Method: GET
- URL: `/auth/login`

#### Input Format:
```javascript
{
    "email" "johndoe@mail.com",
    "password": "12345",
}
```
#### Response:
```javascript
{
    "access_token": "some_bearer_token"
}
```

## User Endpoints
### Register User
- Method: POST
- URL: `/users`

**Input Format:**
```javascript
{
    "first_name": "John",
    "last_name": "Doe",
    "email" "johndoe@mail.com",
    "password": "12345",
}
```
**Response:**
```javascript
{
    "id" "some_uuid",
    "first_name": "John",
    "last_name": "Doe",
    "email" "johndoe@mail.com",
    "is_admin": false
}
```

### Fetch Users
- Method: GET
- URL: `/users`

**Response:**
```javascript
{
    {
        "id" "some_uuid",
        "first_name": "John",
        "last_name": "Doe",
        "email" "johndoe@mail.com",
        "is_admin": false
    },
    ...
}
```

### Fetch User by ID
- Method: GET
- URL: `/users/<user_id>`

**Response:**
```javascript
{
    "id" "some_uuid",
    "first_name": "John",
    "last_name": "Doe",
    "email" "johndoe@mail.com",
    "is_admin": false
}
```

### Fetch Businesses by User
- Method: GET
- URL: `/users/<user_id>/businesses`

**Response:**
```javascript
{
    {
        "id" "some_uuid"
        "name": "Bob's Burguers",
        "Description": "A happy places for families to enjoy some meals",
        "email" "burguerbob@business.com",
        "phone_number" "1234567890"
    },
    ...
}
```

### Update User
- Method: PUT
- URL: `/users/<user_id>`

**Input Format:**
```javascript
{
    "first_name": "Jake",
    "last_name": "Doe",
    "email" "johndoe@mail.com",
}
```
**Response:**
```javascript
{
    "message": "User updated successfully"
}
```

### Delete User
- Method: DELETE
- URL: `/users/<user_id>`

**Response:**
```javascript
{
    "message": "User deleted successfully"
}
```

## Business Endpoints
### Create business
- Method: POST
- URL: `/businesses`

**Input Format:**
```javascript
{
    "name": "Bob's Burguers",
    "Description": "A happy places for families to enjoy some meals",
    "email" "burguerbob@business.com",
    "phone_number" "1234567890"
}
```
**Response:**
```javascript
{
    "id" "some_uuid"
    "name": "Bob's Burguers",
    "Description": "A happy places for families to enjoy some meals",
    "email" "burguerbob@business.com",
    "phone_number" "1234567890",
    "owner_id": "owner_uuid"
}
```

### Fetch Business by ID
- Method: GET
- URL: `/businesses/<user_id>`

**Response:**
```javascript
{
    "id" "some_uuid"
    "name": "Bob's Burguers",
    "Description": "A happy places for families to enjoy some meals",
    "email" "burguerbob@business.com",
    "phone_number" "1234567890",
    "owner_id": "owner_uuid"
}
```

### Fetch Locations by Business
- Method: GET
- URL: `/businesses/<business_id>/locations`

**Response:**
```javascript
{
    {
        "id" "some_uuid",
        "name": "Bob's Burguers 1",
        "Description": "Main Building",
        "capacity": 50,
    },
    ...
}
```

### Update Business
- Method: PUT
- URL: `/businesses/<business_id>`

**Input Format:**
```javascript
{
    "name": "Bob's Burguers",
    "Description": "A happy places for families to enjoy some meals and fries",
    "email" "burguerbob@business.com",
    "phone_number" "1234567890"
}
```
**Response:**
```javascript
{
    "message": "Business updated successfully"
}
```

### Update User
- Method: DELETE
- URL: `/businesses/<business_id>`

**Response:**
```javascript
{
    "message": "Businesses deleted successfully"
}
```

## Location Endpoints
### Create Location
- Method: POST
- URL: `/locations`

**Input Format:**
```javascript
{
    "name": "Bob's Burguers 1",
    "Description": "Main Building",
    "capacity": 50,
    "business_id" "business_uuid"
}
```
**Response:**
```javascript
{
    "id" "some_uuid",
    "name": "Bob's Burguers 1",
    "Description": "Main Building",
    "capacity": 50,
    "business_id" "business_uuid",
    "owner_id": "owner_uuid"
}
```

### Fetch Location by ID
- Method: GET
- URL: `/locations/<location_id>`

**Response:**
```javascript
{
    "id" "some_uuid",
    "name": "Bob's Burguers 1",
    "Description": "Main Building",
    "capacity": 50,
    "business_id" "business_uuid",
    "owner_id": "owner_uuid"
}
```

### Fetch Reservations by Location
- Method: GET
- URL: `/locations/<location_id>/reservations`

**Response:**
```javascript
{
    {
        "id": "some_uuid",
        "client_name": "Jane Doe",
        "Description": "Birthday Reservation",
        "date" "2026-07-23T18:25:43",
        "slot": 4,
        "status": "pending",
        "business_id" "business_uuid"
    },
    ...
}
```

### Update Location
- Method: PUT
- URL: `/locations/<location_id>`

**Input Format:**
```javascript
{
    "name": "Bob's Burguers 1",
    "Description": "Main Building (now expanded!)",
    "capacity": 65,
}
```
**Response:**
```javascript
{
    "message": "Location updated successfully"
}
```

### Delete Location
- Method: DELETE
- URL: `/locations/<location_id>`

**Response:**
```javascript
{
    "message": "Location deleted successfully"
}
```

## Reservation Endpoints
### Create Reservation
- Method: POST
- URL: `/reservations`

**Input Format:**
```javascript
{
    "client_name": "Jane Doe",
    "Description": "Birthday Reservation",
    "date" "2012-04-23T18:25:43"
    "slot": 4
    "business_id" "business_uuid"
}
```
**Response:**
```javascript
{
    "id": "some_uuid",
    "client_name": "Jane Doe",
    "Description": "Birthday Reservation",
    "date" "2026-07-23T18:25:43",
    "slot": 4,
    "business_id" "business_uuid"
}
```

### Fetch Reservation by ID
- Method: GET
- URL: `/reservations/<reservation_id>`

**Response:**
```javascript
{
    "id": "some_uuid",
    "client_name": "Jane Doe",
    "Description": "Birthday Reservation",
    "date" "2026-07-23T18:25:43",
    "slot": 4,
    "status": "pending"
    "business_id" "business_uuid"
},
```

### Update Location
- Method: PUT
- URL: `/reservations/<reservation_id>`

**Input Format:**
```javascript
{
    "client_name": "Jane Doe",
    "Description": "Birthday Reservation",
    "date" "2026-07-23T18:25:43",
    "slot": 9,
    "status": "cancelled"
}
```
**Response:**
```javascript
{
    "message": "Reservation updated successfully"
}
```

### Delete Reservation
- Method: DELETE
- URL: `/reservations/<reservation_id>`

**Response:**
```javascript
{
    "message": "Reservation deleted successfully"
}
```
