# Output

Wadapdoge is a simple chat server application that uses Express and Socket.io. 
![Alt text](image-2.png)


## Package and Dependencies
Necessary dependencies are found in package.json. 

These scripts will be executed when you run npm install command is triggered in Dockerfile.

The main dependencies for this app are:
- express: Web application framework for Node.js.
- socket.io: Real-time bidirectional event-based communication library for Node.js.

```bash
 {
  "name": "c3g2-capstone-rev1",
  "version": "1.0.0",
  "description": "Wadap Doge",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "test": "jest"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/Mha47/c3g2-capstone-rev1.git"
  },
  "author": "C3G2",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/Mha47/c3g2-capstone-rev1/issues"
  },
  "homepage": "https://github.com/Mha47/c3g2-capstone-rev1#readme",
  "dependencies": {
    "express": "^4.18.2",
    "socket.io": "^4.7.2"
  },
  "devDependencies": {
    "jest": "^29.7.0",
    "socket.io-client": "^4.7.2"
  }
}
```

## Containerization 

This Node.js application using the latest version of Node.js is containerized using and Dockerfile sets up as below- a working directory, installs the application dependencies, copies the application code, exposes port 3000, and starts the application.

```docker
#use nodejs with latest version
FROM node:latest

#set working directory
WORKDIR /app

#install the app dependencies
#use wildcard to copy both package.json and package-lock.json
COPY package*.json ./
RUN npm install

#bundle app source
COPY . .

#expose port
EXPOSE 3000

#start the app
CMD ["npm", "start"]

```
