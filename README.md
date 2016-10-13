[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://orleika.github.io/mit-license)
[![nginx](http://img.shields.io/badge/nginx-v1.11.5-blue.svg?style=flat-square)](https://nginx.org/en/download.html)
[![LibreSSL](http://img.shields.io/badge/LibreSSL-v2.5.0-blue.svg?style=flat-square)](https://www.libressl.org/)

# orleika/web-static
small-secure-fast and static web server.  
kudos for [Wonderfall/dockerfiles](https://github.com/Wonderfall/dockerfiles).

## Get Started
```
$ docker pull orleika/web-static
$ docker run -d -p 80:80 orleika/web-static
```

## Features

### small
- Based on **Alpine Linux**, which is known as lightweight Linux distribution.
- **nginx** built without unnecessary modules for static contents server.

This docker image size is only about *21MB*.

### secure
- **LibreSSL**, which is one of the most secure SSL library. nginx built against it.
- **nginx** built using hardening gcc flags.
- Hide server name using headers More module.
- Adjusted configuration considering DDoS attacks.

### fast
- HTTP2 support.
- AIO Threads support.
- Brotli compression support.
- pcre-jit enabled.
- Optimized configuration.

## configuration
<pre>
/etc/ngix
├── conf.d
│   ├── block_bots
│   ├── block_hotlink
│   ├── block_spams
│   ├── headers_params
│   ├── ssl_params
│   ├── vhost_http.conf
│   └── vhost_https.conf
├── nginx.conf
└── sites-enabled
     └── default.conf
</pre>

- `conf.d/headers_params`:
includes X-Frame-Options, X-XSS-Protection, X-Content-Type-Options, CSP.
- `conf.d/vhost_http.conf`: secure HTTP configuration.
- `conf.d/vhost_https.conf`: more secure HTTPS configuration.
- `sites-enabled/default.conf`: default conf file. You should replace new configuration file referring `conf.d/vhost_http?s.conf`.
