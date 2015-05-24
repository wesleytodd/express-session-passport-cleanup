# Don't Create Anymore Empty Sessions

There is this silly issue where [passport](http://passportjs.org) modifies the session causing [express-session](https://github.com/expressjs/session) to create a bunch of extra sessions.  This module fixes that by using a method similar to that recommended by [@Joris-van-der-Wel](https://github.com/Joris-van-der-Wel) [here](https://github.com/jaredhanson/passport/issues/279#issuecomment-69839937).  This module instead overrides the end method on res, becuase either things have changed in `express-session` or that solution never worked correctly.

## Install

```
$ npm install --save express-session-passport-cleanup
```

## Usage

```javascript
var expressSessionPassportCleanup = require('express-session-passport-cleanup');

app.use(session({/* ... */}));
// Include it right after the express session middleware
app.use(expressSessionPassportCleanup);
app.use(passport.initialize());
app.use(passport.session());
```
