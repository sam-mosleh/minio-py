# Minimal object storage library for Python [![Build Status](https://travis-ci.org/minio/minio-py.svg)](https://travis-ci.org/minio/minio-py)

## Install

This library is tested against both python 2.7 and python 3.4. The recommended technique for installing this package
is through pip.

```sh
$ pip install minio
```

## Example

```python
# Instantiate a client
client = Minio('https://s3.amazonaws.com', 
                access_key='access_key', 
                secret_key='secret_key')
                     
# Make a new bucket
client.make_bucket('my_bucket')

# Upload a file
file_stat = os.stat('data.json')
with open('data.json', 'rb') as data_file:
    client.put_object('my_bucket', 'data.json', file_stat.st_size, data_file)


# List objects on server
objects = client.list_objects('my_bucket')
for obj in objects:
    print 'object:', obj.key, obj.last_modified

# Get an object and print each chunk to console
object_data = client.get_object(bucket, 'hello/world')
for object_chunk in object_data:
    print object_chunk
```

## Examples:

### Bucket

[make_bucket(bucket, acl=Acl.private())](examples/make_bucket.py)

[list_buckets()](examples/list_buckets.py)

[bucket_exists(bucket)](examples/bucket_exists.py)

[remove_bucket(bucket)](examples/remove_bucket.py)

[get_bucket_acl(bucket)](examples/bucket_acl.py)

[set_bucket_acl(bucket, acl)](examples/bucket_acl.py)

[drop_all_incomplete_uploads(bucket)](examples/drop_incomplete_uploads.py)

### Object

[get_object(bucket, key, offset=None, length=None)](examples/get_object.py)

[put_object(bucket, key, length, data, content_type='application/octet_stream')](examples/put_object.py)

[list_objects(bucket, prefix=None, recursive=True)](examples/list_objects.py)

[stat_object(bucket, key)](examples/stat_object.py)

[remove_object(bucket, key)](examples/remove_object.py)

[drop_incomplete_upload(bucket, key)](examples/drop_incomplete_uploads.py)

## Join The Community
* Community hangout on Gitter    [![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/minio/minio?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
* Ask questions on Quora  [![Quora](http://upload.wikimedia.org/wikipedia/commons/thumb/5/57/Quora_logo.svg/55px-Quora_logo.svg.png)](http://www.quora.com/Minio)

## Contribute

[Contributors Guide](./CONTRIBUTING.md)
