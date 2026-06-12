---
title: "Kubuntu 10.10.  USB flash permissions"
date: 2011-07-04
forum: Hardware
---

### Post by Lexus45 on 2011-07-04
Hi all.

Suddenly one of our clients got a problem. He can not access his flash disks without "sudo".
Kubuntu 10.10.
------------
support@maksim:~$ sudo ls -l /media/

drwxr-xr-x  2 root  root  4096 2011-04-04 19:29 cdrom
**drwxr-xr-x 16 maxim root 16384 2011-07-04 11:03 disk**
lrwxrwxrwx  1 root  root     7 2011-04-04 19:26 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2011-04-04 19:26 floppy0
**drwxr-xr-x 29 maxim root 65536 2011-07-04 11:01 NOKIA N900**
------------

But as we see, the owner of "disk" and "NOKIA N900" is our user "maxim". And he has rwx permissions.

What's the best way to fix the problem? It's desirable to have access to these disks without "sudo".

---

