---
title: "need help, ld.so.cache~ corrupted"
date: 2008-11-24
forum: General Help
---

### Post by dazift on 2008-11-24
while installing a program in add/remove my computer powered off. now when i try to install something it gives me an error saying to run dpkg --configure -a and i did but i get back:
```
$ sudo dpkg --configure -a
Setting up libc6 (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: Renaming of /etc/ld.so.cache~ to /etc/ld.so.cache failed: No such file or directory
dpkg: subprocess post-installation script returned error exit status 1

```
when i try sudo apt-get update or upgrade it gives the same run dpkg config error

plz help!

---

