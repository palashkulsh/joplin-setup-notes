# joplin-setup-notes


* when shutting down docker-compose file, docker is not able to stop as apparmor is not allowing it to stop, so either disable it or remove it
* removing apparmor removes other software also like docker and containerd in mycase so tread carefully
* to take backup use following command
* `sudo docker exec docker-joplin_db_1 sh -c 'pg_dumpall -U joplin' > ~/$(date +%Y-%m-%d)_psql.backup.sql`
* setup crontab to setup (`sudo crontab -e`) automatic backup job `@hourly sudo docker exec docker-joplin_db_1 sh -c 'pg_dumpall -U joplin' > /tmp/$(date +\%Y-\%m-\%d__\%H__\%M)_psql.backup.sql 2>&1`
