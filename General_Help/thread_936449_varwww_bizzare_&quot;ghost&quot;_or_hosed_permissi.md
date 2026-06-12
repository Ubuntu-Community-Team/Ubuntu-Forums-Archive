---
title: "/var/www bizzare &quot;ghost&quot; or hosed permissions?"
date: 2008-10-02
forum: General Help
---

### Post by thirdpig on 2008-10-02
Had a few interupted server boots trying to get into my bios settings. At startup apache complained that /var/www was missing.

It's visible with the ls command but look at these permissions:

> root@xxx:/var# ls -al
ls: cannot access www: No such file or directory
total 48
drwxr-xr-x 15 root root  4096 2008-10-02 16:49 .
drwxr-xr-x 21 root root  4096 2008-06-13 06:10 ..
drwxr-xr-x  2 root root  4096 2008-09-12 06:41 backups
drwxr-xr-x 11 root root  4096 2008-06-13 06:10 cache
drwxr-xr-x 32 root root  4096 2008-06-20 12:34 lib
drwxrwsr-x  2 root staff 4096 2008-04-14 22:53 local
drwxrwxrwt  3 root root    60 2008-10-02 15:57 lock
drwxr-xr-x 13 root root  4096 2008-10-02 15:57 log
drwxrwsr-x  2 root mail  4096 2008-06-13 06:00 mail
drwxr-xr-x  2 root root  4096 2008-06-13 06:00 opt
drwxr-xr-x 16 root root   480 2008-10-02 15:57 run
drwxr-xr-x  6 root root  4096 2008-06-13 06:10 spool
drwxrwxrwt  2 root root  4096 2008-04-14 22:53 tmp
drwx------  2 root bin   4096 2008-06-13 08:53 webmin
d?????????  ? ?    ?        ?                ? www
root@xxx:/var# cd www
-bash: cd: www: No such file or directory
root@xxx:/var# chown -R root www
chown: cannot access `www': No such file or directory
root@xxx:/var# mv www /root/
mv: cannot stat `www': No such file or directory

Awfully stuck, I have a backup but at this point I can't even make a new /var/www directory.

---

