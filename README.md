# Cinema Project
This project imitates the work of a cinema service. The project has been built on the REST-principles. It supports reservation tickets, registration, authentication and CRUD operations.
# Features:
- authentication and registration, which are accessed for all non-authenticated clients;
- getting all cinema halls, movies, orders, available movie sessions, shopping carts by user for users with a role as user;
- making an order for users with a role as user;
- assigning a new movie session to the specified shopping cart for users with a role as user;
- getting all cinema halls, movies, available movie sessions and users by email for users with role as admin;
- creating new cinema halls, movies and movie sessions for users with a role as admin;
- updating a movie session by id for users with a role as admin;
- removing a movie session by id for users with a role as admin;
# Structure:
- Config:

| Class               | Brief description                                                             |
|---------------------|-------------------------------------------------------------------------------|
| AppConfig           | It's used for setting up configuration parameters for Hibernate               |
| DataInitializer     | It's used for injecting two users for testing our application                 |
| SecurityConfig      | It's used for setting up config parameters and enabling spring security block |
| SecurityInitializer | It's used for setting up config parameters                                    |
| WebAppInitializer   | It's used for setting up config parameters                                    |
| WebConfig           | It's used for setting up config parameters and enabling spring web block      |
- Controllers:

| Controller               | Description                                                                                                                             | Addresses                                                      | Access                                                                                                                                                                            |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AuthenticationController | It's used for authentication and registration clients                                                                                   | /login, /register                                              | non-authenticated users                                                                                                                                                           |
| CinemaHallController     | It's used for receiving all cinema halls and creating a new cinema hall                                                                 | /cinema-halls                                                  | creating a new cinema hall only for admins, receiving all cinema halls for all authenticated users                                                                                |
| MovieController          | It's used for receiving all movies and creating a new movie                                                                             | /movies                                                        | creating a new movie only for admins, receiving all movies for all authenticated users                                                                                            |
| MovieSessionController   | It's used for receiving all available movie sessions, creating a new movie session, removing and updating a movie session by identifier | /movie-sessions, /movie-sessions/available, /movie-sessions/id | creating a new movie session only for admins, receiving available movie sessions for all authenticated users, updating and removing a movie session by identifier only for admins |
| OrderController          | It's used for receiving a history of user's orders and completing an order                                                              | /orders, /orders/complete                                      | completing an order and receiving a history of orders only for users                                                                                                              |
| ShoppingCartController   | It's used for adding a new movie session to a specified shopping cart and for getting a user's shopping cart                            | /shopping-carts/movie-sessions, /shopping-carts/by-user        | getting a shopping cart by user and assigning a new movie session to the specified shopping cart for users with a role as user                                                    |
| UserController           | It's used for receiving a user by email                                                                                                 | /users/by-email                                                | getting a user by email only for admins                                                                                                                                           |

- DAO:

| DaoImpl (handler)   | Model        |
|---------------------|--------------|
| CinemaHallDaoImpl   | CinemaHall   |
| MovieDaoImpl        | Movie        |
| MovieSessionDaoImpl | MovieSession |
| OrderDaoImpl        | Order        |
| RoleDaoImpl         | Role         |
| ShoppingCartDaoImpl | ShoppingCart |
| TicketDaoImpl       | Ticket       |
| UserDaoImpl         | User         |

- DTOs:

| DTO                     | Model        | Type     |
|-------------------------|--------------|----------|
| CinemaHallRequestDto    | CinemaHall   | Request  |
| MovieRequestDto         | Movie        | Request  |
| MovieSessionRequestDto  | MovieSession | Request  |
| UserRequestDto          | User         | Request  |
| CinemaHallResponseDto   | CinemaHall   | Response |
| MovieResponseDto        | Movie        | Response |
| MovieSessionResponseDto | MovieSession | Response |
| OrderResponseDto        | Order        | Response |
| ShoppingCartResponseDto | ShoppingCart | Response |
| UserResponseDto         | User         | Response |

- Exceptions:

| Custom exception        | Description                                                            |
|-------------------------|------------------------------------------------------------------------|
| DataProcessingException | an exception indicating problems with processing data on the DAO layer |

- LIB:

| Validator                 | Corresponding annotation | Description                                                        |
|---------------------------|-----------------|--------------------------------------------------------------------|
| EmailValidator            | ValidEmail      | It's used for checking the passing user's email is valid           |
| FieldsValueMatchValidator | FieldValueMatch | It's used for checking if the two fields are equalled between them |

- Models:

| Model        | Description                          |
|--------------|--------------------------------------|
| CinemaHall   | a model representing a cinema hall   |
| Movie        | a model representing a movie         |
| MovieSession | a model representing a movie session |
| Order        | a model representing an order        |
| Role         | a model representing a role          |
| ShoppingCart | a model representing a shopping cart |
| Ticket       | a model representing a ticket        |
| User         | a model representing a user          |

- Services:

| Service                   | Description                                                                    |
|---------------------------|--------------------------------------------------------------------------------|
| AuthenticationServiceImpl | a service happening all business logic with authentication                     |
| CinemaHallServiceImpl     | a service happening all business logic with CinemaHall model                   |
| MovieServiceImpl          | a service happening all business logic with Movie model                        |
| MovieSessionServiceImpl   | a service happening all business logic with MovieSession model                 |
| OrderServiceImpl          | a service happening all business logic with Order model                        |
| RoleServiceImpl           | a service happening all business logic with Role model                         |
| ShoppingCartServiceImpl   | a service happening all business logic with ShoppingCart model                 |
| UserDetailsServiceImpl    | It's used for connecting between custom User model and UserDetails from Spring |
| UserServiceImpl           | a service happening all business logic with User model                         |

- Mappers:

| Mapper             | Description                                                             | Methods                  |
|--------------------|-------------------------------------------------------------------------|--------------------------|
| CinemaHallMapper   | It's used for converting from CinemaHall model to a corresponding DTO   | mapToModel(), mapToDto() |
| MovieMapper        | It's used for converting from Movie model to a corresponding DTO        | mapToModel(), mapToDto() |
| MovieSessionMapper | It's used for converting from MovieSession model to a corresponding DTO | mapToModel(), mapToDto() |
| OrderMapper        | It's used for converting from Order model to a corresponding DTO        | mapToDto()               |
| ShoppingCartMapper | It's used for converting from ShoppingCart model to a corresponding DTO | mapToDto()               |
| UserMapper         | It's used for converting from User model to a corresponding DTO         | mapToDto()               |

- Util:

| Util                | Description                                |
|---------------------|--------------------------------------------|
| DateTimePatternUtil | It's used for determining DateTime pattern |

# Technologies:
- JDK 17;
- Hibernate 5.6.14.Final;
- Spring 5.3.20;
- Spring Security 5.6.10;
- MySQL 8.0.22;
- Tomcat 9.0.73;
- Maven 3.1.1;

# How to run this project locally?
- make sure you have JDK 17 installed on your system;
- make sure you have Tomcat and MySQL installed on your system;
- clone this repository;
- open this project (you can do this using Intellij IDEA or another development environment);
- configure the database connection parameters in the resources/db.properties file;
- configure a local Tomcat configuration in your IDE;
- run the Tomcat configuration and deploy the application;
- when the program starts, two users are added to the database, you can log in both (you can use Postman to send some http request)

# Credentials
- admin credentials: alex@gmail.com and qwerty228 (if you want to log in as admin);
- user credentials: alice@gmail.com and 12345678 (if you want to log in as user).