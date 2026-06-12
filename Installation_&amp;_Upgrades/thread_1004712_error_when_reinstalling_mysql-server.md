---
title: "error when reinstalling mysql-server"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by devliljohn on 2008-12-07
i am getting this error when i try to reinstall mysql-server:

```
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 258: 14601 Segmentation fault      update-rc.d mysql-ndb-mgm defaults 17 23 > /dev/null
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up module-init-tools (3.3-pre11-4ubuntu5.8.04.1) ...
Segmentation fault
dpkg: error processing module-init-tools (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 module-init-tools
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any ideas? this is on ubuntu 8.04 server.

---

### Post by lovelyvik293 on 2008-12-07
I think you have the problem with the dependances of the Mysql.
just install the dependances first.

---

