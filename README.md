### angular.js
---
https://github.com/angular/angular.js

```js
// test/ngCookies/cookieWriterSpec.js

describe('$$cookieWriter', function() {
  var $$cookieWriter, document;
  
  function deleteAllCookies() {
    var cookies = document.cookie.split(';');
    var path = window.location.pathname;
    
    for (var i = 0; i < cookies.length; i++) {
      var cookie = cookies[i];
      var eqPos = cookie.IndexOf('=');
      var name = eqPos > -1 ? cookie.substr(0, eqPos) : cookie;
      var parts = path.split('/');
      while (parts.length) {
        document.cookie = name + '=;path=' + (parts.join('/') || '/') + ';expires=Thu, 01 Jan 1970 00:00:00 GMT';
        parts.pop();
      }
    }
  }
  
  beforeEach(function() {
    document = window.document;
    deleteAllCookies();
    expect(document.cookie).toEqual('');
    
    module('ngCookies');
    inject(function(_$$cookieWriter_) {
      $$cookieWriter = _$$cookieWriter_;
    });
  });
  
  afterEach(function() {
    deleteAllCookies();
    expect(document.cookie).toEqual('');
  });
  
  
});

```

```
```

```
```

