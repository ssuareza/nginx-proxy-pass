# Nginx proxy pass

A simple container that proxy passes to an external source.

Simply run:

```
docker run -d -p 80:80 -e TARGET=<proxy location> ssuareza/nginx-proxy-pass
```

For example, want to proxy everything to google?

```
docker run -d -p 80:80 -e TARGET=https://google.com ssuareza/nginx-proxy-pass
```

Or maybe another server on your network:

```
docker run -d -p 80:80 -e TARGET=http://192.168.8.15:8080 ssuareza/nginx-proxy-pass
```

## Use authentication

Just mount a htpasswd file. Example:

```sh
docker run -d -p 80:80 \
  -v .htpasswd:/etc/nginx/.htpasswd
  -e TARGET=<proxy location> \
  ssuareza/nginx-proxy-pass
```

To create a htpasswd file run:

```sh
htpasswd -c .htpasswd user1
```
