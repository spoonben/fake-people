People API
===
An API for creating... people

This is a simple "API" used for my JavaScript class at Philadelphia University.

## Getting an API Key
In order to develop against the API, you'll need a key. To obtain a key, hit `https://fake-people.benspoon.com/getApiKey`.

The returned key is yours! Then just hit `https://fake-people.benspoon.com/[your-api-key]/people` to get the initial data back.

## API
The API contains a single endpoint, `people`, which supports **GET**, **POST**, and **PATCH** requests.

#### GET `[your-api-key]/people`
Returns a list of all available people.

Example request:
```http
GET /7c023f01/people HTTP/1.1
Accept: application/json
Host: fake-people.benspoon.com
User-Agent: HTTPie/0.9.2
```

Example response:
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Fri, 20 Nov 2015 14:18:57 GMT

[
    {
  "id": "56ef4e9b610100492388811f",
  "picture": "http://placehold.it/32x32",
  "age": 34,
  "eyeColor": "brown",
  "name": "Gracie Mathis",
  "gender": "female",
  "email": "graciemathis@namegen.com",
  "phone": "+1 (857) 555-2824",
  "address": "540 Seeley Street, Oneida, Guam, 4938",
  "friends": [
    {
      "id": 0,
      "name": "Boone Ware"
    },
    {
      "id": 1,
      "name": "Johanna Coleman"
    },
    {
      "id": 2,
      "name": "Glenda Benson"
    }
  ]
},
    ...
]
```

#### GET `[your-api-key]/people/{id}`
Returns a single hero's information

Example request:
```http
GET /7c023f01/people/1 HTTP/1.1
Accept: application/json
Host: fake-people.benspoon.com
```

Example response:
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Fri, 20 Nov 2015 14:18:57 GMT

 {
  "id": "56ef4e9b610100492388811f",
  "picture": "http://placehold.it/32x32",
  "age": 34,
  "eyeColor": "brown",
  "name": "Gracie Mathis",
  "gender": "female",
  "email": "graciemathis@namegen.com",
  "phone": "+1 (857) 555-2824",
  "address": "540 Seeley Street, Oneida, Guam, 4938",
  "friends": [
    {
      "id": 0,
      "name": "Boone Ware"
    },
    {
      "id": 1,
      "name": "Johanna Coleman"
    },
    {
      "id": 2,
      "name": "Glenda Benson"
    }
  ]
}
```

#### POST `[your-api-key]/people`
Create a new person. The `id` will be automatically generated. All other fields need to be provided
in `JSON` format. See the [GET](#get-your-api-keypeople) example above for the list of expected fields.

Example request:
```http
POST /7c023f01/people HTTP/1.1
Accept: application/json
Content-Type: application/json
Host: fake-people.benspoon.com

{
    "name": "Bob Paterson",
    "age": 89,
    ...
}
```

Example response:
```http
HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8
Date: Fri, 20 Nov 2015 14:18:57 GMT

{
    "id": 11,
    "name": "Bob Peterson",
    "age": 89,
    ...
}
```

#### PATCH `[your-api-key]/people/{id}`
Update an existing person. Fields must to be provided in `JSON` format. Fields that are not provided
in the request body will not be updated.

Example request:
```http
PATCH /7c023f01/people/1 HTTP/1.1
Accept: application/json
Content-Type: application/json
Host: fake-people.benspoon.com

{
    "name": "Gracie Mathis"
}
```

Example response:
```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Fri, 20 Nov 2015 14:18:57 GMT

{
    "name": "Gracie Mathis",
    "age": 34,
    ...
}
```
