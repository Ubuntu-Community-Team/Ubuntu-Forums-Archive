---
title: "Ubuntu do not mount /home"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by seimulus on 2009-09-19
Hi to all. after looking for a solution for my problem i cannot be able to find it, so I tell my problem here.
After a reboot, ubuntu sends the next error: "kinit. no resume image...". I solved with a swapoff/mkswap of /dev/sda3 (swap).
then, ubuntu starts normally, but no graphic display appears. Only a console. From console I logged and start GDM. the error is that don't exist /home (dev/sda8).
Looking for I've foud that ubuntu doesn't mount /dev/sda8 at start. So If I try...
 $ sudo mount -a
 $ sudo gdm
the system starts normally. 
How can I do to get /home automatically mounted and gdm starting?
thanks

---

### Post by SuperSonic4 on 2009-09-19
What is the ouput of ```
cat /etc/fstab
```

---

### Post by seimulus on 2009-09-19
That's it. I think there's nothing bad...

```
camulus@MIKAC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1ea50327-fee6-45a4-b950-15a0e4592597 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=709F-A194              /FAT32            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=82c4d455-d158-4ebb-a1b7-021d51afa5d1 /boot           ext3    relatime        0       2
# /dev/sda8
UUID=bbd68d58-e7c6-47a3-b24d-e8e2afefd784 /home           xfs     relatime        0      2
# /dev/sda6
UUID=b982cda8-79cb-4573-b7ee-43eded3d73ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
camulus@MIKAC:~$ 

```

---

### Post by seimulus on 2009-09-21
No more ideas? I have thinking about reinstalling the system but I think that solution must be a little thing...
Can anybody help me?

---

