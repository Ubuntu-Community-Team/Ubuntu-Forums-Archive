---
title: "Error creating mysql database"
date: 2008-07-27
forum: General Help
---

### Post by hallikpapa on 2008-07-27
I installed Linux 2.6.15-51-sparc64 and have
mysql version 5.0.22-Debian_0ubuntu6.06.10 installed.

I have my datadir directory owned by mysql:mysql as well as everything else under that directory.

I can successfully restart mysql and it works great. I created a user with full permissions with grant option, and even tried with the root mysql user. But I get this error when trying to create a database:

ERROR 1006 (HY000): Can't create database 'los' (errno: 13)

help....

---

### Post by RealPSL on 2008-07-28
Are you using the default datadir or one you created. If you are not using the default you might want to make sure you are not getting denied by apparmor.

---

