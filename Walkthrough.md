# Unit 14 Sequelize Homework: Reverse Engineering Code

```
AS A developer

I WANT a walk-through of the codebase

SO THAT I can use it as a starting point for a new project
```

Reverse engineer the starter code provided and create a tutorial for the code.

Begin inspecting the code to get an understanding of each file's responsibility. Then, in a Google Doc, write a tutorial explaining *every* file and its purpose. If one file is dependant on other files, be sure to let the user know.

At the end of the tutorial, add instructions for how you could now add changes to this project.

## Walk-Through

Package File:
In the package file, it houses all your dependencies of npm plugins that will be utilized throughout your code. It also contains the name, description, and scripts that you can use to get your app started.
To create the packages from scratch, use the following CLI command in the terminal: < npm init >
The command will initialize the folder of your choosing where you would house your new project.

In your terminal, you can begin installing npm packages using the npm install command that can be taken from the specific npm package site. The packages that you install will show in your package.json file as dependencies. This allows for others that will be using your code to simply run an npm install and the npm packages will also be installed based off the information in the package file.

To build a project with a package.json file already created, simply use < npm install > in your cli to build your project.

Server.js File:
In this file, this will handle all server related services, the configurations of the ports, and authentication handling.
We will require all the npm packages and the passport file that you will later configure (note that you will require this file after it is built).
After declaring what is required then a port is configured and the database will need to be required of the models. This will sync your database which you will configure in the models folder. 
The next step is to create an express app and configure middleware needed for authentication such as express.json() which is a built-in middleware function in express that parses incoming requests with JSON payloads. In this project, the middleware handles parsing and handles static files.
Next, we will need to manage the login status of the user where will utilize passport and sessions. Based on the express app we will also need to require the routes.
Lastly, spin up the server using sequelize and syncing the database.

Folders:

Folders are a great way to manage files to allow ease of access and navigation. The basic folders needed to be configured are: config, models, public, and routes. The routes folder will handle the api calls and the url management of the project. The public folder will have information for the user to see such as your html page. Models contains the database information where a template will be created that the database can utilize for every unique user. The config folder will contain authentication, login process and environment information.

Folder: config/middleware:

Within the config folder we will create another folder called 'middleware'. It does not need to be created, but it is good to keep the files seperated neatly. The file that will be inside is called 'isAuthenticated.js'. This js file will restrict users based on their login status to grant or deny access to restricted URL's.

Folder: config:

The config.json file configures the environment. It specifies the username, password, database being utilized, host, and dialect. It tells the CLI how to connect with the database.

The passport.js is the fill that will require the passport module and the strategy of the passport. Also will need the database established by requiring the models folder. Here you will write code that will use passport to establish a strategy for users trying to login. You will need to look at the database to verify the credentials are correct. Afterwards, use passport to serialize and deserialize the user to retain authentication across different HTTP requests. Don't forget to export the configured passport to be utilized in other files and folders.

Folder: models:

In the index.js file, we will need to require:
1. fs to read and write file systems
2. path to locate the proper location of the file we will read from or write to.
3. sequelize to utilize the ORM [Object Relational Mapper] which allows for the models, seeding, etc. to be managed easier. Mapping out the objects to relational databases.
4. config file which will have the information on how to connect to the database.
5. basename which will extract the filename from a file path.
6. default environment established
7. variable db with empty curly braces

Using the required and defined variables you can create a new instance of sequelize of your config file envrionment. These are the parameters needed for the database to run. Then we establish our file system files to create the proper database relationship and association. We are able to real and map out each file in the model folder. Export the db module.

In the user.js, we begin by making necessary requirements. The only needed requirement would be bcrypt which will be used to conceal the password that a user sets. In creating the user model, we define a table for users which will have two columns of information, email and password. Like SQL, we define certain information for the two pieces of information such as DataTypes or validation, etc. Bcrypt will be used to do two things: validate the password and create a function to automatically hash the user's password. This will be exported as a module.

