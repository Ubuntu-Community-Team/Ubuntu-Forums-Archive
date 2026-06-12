---
title: "WordPress script to copy from site A to B"
date: 2023-09-28
forum: Hardware
---

### Post by Raymond Day on 2023-09-28
Got WordPress for years now and want to auto back it up.

Some one may of done this all ready but not sure. There my be a script out there all ready that does this.

Went to Bing AI and ask it to make this script put a rsync in it so it should only copy the changes.

Don't want it to copy the hole database. It's on a SSD and would were it out faster.

Can wright a post in WordPress and it only saves the changes so they must be a way.

This must not work right because if I delete all tables it will not restore all it's messed up then.

So I hope some one can look at this script and fix it.

I took the names and passwords out Replace names with a and b and passwords with x's.

```
#!/bin/bash

# Define the connection details for both servers
server_a="root@a"
server_b="root@b-backup"

# Define the path for the last backup file
last_backup_file="/root/last_backup.txt"

# Get the timestamp of the last backup
last_backup=$(cat $last_backup_file)

# Dump the database from server A with only new entries
mysqldump --no-tablespaces -u wordpressuser -pbxxxxx wordpress > dump.sql

# Replace all occurrences of the server A URL with the server B URL
sed -i 's%https://a/blog%http://b-backup%g' dump.sql

# Copy the dump file to server B
rsync -azvp -e ssh dump.sql $server_b:/root/dump.sql

# Import the dump file into the database on server B
ssh $server_b "mysql -u wordpress -pxxxxx wordpress_wp < /root/dump.sql"

# Update the last backup timestamp
date +%Y-%m-%d_%H:%M:%S > $last_backup_file

# Clean up the dump file
rm dump.sql

echo "Database updated successfully!"
```

It's be grate to have this work right.

All so I guess it will replace even the server name if have it in the post text. Just like it to change it from the media files. Audio, Video, and photos. Have a link in the database.

Used this one line command so server a and log on to server b with out a password.

```
cat ~/.ssh/id_rsa.pub | ssh root@b-backup "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

-Raymond Day

---

### Post by SeijiSensei on 2023-09-28
I don't know exactly what you're trying to accomplish, but the [Duplicator]("https://wordpress.org/plugins/duplicator/") plugin for Wordpress is the easiest solution to create a copy of the site you can migrate to another server. I've used it a few times now, and it works like a charm.

---

### Post by Raymond Day on 2023-09-28
Installed the Duplicator and did the $50 that looks like it would be every year.

It just seems to much to do this. Seems complicated they got a lot of videos just to try and make it not complicated.

Right now it's Building Package and my WordPress Media is big about 4TB's. Looks like it's going to take 12:28:17 hours as I type this.

Doing a easy and fast command like this to copy my media works gate because only copies the changes.

```
rsync -avP --delete root@a:/var/www/html/blog/wp-content/uploads/ /var/www/html/wp-content/uploads
```

That command is on the b server.

If could get that script to work right it be fast for that too and could just put in it a cron job then it could just auto do it and any one can do the same for free.

-Raymond Day

---

### Post by SeijiSensei on 2023-09-29
I didn't pay a cent. Perhaps my site isn't as large as yours, but twelve hours is way longer than anything I ever experienced using Duplicator. Usually takes less than an hour to build the package.

---

### Post by Raymond Day on 2023-09-30
If could get this script to work and only save the changes it only take seconds. Just like a day post update and it does it right away. Then could easy set it up to auto back it up with a cron job any way you want easy. a hour or a day or a week or month or what every.

---

### Post by Raymond Day on 2023-09-30
On a WordPress backup I clear all the database tables and when I run it on it it looks like this with the error at the end.

```
mysqldump: [Warning] Using a password on the command line interface can be insecure.
sending incremental file list
dump.sql

sent 383,200 bytes  received 120,859 bytes  201,623.60 bytes/sec
total size is 298,568,911  speedup is 592.33
ERROR 1273 (HY000) at line 461: Unknown collation: 'utf8mb4_0900_ai_ci'
root@B:~#
```

Maybe it work if can edit the script to fix this.

Right now it just says the Hello world! 1 post. So it does not restore it. But in phpMyAdmin it looks like it's good.

Hope some one can help.

---

### Post by SeijiSensei on 2023-09-30
utf8mb4_0900_ai_ci

That's a type of character encoding. Looks like Unicode with multibyte support. You need to see if your DB can support that character set. If it only happens on one line, you can probably just ignore it.

This might help: [https://tecadmin.net/resolved-unknown-collation-utf8mb4_0900_ai_ci/](https://tecadmin.net/resolved-unknown-collation-utf8mb4_0900_ai_ci/)

---

### Post by Raymond Day on 2023-09-30
Thank you. I did that but then get some other error:

```
root@b-backup:~# sed -i 's/utf8mb4_0900_ai_ci/utf8_general_ci/g' dump.sql
root@b-backup:~# sed -i 's/CHARSET=utf8mb4/CHARSET=utf8/g' dump.sql
root@b-backup:~# mysql -u wordpress -pXXXXX wordpress_wp < /root/dump.sql
ERROR 1253 (42000) at line 25: COLLATION 'utf8mb4_unicode_520_ci' is not valid for CHARACTER SET 'utf8mb3'
root@b-backup:~#
```

They both have the same version of database too.

```
root@b-backup:~# php -v
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
root@b-backup:~#
```

---

### Post by SeijiSensei on 2023-10-03
i"m out of suggestions. I've ever only used [PostgreSQL]("https://www.postgresql.org/") since the 1990s. I do have a MySQL installation on my webserver since that's the only database Wordpress supports without a lot of fuss.

Did you open the file in an editor and look at line 25?

---

