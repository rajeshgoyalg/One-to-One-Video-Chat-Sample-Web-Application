# 1-to-1 RTC: A Sample Web App with EnableX Video Web Toolkit

The Sample Web App demonstrates the use of Video APIs for EnableX platform to carry out 1-to-1 RTC (Real Time Communication). The main motivation behind this application is to demonstrate usage of Video APIs and allow developers to ramp up on app by hosting on their own devices instead of directly using servers.

RTC Applications hosted on EnableX platform run natively on supported set of web browsers without any additional plugin downloads.

This basic 1-to-1 Video Chat Application is developed using HTML, CSS, Bootstrap, JAVA Script, jQuery, Node V8.9.1 and EnxRtc (The EnableX Web Toolkit).

>The details of the supported set of web browsers can be found here:
https://developer.enablex.io/video/browser-compatibility-of-enablex-video/


## 1. Important!

When developing a Node Application with EnxRtc.js make sure to include the updated EnxRtc.js polyfills from https://developer.enablex.io/video-api/client-api/web-toolkit/ for RTCPeerConnection and getUserMedia otherwise your application will not work in web browsers.


## 2. Trial

Sign up for a free trial https://portal.enablex.io/cpaas/trial-sign-up/ or try our multiparty video chat https://try.enablex.io/


## 3. Installation


### 3.1 Pre-Requisites

#### 3.1.1 App Id and App Key

* Register with EnableX https://portal.enablex.io/trial-sign-up/
* Create your Application
* Get your App ID and App Key delivered to your registered email
* Clone or download this repository `git clone https://github.com/EnableX/One-to-One-Video-Chat-Sample-Web-Application.git`


#### 3.1.2 SSL Certificates or Self-Signed Certificates

The Application needs to run on https. So, you need to use a valid SSL Certificate for your Domain and point your application to use them.

However you may use self-signed Certificate to run this application locally. There are many websites to get a self-signed certificate generated for you.
* https://letsencrypt.org/
* https://www.sslchecker.com/csr/self_signed
* https://www.akadia.com/services/ssh_test_certificate.html

The following below can also be used to create a self-signed certificate.

`cd One-to-One-Video-Chat-Sample-Web-Application`

`mkdir certs`

`cd certs`

`sudo openssl req -x509 -newkey rsa:4096 -keyout ./certs/localhost.key -out ./certs/localhost.crt -days 10000 -nodes`

`sudo chmod 755 ./certs/localhost.*`

`cd ..`

#### 3.1.3 Configure

Before you can run this application by hosting it you need to set three system environment variables. These are:
```javascript
SERVICE_PORT : Node port on which your application will run. Default port set is 5000
ENABLEX_APP_ID : Your EnableX "App ID" - It's your username for EnableX API and can be found at Dashboard > Projects https://portal.enablex.io/dashboard/
ENABLEX_APP_KEY : Your EnableX "App Key" - - It's your password for EnableX API and can be found at Dashboard > Projects https://portal.enablex.io/dashboard/
```

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the `=` with values from your EnableX account:
```javascript
  export SERVICE_PORT=XXXX
  export ENABLEX_APP_ID=XXXXXXXXXX
  export ENABLEX_APP_KEY=XXXXXXXXX
```

On Windows, open a powershell / command window and type the following commands. Note that there is no `=`, just the key and value separated by a space:
```javascript
  setx SERVICE_PORT 'XXXX'
  setx ENABLEX_APP_ID 'XXXXXXXXX'
  setx ENABLEX_APP_KEY 'XXXXXXXXX'
```

### 3.2 Build

Run `npm install` to build the project and the build artifacts will be stored in the `./node_modules` directory.


#### 3.2.1 Run Server

Run `node server.js` inside `server` folder to start your server.

`cd server`

`node server.js`
Server started. Listening on Port 5000

#### 3.2.2 Test Video Call

* Open a browser and go to `https://yourdomain:5000/`. The browser should load the App. Go to -> Advanced -> Proceed to localhost
* Don't have a Room ID? Create here (create a new RoomID)
* Store the Room ID for future use or share
* Enter a username (e.g. test0)
* Join and allow access to camera and microphone when prompted to start your first webRTC call through EnableX
* Open another browser tab and enter `https://yourdomain:5000/`
* Enter the same roomID previously created and add a different username (test1) and click join
* Now, you should see your own video in both the tabs!


## 4 Server API

EnableX Server API is a Rest API service meant to be called from Partners' Application Server to provision video enabled
meeting rooms. API Access is given to each Application through the assigned App ID and App Key. So, the App ID and App Key
are to be used as Username and Password respectively to pass as HTTP Basic Authentication header to access Server API.

For this application, the following Server API calls are used:
* https://developer.enablex.io/video-api/server-api/rooms-route/#get-rooms - To get list of Rooms
* https://developer.enablex.io/video-api/server-api/rooms-route/#get-room-info - To get information of the given Room
* https://developer.enablex.io/video-api/server-api/rooms-route/#create-token - To create Token for the given Room

To know more about Server API, go to:
https://developer.enablex.io/latest/server-api/


## 5 Client API

Client End Point Application uses Web Toolkit EnxRtc.js to communicate with EnableX Servers to initiate and manage RTC Communications.

To know more about Client API, go to:
https://developer.enablex.io/video-api/client-api/
