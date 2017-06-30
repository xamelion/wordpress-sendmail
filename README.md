# docker-wordpress-sendmail
a docker image of wordpress with sendmail installed so that php mail works

## Usage

Use this image(`osexp2000/wordpress-sendmail`) to replace `wordpress`(without `:tag`) or `wordpress:*apache*` in your `docker-compose.yml`

Sample `docker-compose.yml`

```
version: '2'

services:
  wordpress:
    depends_on:
      - db
    #image: wordpress
    image: osexp2000/wordpress-sendmail   #####here#####
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress

  db:
    image: mysql
    volumes:
      - ./db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
```
