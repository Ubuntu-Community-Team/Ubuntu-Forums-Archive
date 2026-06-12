---
title: "sd card mounted read-only"
date: 2009-05-28
forum: Hardware
---

### Post by erydj on 2009-05-28
Folks, I have a problem with my sd card. I formatted the sd card in ext2, and suddenly I cannot write to it. I can write to it with sudo, but not as a user.

The sd card works fine when formatted as vfat. The /etc/mtab contains the following line:

```
/dev/mmcblk0p1 /media/sdaspire ext2 rw,nosuid,nodev,uhelper=hal 0 0
```

I am using Jaunty UNR on Acer Aspire One.

Any helps would be greatly appreciated. Thanks.

---

### Post by linesma on 2009-05-28
How did you format it?  If you use gparted, you should be able to use it.  Gparted is not installed by default.  To insall it go to the terminal and type: **sudo apt-get install gparted**

Then to run gparted, in the terminal type: **gparted**

This program works like the old Partition Magic.  Choose your drive, action, and then hit apply.

I hope this helps.

Linesma

---

