---
title: "command make sql (error)"
date: 2008-11-30
forum: General Help
---

### Post by snurexx on 2008-11-30
Well, first of all hello and im new on ubuntu and sry for my ignorancy but i can't solve it.
I tried many things except install sql got this message error.
Below:

checking for mysql_config... no
checking for mysql_init in -lmysqlclient... no
checking mysql.h usability... no
checking mysql.h presence... no
checking for mysql.h... no
checking MySQL library (optional)... no
configure: disabling MySQL (optional)
checking for pcre_study in -lpcre... no
checking PCRE library (optional)... no
configure: disabling PCRE (optional)
checking host OS... Linux
checking for MinGW... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/common/Makefile
config.status: creating src/char/Makefile
config.status: creating src/login/Makefile
config.status: creating src/ladmin/Makefile
config.status: creating src/char_sql/Makefile
config.status: creating src/txt-converter/Makefile
config.status: creating src/map/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/tool/Makefile
snurexx@ubuntu:~/cronus/Server/trunk$ make sql
MySQL not found or disabled by the configure script
make: ** [needs_mysql] Erro 1

Im trying to compile an emulator and make this one in sql type but i got this error.

If anyone could help me i'd thank u.

Best regards.

---

### Post by cariboo on 2008-11-30
Have you tried installing mysql-server-5.0 from the repositories? Go to System-->Administration-->Synaptic PAckage Manager and search for mysql-server-5.0.

It is way easier installing packages from the repositories, then it is to try and compile the program.

Mysql does not have a gui, so you may want to install phpmyadmin, which is also in the  repositories. It is web based, to access it once phpmyadmin istalled, open Firefox and in the address bar type:

```
http://localhost/phpmyadmine
```

See screenshot.

---

### Post by snurexx on 2008-11-30
Hi Thanks to your advance but even installing the latest mysql-server i tried to execute the same way and still get the same error.

Idk what to do.
:(

---

### Post by kannan02 on 2011-07-18
```
**sudo** **aptitude install libmysqlclient-dev**
```this one should work...

---

