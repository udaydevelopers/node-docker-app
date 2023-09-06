To create a Dockerfile for running a Node.js application in a Docker container, you can follow these steps:

1. Create a directory for your Node.js application and navigate to it in your terminal.

2. Create a file named `Dockerfile` (without any file extension) in the application directory.

3. Open the `Dockerfile` in a text editor and add the following contents:

```Dockerfile
# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of the application source code to the working directory
COPY . .

# Expose the port your app will run on
EXPOSE 3000

# Define the command to run your application
CMD [ "npm", "start" ]
```

This Dockerfile sets up a basic Node.js environment and copies your application code into the container. It assumes you have a `package.json` file that lists your application's dependencies and a `npm start` script to start your application. You may need to adjust these settings to match your specific Node.js project.

4. Save the Dockerfile.

5. Build the Docker image from the Dockerfile using the `docker build` command. Run this command from the directory containing your Dockerfile:

```bash
docker build -t your-image-name .
```

Replace `your-image-name` with a meaningful name for your Docker image.

6. Once the image is built successfully, you can run a container based on this image using the `docker run` command:

```bash
docker run -p 3000:3000 your-image-name
```

Replace `your-image-name` with the name you provided in step 5.

Your Node.js application should now be running in a Docker container, and you can access it in your web browser at `http://localhost:3000` or from any other client that can reach your Docker host.

Make sure to customize the Dockerfile and commands as needed to suit the specific requirements of your Node.js application.