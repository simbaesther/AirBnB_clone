# 0x00. AirBnB clone - The console

## Description

What I learned from the tasks:

- How to use command interpreter to manage an object
- HTML/CSS templating
- Database storage
- API
- Front-end integration

---

## General Requirements

- Allowed editors: vi, vim and emacs.
- All files were created and compiled on Ubuntu 20.04.4 LTS using using python3 (version 3.8.5)
- All files end with a new line
- The first line of all files is exactly #!/usr/bin/python3
- Code style used is pycodestyle (version 2.8.\*)
- All files executable

## Usage

Console works in both interactive and non-iteractive modes.

| Command                                       | Example                                                                                                                                   |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Run the console                               | `./console.py`                                                                                                                            |
| Quit the console                              | `(hbnb) quit`                                                                                                                             |
| Display the help for a command                | `(hbnb) help <command>`                                                                                                                   |
| Create an object (prints its id)              | `(hbnb) create <class>`                                                                                                                   |
| Show an object                                | `(hbnb) show <class> <id>` or `(hbnb) <class>.show(<id>)`                                                                                 |
| Destroy an object                             | `(hbnb) destroy <class> <id>` or `(hbnb) <class>.destroy(<id>)`                                                                           |
| Show all objects, or all instances of a class | `(hbnb) all` or `(hbnb) all <class>`                                                                                                      |
| Update an attribute of an object              | `(hbnb) update <class> <id> <attribute name> "<attribute value>"` or `(hbnb) <class>.update(<id>, <attribute name>, "<attribute value>")` |

Non-interactive mode example

```bash
$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF help quit
(hbnb)
```

## Models

The folder [models](./models/) contains all the classes used in this project.

| File                                    | Description                                          | Attributes                                                                                                                     |
| --------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| [base_model.py](./models/base_model.py) | BaseModel class for all the other classes            | id, created_at, updated_at                                                                                                     |
| [user.py](./models/user.py)             | User class for future user information               | email, password, firstname, lastname                                                                                           |
| [amenity.py](./models/amenity.py)       | Amenity class for future amenity information         | name                                                                                                                           |
| [city.py](./models/city.py)             | City class for future location information           | stateid, name                                                                                                                  |
| [state.py](./models/state.py)           | State class for future location information          | name                                                                                                                           |
| [place.py](./models/place.py)           | Place class for future accomodation information      | city_id, userid, name, description, number_rooms, number_bathrooms, max_guest, price\_\_night, latitude, longitude, amenity_id |
| [review.py](./models/review.py)         | Review class for future user/host review information | place_id, user_id, text                                                                                                        |

## File storage

The folder [engine](./models/engine/) manages the serialization and deserialization of all the data, following a JSON format.

A FileStorage class is defined in [file_storage.py](./models/engine/file_storage.py) with methods to follow this flow:
`<object> -> to_dict() -> <dictionary> -> JSON dump -> <json string> -> FILE -> <json string> -> JSON load -> <dictionary> -> <object>`

The [**init**.py](./models/__init__.py) file contains the instantiation of the FileStorage class called **storage**, followed by a call to the method reload() on that instance.
This allows the storage to be reloaded automatically at initialization, which recovers the serialized data.

## Tests

All the code is tested with the **unittest** module.
The test for the classes are in the [models_test](./tests/models_test/) directory.

---

### Author

- **Esther Simba** - (https://github.com/simbaesther)