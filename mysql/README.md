The docker compose creates a pretty default mysql container.

I put the environmental variable for building with the root password in a file called mysql-root. If you need to do it another way, change those environmenal variables there.

Build it with"

```bash
MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD docker-compose up
```
access mysql from root with 
```bash
docker exec -it <CONTAINER ID OR NAME> mysql -u root -p
```

Enter your password, create a user and grant access to the tables. Make sure the user@host host allow access from the host or outside.

Login to mysql via
```
mysql --protocol=tcp -P 3306 -h 127.0.0.1 -u $MYSQL_USERNAME -p
```

The dockerfile sets the volume to:
auth-db_auth-db-vol

To create a backup/dump.
```bash
sudo docker exec <CONTAINER ID OR NAME> sh -c 'exec mysqldump --all-databases -u root -p"$MYSQL_ROOT_PASSWORD"' > auth-db-dump.sql
```
