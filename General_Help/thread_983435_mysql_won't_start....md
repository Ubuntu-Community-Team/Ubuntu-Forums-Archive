---
title: "mysql won't start..."
date: 2008-11-15
forum: General Help
---

### Post by nappymonster on 2008-11-15
hi all,
I got torrentflux B4RT running successfully earlier, but rebooted the machine and then suddenly, at localhost/flux i get:
Database Connection Problems

Check your database-config-file. (inc/config/config.db.php)


So i decided to restart mysql, but I don't think it was ever started (since the reboot). It [OK]s the stopping, but it [Fail]s the starting...

I am running Hardy Desktop
Any ideas?
Thanks.

---

### Post by beno1990 on 2008-11-15
Go to /etc/mysql/my.conf and ensure your configuration is correct; MySQL won't start if it detects a problem configuration on startup. If you're not sure how, try installing the MySQL GUI tools from the repositories; you can set up your configuration from there.

---

