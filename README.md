# Dev Platform

I use dev platform every day. It has the usual services needed like postgresql and redis, more some extras like a custom fileserver provided by nginx+webdav protocol, some scripts utils for rapid db provisioning, pgadmin4 for administration, a local docker registry and more. 

This project it has faced different changes, where SSL support was added. In the last version, SSL is not used but the scripts needed for cert creation and managment still exists.

# Check references

https://gist.github.com/cboettig/8643341bd3c93b62b5c2


https://stackoverflow.com/questions/22665809/how-to-configure-ipython-behind-nginx-in-a-subpath/23912400#23912400

https://jupyter-docker-stacks.readthedocs.io/en/latest/using/recipes.html#dask-jupyterlab-extension

## Fileserver

Put object:
```
curl -v -L -X PUT -d bigswag https://fileserver.local:4444/wehave
```

Get object:
```
curl -v -L https://fileserver.local:4444/wehave
```

## Webdav server

The original implementation of webdav in nginx doesn't implement all the options required for a full webdav store.

The following projects use external modules for nginx:
- https://github.com/dgraziotin/docker-nginx-webdav-nononsense
- https://www.robpeck.com/2020/06/making-webdav-actually-work-on-nginx/

## Postgresql

Because postgres allows the use of extensions, a custom image is provided with pgvector support. But also it keeps the default image.
Migration: 
https://github.com/tianon/docker-postgres-upgrade
