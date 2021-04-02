[![Last Commit][last-commit]][commits]
# Simple workspace of [PHP][1] <!-- omit in toc -->

- [Description](#description)
- [Default configuration](#default-configuration)
- [Acessing the container through brower](#acessing-the-container-through-brower)
- [Useful commands](#useful-commands)
  - [Start the container in *"detached"* mode](#start-the-container-in-detached-mode)
  - [To attach to the container you can use the container's ID or name](#to-attach-to-the-container-you-can-use-the-containers-id-or-name)
  - [To see what is currently running](#to-see-what-is-currently-running)

## Description
This docker compose file create for you an container of php using [*php:7-apache*][2] image that contains Debian's [Apache httpd][3] in conjunction with PHP (as mod_php) and uses mpm_prefork by default.

## Default configuration
* container's name _*my-php-workspace*_
* 1GB of shared memory
* default workdir as */var/www/html/*
* the *source* folder being mapped as */var/www/html/*
* internal port 80 exposed in 8081
* mod_rewrite enabled

You can enable and/or add other modules editing the DockerFile as the example below:

```
FROM php:7-apache

RUN a2enmod rewrite \
    && docker-php-ext-install pdo_mysql
```

## Acessing the container through brower
You can access the container page through url http://localhost:8080

## Useful commands

### Start the container in *"detached"* mode

```
$ docker-compose up -d
```

### To attach to the container you can use the container's ID or name

```
$ docker container attach my-php-workspace
```

### To see what is currently running

```
$ docker-compose ps
```

---

> For more informations about compose file check the [reference guide][reference-guide]

[1]: https://www.php.net/
[2]: https://github.com/docker-library/php/blob/1bc63c1ce4294a4ecb50c60dcf6a57d6749cba7d/7.4/buster/apache/Dockerfile
[3]: http://httpd.apache.org/

[reference-guide]: https://docs.docker.com/compose/compose-file/compose-file-v3/
[commits]: https://github.com/wvicente/php-workspace/commits/master
[last-commit]: https://img.shields.io/github/last-commit/wvicente/php-workspace/master?style=plastic&logo=github