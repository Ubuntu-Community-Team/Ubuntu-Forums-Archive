---
title: "Help mounting my 2nd ext3 hdd"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by idn on 2005-09-17
does anyone know how to do this? I want it to mount to /mnt/shared, the device is /dev/sdb1, the filesystem is etx3.

This only contains music and movies, no system files. I dont know hat to put in /etc/fstab though

thanks

---

### Post by idn on 2005-09-17
Don't worry I have fixed this problem, i set my fstab file to:

/dev/sdb1       /mnt/shared               ext3    rw,user,noauto  0       0

---

