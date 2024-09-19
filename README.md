### spin up our containerised services

```bash
docker compose up -d #run all containers in detached mode kind of like -dit
```

### migrate(create) all DB table from schemas defined in \*/src/models for each services

```bash
docker-compose exec api-gateway npx sequelize db:migrate
docker-compose exec flights-service npx sequelize db:migrate
docker-compose exec booking-service npx sequelize db:migrate
docker-compose exec notification-service npx sequelize db:migrate
```

### seed all service data in db

```bash
docker-compose exec api-gateway npx sequelize db:seed:all
docker-compose exec flights-service npx sequelize db:seed:all
docker-compose exec booking-service npx sequelize db:seed:all
docker-compose exec notification-service npx sequelize db:seed:all
```

### check if all data seeded or not in db tables

```bash
docker-compose exec api-gateway mysql -u root -p
mysql>use service_db;
mysql>show tables;
mysql>select * from Roles;
```
