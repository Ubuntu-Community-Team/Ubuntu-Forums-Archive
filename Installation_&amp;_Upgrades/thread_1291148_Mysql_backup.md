---
title: "Mysql backup"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by vksingh on 2009-10-14
Hi,

Can some body tell how to backup mysql data base?

Thanks,

Vivek

---

### Post by DaithiF on 2009-10-14
use mysqldump
example usage:
```
mysqldump -h host -u user -ppassword --databases database1 database2 > mysqlbackup.bak

```

---

### Post by vksingh on 2009-10-14
How to create database files at given location?

Thanks,

Vivek

---

### Post by DaithiF on 2009-10-14
what do you mean -- create a backup of a single database at a certain location?
```
mysqldump -h host -u user -ppassword --databases databasename > /path/to/yourbackup.bak
```
or just:
```
mysqldump -h host -u user -ppassword databasename > /path/to/yourbackup.bak
```

---

