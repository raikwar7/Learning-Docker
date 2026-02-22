# ------------------------------------------------------------
# Base Image
# ------------------------------------------------------------
# Use the official Node.js version 24 image from Docker Hub.
# This image already contains:
# - A Linux OS (Debian-based by default)
# - Node.js v24 installed
# - npm (Node Package Manager)
# This becomes the foundation of our container.
FROM node:24

# ------------------------------------------------------------
# Working Directory
# ------------------------------------------------------------
# Sets the working directory inside the container to /myapp.
# If the folder does not exist, Docker will create it.
# All following commands (COPY, RUN, CMD, etc.)
# will execute inside this directory.
WORKDIR /myapp

# ------------------------------------------------------------
# Copy Project Files
# ------------------------------------------------------------
# Copies all files and folders from the current
# local project directory into /myapp inside the container.
# First "."  -> current directory on your local machine
# Second "." -> current working directory inside container (/myapp)
# Note: It is usually better practice to copy package.json first
# for better Docker layer caching.
COPY . .
# ------------------------------------------------------------
# Install Dependencies
# ------------------------------------------------------------
# Runs the command inside the container:
#    npm install
# This installs all dependencies listed in package.json
# into node_modules inside the container.
# This step creates a new Docker layer.
RUN npm install

# ------------------------------------------------------------
# Expose Port
# ------------------------------------------------------------
# Tells Docker that the container will listen
# on port 3000 at runtime.
#
# IMPORTANT:
# EXPOSE does NOT publish the port automatically.
# You must still use:
#    docker run -p 3000:3000 <image-name>
EXPOSE 5173


# ------------------------------------------------------------
# Default Command
# ------------------------------------------------------------
# This is the default command that runs
# when the container starts.
#
# It executes:
#    npm start
#
# This usually starts your Node.js application
# (based on the "start" script inside package.json).
CMD ["npm", "run", "dev","--","--host"]