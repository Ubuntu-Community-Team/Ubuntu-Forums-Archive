---
title: "AuthenTec AES2501 - Segmentation fault"
date: 2008-10-05
forum: General Help
---

### Post by skyggen on 2008-10-05
Hello. Is this bug fixed somehow? The fingerscanner on my Lenovo 3000 n200 works, but when sudo still is active it shows segmentation fault. See below:

> skyggen@skyggen-laptop:~$ sudo gedit /etc/pam.d/common-auth
Segmentation fault
skyggen@skyggen-laptop:~$ sudo -k
skyggen@skyggen-laptop:~$ sudo gedit /etc/pam.d/common-auth
Scan right middle finger on AuthenTec AES2501

And it works again, after i do sudo -k

Anyway around this?

---

