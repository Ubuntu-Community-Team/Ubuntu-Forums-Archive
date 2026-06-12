---
title: "removing log files"
date: 2008-11-02
forum: General Help
---

### Post by Woody1987 on 2008-11-02
My Ubuntu 8.04 server box keeps filling up with logs specifically kern.log.0 debug.0 syslog.0. These fill up my entire root parition, and i have to manually remove them every couple of weeks. Why is this? and how do i stop it?

---

### Post by cariboo on 2008-11-02
Are you using **logrotate**? my server keeps a maximum of 8 entries for each service eg:

```
-rw-r----- 1 syslog      adm       61589 2008-11-02 12:07 syslog
-rw-r----- 1 syslog      adm      288682 2008-11-02 00:05 syslog.0
-rw-r----- 1 syslog      adm       28982 2008-11-01 00:02 syslog.1.gz
-rw-r----- 1 syslog      adm       99028 2008-10-31 00:27 syslog.2.gz
-rw-r----- 1 syslog      adm     2106295 2008-10-30 00:29 syslog.3.gz
-rw-r----- 1 syslog      adm       21232 2008-10-28 00:31 syslog.4.gz
-rw-r----- 1 syslog      adm     7008635 2008-10-27 01:05 syslog.5.gz
-rw-r----- 1 syslog      adm        5489 2008-10-26 00:12 syslog.6.gz
```

It deletes anything oldrer.

Jim

---

### Post by Woody1987 on 2008-11-02
im not sure, but i checked and it is installed, how do i use it?

---

### Post by Woody1987 on 2008-11-04
bump

---

