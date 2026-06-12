---
title: "MySQL"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by Permafrost91 on 2006-01-15
I just did an update and upgrade via apt-get and now with a new MySQL version I always get these error messages. I apparently updated to 4.1 which didn't work so I thought using 5.0 would work but without any success.

These are the relevant outputs:

```
$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

and /var/log/syslog:

```

Jan 15 17:45:23 localhost mysqld[4052]: 060115 17:45:23 [Note] /usr/sbin/mysqld: Nor
mal shutdown
Jan 15 17:45:23 localhost mysqld[4052]:
Jan 15 17:45:23 localhost mysqld[4052]: 060115 17:45:23  InnoDB: Starting shutdown...
Jan 15 17:45:25 localhost mysqld[4052]: 060115 17:45:25  InnoDB: Shutdown completed; log sequence number 0 43655
Jan 15 17:45:25 localhost mysqld[4052]: 060115 17:45:25 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 15 17:45:25 localhost mysqld[4052]:
Jan 15 17:45:25 localhost mysqld_safe[5401]: ended
Jan 15 17:45:29 localhost mysqld_safe[5458]: started
Jan 15 17:45:29 localhost mysqld[5461]: 060115 17:45:29  InnoDB: Started; log sequence number 0 43655
Jan 15 17:45:29 localhost mysqld[5461]: 060115 17:45:29 [ERROR] Can't start server:
Bind on TCP/IP port: Cannot assign requested address
Jan 15 17:45:29 localhost mysqld[5461]: 060115 17:45:29 [ERROR] Do you already have
another mysqld server running on port: 3306 ?
Jan 15 17:45:29 localhost mysqld[5461]: 060115 17:45:29 [ERROR] Aborting
Jan 15 17:45:29 localhost mysqld[5461]:
Jan 15 17:45:29 localhost mysqld[5461]: 060115 17:45:29  InnoDB: Starting shutdown...
Jan 15 17:45:32 localhost mysqld[5461]: 060115 17:45:32  InnoDB: Shutdown completed; log sequence number 0 43655
Jan 15 17:45:32 localhost mysqld[5461]: 060115 17:45:32 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 15 17:45:32 localhost mysqld[5461]:
Jan 15 17:45:32 localhost mysqld_safe[5489]: ended
Jan 15 17:45:35 localhost /etc/init.d/mysql[5534]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jan 15 17:45:35 localhost /etc/init.d/mysql[5534]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan 15 17:45:35 localhost /etc/init.d/mysql[5534]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jan 15 17:45:35 localhost /etc/init.d/mysql[5534]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan 15 17:45:35 localhost /etc/init.d/mysql[5534]:
```

---

### Post by Permafrost91 on 2006-01-17
does no one have the same problem or any idea on how to solve this?

---

### Post by Permafrost91 on 2006-01-17
I discovered that I didn't have the correct permissions for /var/run/mysqld which holds the MySQL socket to access the MySQL database locally. I changed the permissions to 775 (owner: mysql, group: root) and now I can access my MySQL databases again.

---

### Post by Permafrost91 on 2006-01-23
The above solution works but the change isn't consistent. Every time the computer reboots the permissions are changed back to only give the root user access to the local MySQL. How can I make this change persistent in the filesystem?

---

