# parse-server-gcs-adapter
[![Build
Status](https://travis-ci.org/parse-server-modules/parse-server-gcs-adapter.svg?branch=master)](https://travis-ci.org/parse-server-modules/parse-server-gcs-adapter)
[![codecov.io](https://codecov.io/github/parse-server-modules/parse-server-gcs-adapter/coverage.svg?branch=master)](https://codecov.io/github/parse-server-modules/parse-server-gcs-adapter?branch=master)

parse-server adapter for Google Cloud Storage

# installation

`npm install --save parse-server-gcs-adapter`

# usage with parse-server

### using a config file

```
{
  "appId": 'my_app_id',
  "masterKey": 'my_master_key',
  // other options
  "filesAdapter": {
    "module": "parse-server-gcs-adapter",
    "options": {
      "projectId": "projectId",
      "keyFilename": "path/to/keyfile",
      "bucket": "my_bucket",
      // optional:
      "bucketPrefix": '', // default value
      "directAccess": false, // default value
      "resumable": false // default value
    }
  }
}
```

### using environment variables

Set your environment variables:

```
GCP_PROJECT_ID=projectId
GCP_KEYFILE_PATH=projectId
GCS_BUCKET=bucketName
```

And update your config / options

```
{
  "appId": 'my_app_id',
  "masterKey": 'my_master_key',
  // other options
  "filesAdapter": "parse-server-gcs-adapter"
}
```


### passing as an instance

```
var GCSAdapter = require('parse-server-gcs-adapter');

var gcsAdapter = new GCSAdapter('project',
								'keyFilePath',
								'bucket' , {
									bucketPrefix: '',
									directAccess: false,
									resumable: false
								});

var api = new ParseServer({
	appId: 'my_app',
	masterKey: 'master_key',
	filesAdapter: gcsAdapter
})
```

or with an options hash

```
var GCSAdapter = require('parse-server-gcs-adapter');

var gcsOptions = {
	"projectId": "projectId",
  "keyFilename": "path/to/keyfile",
  "bucket": "my_bucket",
  "bucketPrefix": '',
	"directAccess": false,
	"resumable": false
}

var gcsAdapter = new GCSAdapter(gcsOptions);

var api = new ParseServer({
	appId: 'my_app',
	masterKey: 'master_key',
	filesAdapter: gcsAdapter
})
```
