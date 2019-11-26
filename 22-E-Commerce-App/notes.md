
### bodyParser
```js
const bodyParser = (req, res, next) => {
  if (req.method === 'POST') {
    req.on('data', data => {
      const parsed = data.toString('utf8').split('&');
      const formData = {};

      for (let pair of parsed) {
        const [key, value] = pair.split('=');
        formData[key] = value;
      }
      req.body = formData;
      next();
    });
  } else {
    next();
  }
};
```

### Repository Approach
> A single class (repository) is reqponsible for data access. All records are stored and used as plain JS object

### Active Record Approach
> Every record is an instance of a 'model' class that has methods to save, update, delete this record.

