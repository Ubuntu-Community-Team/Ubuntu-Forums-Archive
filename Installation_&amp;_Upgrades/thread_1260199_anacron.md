---
title: "anacron"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by phillw on 2009-09-07
Hi,

I understand the bit about 127.0.0.1 - that is to be expected .. But, I don't understand about the rotation of the MySQL log file.

```

/etc/cron.daily/logrotate:
apache2: Could not reliably determine the server's fully qualified domain name, using
127.0.0.1 for ServerName
error: error running shared postrotate script for '/var/log/mysql.log /var/log/mysql/mysql.log
/var/log/mysql/mysql-slow.log '
run-parts: /etc/cron.daily/logrotate exited with return code 1
    

```

Thanks,

Phill.

---

