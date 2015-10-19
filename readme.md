
# Node Cookie

![](http://i1117.photobucket.com/albums/k594/thetutlage/poppins-1_zpsg867sqyl.png)

`node-cookie` is a standalone I/O module for reading and writing cookies on http request.
Out of the box it has support for

1. signed cookies.
2. encrypted cookies.

## See also

1. node-req
2. node-res

## Basic Setup

```javascript
const http = require('http')
const nodeCookie = require('node-cookie')

http.createServer(function (req, res) {

  // this will update set-cookie header on res object.
  nodeCookie.create(req, res, 'user', 'virk')

}).listen(3000)
```

## Signing cookies with a secret

```javascript
const http = require('http')
const nodeCookie = require('node-cookie')

http.createServer(function (req, res) {

  nodeCookie.create(req, res, 'user', 'virk', 'secret')

}).listen(3000)
```

## Signing & encrypting cookies with a secret

```javascript
const http = require('http')
const nodeCookie = require('node-cookie')

http.createServer(function (req, res) {

  nodeCookie.create(req, res, 'user', 'virk', 'secret', true)

}).listen(3000)
```

## Methods

#### create (req, res, key, value, secret=null?, encryptCookie=false?)

```javascript
nodeCookie.create(req, res, 'somekey', 'somevalue', 'yoursecret', true)
```

#### clear (req, res, key)

remove existing cookie from http request

```javascript
nodeCookie.clear(req, res, 'somekey')
```

#### parse (req, secret=null?,decryptCookie=false?)

parse cookies from request. Note - nodeCookie can only decrypt and unsign cookies created via `node-cookie`

```javascript
nodeCookie.parse(req, 'somesecret', true)
```
