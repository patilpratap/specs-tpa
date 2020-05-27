## Login

#### To call server APIs a token is required. To get this token using the below mentioned login API

    /tpa/login [POST]
HEADER

    Content-Type:application/json
    
BODY
```javascript
{
  "tpaKey": "asdasd",  // required
}
```

RESPONSE - code - 200
```javascript
{
  "result": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
  },
  "name": "SuccessfullySaved.",
  "code": 20,
  "message": "Notification Sent Successfully to Upgrade Devices"
}
```

## TPA app upgrade

#### Notify CMS server about app upgrade

    /app-upgrade/notify [POST]

HEADER

    Content-Type:application/json
    Authorization : Bearer <token>

QUERY

    NA

BODY
```javascript
{
  "deviceOs": "WINDOWS",  // required
  "buildDownloadUrl": "http://builddownloadurl", // required
  "tpappId": 123, // required - third party app id (CMS team will provide one ID which will be final and you can always use that one
  "tpappVersion": "x.y.z" // required - this is the version of the app that you are updating to
}
```

RESPONSE - code - 200
```javascript
{
  "result": null,
  "name": "SuccessfullySaved.",
  "code": 20,
  "message": "Notification Sent Successfully to Upgrade Devices"
}
```

## TPA app upgrade build status

#### Checkthe build status

    /tpa/builds/status [GET]

HEADER

    Content-Type:application/json
    Authorization : Bearer <tpa token>

QUERY

    NA

BODY
    
    NA

RESPONSE - code - 200
```javascript
{
  "result": [
    {
      "tpappId": 1,
      "md5checksum": "E73A1A78A60152FC9D4DFE13A03096CC",
      "updateType": "DELETE_AND_UPDATE",
      "deviceOs": "WINDOWS",
      "buildDownloadUrl": "http://download.com/1",
      "tpaBuildState": "NOTIFIED",  // possible values: TO_BE_DOWNLOADED = DS server is yet to download the build,
                                    //                  DOWNLOADED_BUT_TO_BE_NOTIFIED = DS server has downloaded the build but is yet to notfify the devices,
                                    //                  NOTIFIED = DS server has downloaded the build and notified the devices,
                                    //                  MD5_CHECKSUM_MISMATCH = DS server has downloaded the build but there is a mismatch of MD5 checksum,
                                    //                  DOWNLOAD_FAILING = DS server could not download the build from the given url,
                                    //                  SAVING_BUILD_FAILED = DS server downloaded the build, the MD5 also matched but DS server is unable to save the build file in desired directory or S3 bucket
      "buildDate": "2019-05-15 09:46 UTC",
      "listOfDeviceIds": [
        175, 899
      ]
    },
    {
      "tpappId": 1,
      "md5checksum": "E73A1A78A60152FC9D4DFE13A03096AA",
      "updateType": "DELETE_AND_UPDATE",
      "deviceOs": "WINDOWS",
      "buildDownloadUrl": "http://download.com/2",
      "tpaBuildState": "NOTIFIED",
      "buildDate": "2019-05-15 09:44 UTC",
      "listOfDeviceIds": [
        453
      ]
    },
    {
      "tpappId": 1,
      "md5checksum": "E73A1A78A60152FC9D4DFE13A03096UU",
      "updateType": "DELETE_AND_UPDATE",
      "deviceOs": "WINDOWS",
      "buildDownloadUrl": "http://download.com/3",
      "tpaBuildState": "NOTIFIED",
      "buildDate": "2019-05-15 09:02 UTC",
      "listOfDeviceIds": [
        8989, 175
      ]
    }
  ],
  "pagination": null,
  "name": null,
  "code": null,
  "message": null
}
```

## IFrame APIs

### Add a iframe url
--------------------

    /iframe-url [POST]

HEADER

    Authorization: Bearer {userToken} 
    Content-Type:application/json

BODY
```javascript
{
  "iframeUrl": "string"
}
```

RESPONSE - code - 200
```javascript
{
  "result": {
    "iframeUrlId": 1, // long
    "iframeUrl": "string"
  },
  "name": null,
  "code": null,
  "message": null
}
```

### Update a iframe url
-----------------------

    /iframe-url/<iframeUrlId> [PUT]

HEADER

    Authorization: Bearer {userToken} 
    Content-Type:application/json

BODY
```javascript
{
  "iframeUrl": "string"
}
```

RESPONSE - code - 200
```javascript
{
  "result": {
    "iframeUrlId": 1, // long
    "iframeUrl": "string"
  },
  "name": null,
  "code": null,
  "message": null
}
```

### Get all iframe urls
-----------------------

    /iframe-url [GET]

HEADER

    Authorization: Bearer {userToken} 
    Content-Type:application/json

BODY

    NA

RESPONSE - code - 200
```javascript
{
  "result": [
    {
      "iframeUrlId": 1, // long
      "iframeUrl": "string"
    }
  ],
  "name": null,
  "code": null,
  "message": null
}
```

### Get a iframe url by id
--------------------------

    /iframe-url/<iframeUrlId> [GET]

HEADER

    Authorization: Bearer {userToken} 
    Content-Type:application/json

BODY

    NA

RESPONSE - code - 200
```javascript
{
  "result": {
    "iframeUrlId": 1, // long
    "iframeUrl": "string"
  },
  "name": null,
  "code": null,
  "message": null
}
```

### Delete a iframe url
-----------------------

    /iframe-url/<iframeUrlId> [DELETE]

HEADER

    Authorization: Bearer {userToken} 
    Content-Type:application/json

BODY

    NA

RESPONSE - code - 200
```javascript
{
  "result": null,
  "name": "SuccessfullyDeleted",
  "code": null,
  "message": "Succcessfully deleted"
}
```
