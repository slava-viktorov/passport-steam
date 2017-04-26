# FORK Passport-Steam
An optional parameter for adding characters at the end of a name

[Passport](https://github.com/jaredhanson/passport) strategy for authenticating
with [Steam](http://steamcommunity.com/) using OpenID 2.0.


## Installation

```bash
$ npm install --save passport-steam-some
```

## Usage

#### Configure Strategy

The Steam authentication strategy authenticates users using a steam account,
which is also an OpenID 2.0 identifier.  The strategy requires a `validate`
callback, which accepts this identifier and calls `done` providing a user.
Additionally, options can be supplied to specify a return URL and realm.

```javascript
passport.use(new SteamStrategy({
    returnURL: 'http://localhost:3000/auth/user/return',
    realm: 'http://localhost:3000/',
    apiKey: 'your steam API key'
  },
  function(identifier, profile, done) {
    User.findByOpenID({ openId: identifier }, function (err, user) {
      return done(err, user);
    });
  },
  '1'
));

passport.use(new SteamStrategy({
    returnURL: 'http://localhost:3000/auth/admin/return',
    realm: 'http://localhost:3000/',
    apiKey: 'your steam API key'
  },
  function(identifier, profile, done) {
    User.findByOpenID({ openId: identifier }, function (err, user) {
      return done(err, user);
    });
  },
  '2'
));

passport.authenticate('steam-1', (err, user, info) => {
...
passport.authenticate('steam-2', (err, user, info) => {
...
```
