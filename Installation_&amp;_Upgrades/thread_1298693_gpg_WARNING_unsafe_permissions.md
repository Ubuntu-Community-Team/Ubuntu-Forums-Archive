---
title: "gpg: WARNING: unsafe permissions"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by 00chilli00 on 2009-10-23
Hi,
( sorry about warning in caps , its what the error said so yeh)
Im having some issues getting any gpg keys added =O.
This is the error.
chilli0@chilli0:~$ sudo gedit /etc/apt/sources.list
[sudo] password for chilli0: 
chilli0@chilli0:~$ gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: WARNING: unsafe permissions on configuration file `/home/chilli0/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/chilli0/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
chilli0@chilli0:~$ 

Anyone know how to fix?
Thanks

---

### Post by 00chilli00 on 2009-10-23
I also changed the perms on the file /home/chilli0/.gnupg/gpg.conf
That everything could read and write ( set to chilli0)

---

### Post by 00chilli00 on 2009-10-23
I also changed the perms on the file /home/chilli0/.gnupg/gpg.conf
That everything could read and write ( set to chilli0)

---

### Post by Barriehie on 2009-10-28
I too was getting those messages and changed the permissions of both the .gnupg folder and gpg.conf as per the attached screenshot and now it works.

Barrie

---

