# 🚀 Node.js + Express \| AWS EC2 Dynamic Website

**GitHub-based deployment of a Node.js + Express application on AWS
EC2**

![Node.js](https://img.shields.io/badge/Node.js-18.x-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-4.x-000000?style=for-the-badge&logo=express&logoColor=white)
![AWS
EC2](https://img.shields.io/badge/AWS-EC2-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white)

------------------------------------------------------------------------

## 🎯 Project Overview

This project demonstrates the complete workflow of deploying a Node.js +
Express application on AWS EC2 using GitHub as the source-code
repository.

**Developer → Git → GitHub → EC2 → Clone → npm install → Node.js/Express
→ Browser**

## 🏗️ Architecture

![Deployment Flow](flow.jpg)

## 🧰 Technology Stack

  Technology          Purpose
  ------------------- -----------------------
  Node.js             JavaScript runtime
  Express.js          Web framework
  npm                 Dependency management
  Git                 Version control
  GitHub              Source repository
  AWS EC2             Cloud server
  Amazon Linux 2023   Server OS
  Security Group      Network access
  SSH                 Server connection

------------------------------------------------------------------------

# 🚀 Deployment Walkthrough

## 01. Application Files & Source Code

``` text
NodeJS-Express-Dynamic-Website/
├── app.js
└── package.json
```

## 02. Git Repository Initialization & Push

``` bash
git init
git status
git add .
git commit -m "tested ok"
git branch main -M
git remote add origin <repository-url>
git push -u origin main
```

## 03. GitHub Repository

The GitHub repository contains:

``` text
app.js
package.json
```

## 04. EC2 Launch & User Data

Amazon Linux 2023 was selected with a `t3.micro` instance.

``` bash
#!/bin/bash
yum update -y
yum install nodejs git -y
```

## 05. EC2 Server Status

The EC2 instance was launched successfully and reached the Running
state.

## 06. Server Environment Verification

``` bash
node --version
npm --version
git --version
```

Captured versions:

``` text
Node.js  v18.20.8
npm      10.8.2
Git      2.50.1
```

## 07. Clone Application Repository

``` bash
git clone <repository-url>
cd NodeJS-Express-Dynamic-Website/
ls
```

Initially:

``` text
app.js
package.json
```

## 08. Dependency Error

Before installing dependencies:

``` bash
node app.js
```

Result:

``` text
Error: Cannot find module 'express'
```

The source code was present, but Express had not yet been installed on
the server.

## 09. Permission Fix & Dependency Installation

Because `sudo git clone` was used, the project became root-owned.

``` bash
sudo chown -R ec2-user:ec2-user .
npm install
```

After installation:

``` text
node_modules/
package-lock.json
```

Then:

``` bash
node app.js
```

Successful result:

``` text
App listening at http://localhost:3000
```

## 10. Security Group

TCP port `3000` was allowed so the application could be reached
externally.

``` text
Browser
   ↓ TCP :3000
EC2 Security Group
   ↓
Node.js + Express
```

## 11. Final Verification

``` text
http://<EC2-PUBLIC-IP>:3000
```

The Express response was successfully displayed in the browser.

------------------------------------------------------------------------

# 🧠 Key DevOps Learning

### `npm install`

Run it inside the directory containing `package.json`:

``` bash
cd NodeJS-Express-Dynamic-Website
npm install
```

It installs the dependency tree and creates `node_modules` and
`package-lock.json`.

### Permission Issue

If the repository was cloned using `sudo`, ownership can be corrected
with:

``` bash
sudo chown -R ec2-user:ec2-user .
```

### Application Start

``` bash
node app.js
```

The application listens on port `3000`.

------------------------------------------------------------------------

# 🛠️ Troubleshooting

### ❌ Cannot find module 'express'

``` bash
npm install
node app.js
```

### ❌ EACCES: permission denied

``` bash
sudo chown -R ec2-user:ec2-user .
npm install
```

### ❌ Browser cannot connect

Check:

1.  `node app.js` is running.
2.  Port `3000` is configured.
3.  Security Group allows TCP `3000`.
4.  Correct EC2 public IP is used.
5.  URL contains `:3000`.

------------------------------------------------------------------------

# 📸 Project Evidence

    No. Evidence
  ----- ---------------------------------------------
     01 Application Files & Source Code
     02 Git Repository Initialization & Push
     03 GitHub Repository
     04 EC2 Instance Configuration & User Data
     05 EC2 Server Status
     06 Server Environment Verification
     07 Application Repository Cloning
     08 Application Dependency Error
     09 Dependency Installation & Application Start
     10 Security Group Configuration
     11 Deployed Node.js Application

> **Important:** Screenshots will only appear in GitHub README after
> their image files are uploaded to the repository. The current
> repository screenshot shows that only `flow.jpg`, the PDF and the
> README were uploaded.

------------------------------------------------------------------------

# 📂 Repository Documentation

``` text
NodeJS-Express-Dynamic-Website/
├── app.js
├── package.json
├── README.md
├── flow.jpg
└── NodeJS_Express.pdf
```

# 📕 Project Report

[Open NodeJS Express Project PDF](NodeJS_Express.pdf)

------------------------------------------------------------------------

# 🏁 Final Result

``` text
Developer
   ↓
Git
   ↓
GitHub
   ↓
AWS EC2
   ↓
git clone
   ↓
npm install
   ↓
node app.js
   ↓
Security Group :3000
   ↓
Browser
```

## ✅ Successfully Deployed

**GitHub → AWS EC2 → Node.js + Express → Browser**
