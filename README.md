# railsDevelopmentEnvironmentOnDocker
## Setup

1. `docker-compose run web rails new . --force --database=mysql`
1. `docker-compose build`
1. `cd config` edit `database.yml` like this
```
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: mysqlRootPW # 追加
  host: db # 変更
```

1. `docker-compose up -d`
1. `docker-compose run web bundle exec rails db:create`
1. Access `localhost:3000` with browser