---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true

code_clipboard: true
---

# Introduction

Welcome to the OCRAN Enterprise API documentation. The OCRAN Enterprise
API allows a client to upload receipt documents and view the raw results in
the form of a structured data set.

Sample code is available for reference in Java, and Python on the right. The
Java code requires the Unirest library. The Python code requires the Unirest
and Json libraries.

To integrate the OCRANE Enterprise API with your application, check out the
[Getting Started] section for a step-by-step guide and workflow overview.

# Releases

<aside class="notice">
 API releases are always backwards compatible. Any major releases
 will be communicated and documented ahead of time.
 </aside>

## Upcoming

 <aside class="success">
 Uploaded!
 </aside>


## Change log

#### Released July 07,2021
#### Released June 20,2021

### Summary

Any user can signup as a new user and then
sign in as per requirement. Upon signing in
the user will be assigned a unique key named as
"Public key". User can then upload a document with
the constraint of two fields, namely:<br>
1. image<br>
2. public_key

Then in return, the user gets the jason in response
to the request uploaded.

# POST Module

## Get all posts

```ruby
require 'uri'
require 'net/http'

url = URI("http://107.22.71.37:5001/get_imageurl")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request["cache-control"] = 'no-cache'
request["postman-token"] = 'cf67148d-17ac-cba5-2001-3a3d316dbc43'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"image\"; filename=\"connectssh.txt\"\r\nContent-Type: text/plain\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"public_key\"\r\n\r\n24e595bfd1c158ac2b2747c62def91f177bde934ceda7a9ecce5117cc8838eb4\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "http://107.22.71.37:5001/get_imageurl"

payload = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"image\"; filename=\"1079-receipt.jpg\"\r\nContent-Type: image/jpeg\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"pk\"\r\n\r\n85f84bb45856bf1c4f41c436ae55d1ba8b76cd16433006545b9b12308d7a0e03\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"
headers = {
    'content-type': "multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW",
    'cache-control': "no-cache",
    'postman-token': "27671293-3db2-0d59-2969-4514e31a539e"
    }

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```shell
curl --request POST \
  --url http://107.22.71.37:5001/get_imageurl \
  --header 'cache-control: no-cache' \
  --header 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  --header 'postman-token: e021c3ac-627c-0294-85b1-66b39d140ee1' \
  --form image=@connectssh.txt \
  --form public_key=24e595bfd1c158ac2b2747c62def91f177bde934ceda7a9ecce5117cc8838eb4
```

```javascript
var form = new FormData();
form.append("image", "1079-receipt.jpg");
form.append("pk", "85f84bb45856bf1c4f41c436ae55d1ba8b76cd16433006545b9b12308d7a0e03");

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://107.22.71.37:5001/get_imageurl",
  "method": "POST",
  "headers": {
    "cache-control": "no-cache",
    "postman-token": "8b3eec85-2d88-b490-680f-c9e992ad86d6"
  },
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> The above command returns JSON structured like this:

```json
[{"Result": {"total": "     TOTAL 235.19, conf: 0.28", 
  "address": "     FALMOUTH RAW BAR  56 Scranton Ave., conf: 0.5", 
  "subtotal": "     Items 219.81 |  aan iM tay 15 90, conf: 0.33", 
  "phone_number": "     Falmouth, MA 02540  (508) 548-7729, conf: 0.47", 
  "items": [[[" Gt OS Pe", 0.39, "et", 0.38], 
    [" Gt OS Pe", 0.39, "et", 0.38],
    [" 1..6 Gt OS Pe", 0.67, "19.00", 0.64], 
    [" 1..6 Oysters Chips", 0.94, "22.00", 0.43],
    [" 1..Fish and 114.00", 0.92, "", 0], 
    [" 3..MONSTAH Wings", 0.92, "12.00", 0.9], 
    [" 1..Chicken Wings", 0.62, "28.50", 0.87], 
    [" 3..4#Patron Wine", 0.65, "22.00", 0.77], 
    [" 1..#0pen Wine double tax included)", 0.87, "6.00", 0.95]]]}, 
  "image": "receipt-20210701112354398.jpg"}]
```

### HTTP Request

`GET http://107.22.71.37:5001/get_imageurl`

### Request Information

|Category|Value|
|---------|-----|
|Http Request|'POST'|
|URL|http://107.22.71.37:5001/get_imageurl|

### Headers

No headers required for this request

### Input Schemas for requests

|Field|Meaning|
|-------|------|
|image|The image of receipt to be uploaded|
|public_key|Public Key generated by Ocran |

### Output Schemas of requests

|Field|Meaning|
|-------|------|
|total|Total bill one has to pay inclusive of taxes|
|address|Address of the place|
|subtotal|Bill without taxes|
|phone_number|Phone number of the place|
|items|The items which were ordered|

# Errors

The Enterprise API uses the following error codes:

| Error Code | Body                                                                                                                                | Meaning                  | In Depth Meaning                                                                                   |
|------------|-------------------------------------------------------------------------------------------------------------------------------------|--------------------------|----------------------------------------------------------------------------------------------------|
| 400        | {"error": "Minimum file size is 100KB"}                                                                                             | Not Found                | Reason may be one of the following:                                                                              |
|            | {"error": "Maximum file size is 5MB"}                                                                                               |                          | Size of document is out of bounds                                                      |
|            | {"error": "The browser (or proxy) sent a request that this server could not understand."}                                           |                          | Spelling mistake in input keywords                                                                                       | 
| 401        | {"error": "access denied - invalid token or account"}                                                                               | Unauthorized             | Recheck the API token                                                      |
| 404        | {"message":"The requested URL was not found on the server. If you entered the URL manually please check your spelling and try again."}| Not Found                | Path leading to a particular document may have some problem                                                         |
| 405        | {"message":"Method not allowed."}                                                                                                   | Method Not Allowed       | the request has been received and recognized by the web server but the specific HTTP method has been rejected                                   |
| 415        | {"error": "multipart/form-data is the only content type allowed for document upload"}                                               | Unsupported Content-Type |The format of payload of Origin server may be different than the format at target resource.                           |
| 500        | {"error": "The server encountered an internal error and was unable to complete your request. Either the server is overloaded or     | Internal Server Error    | login credentials may have a problem
|            |   there is an error in the application"}                                                                                           |                           |                                                                                                                 |   
|            |                                                                                                                                     |                          | Browser Cache                                                                                         |
|             |                                                                                                                                     |                          |Problem in File/Folder permissions                                    |

## Error responses while using Postman


 Body                                                                                                                                | Meaning                  | In Depth Meaning                                                                                   |
-------------------------------------------------------------------------------------------------------------------------------------|--------------------------|----------------------------------------------------------------------------------------------------|
{"error": "Wrong image type, please select valid image type(jpg ,png ,jpeg ,JPG)"}                                                   | Mismatch                | if wrong image type is chosen or not chosen at all                              |
{"error": "Your remaining quota is less than requested files. please update your quota limit"}                                       | incomplete              | If wrong/incomplete public_key is written                                                      |
{"error": "no items detected"}                                                                                                      | wrong image              | If image with no information is uploaded!                                                                                       | 

