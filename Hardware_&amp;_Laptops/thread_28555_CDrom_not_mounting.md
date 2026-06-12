---
title: "CDrom not mounting"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by Jones on 2005-04-20
Hey all,

I have recently installed  Ubuntu and it has worked perfect for me. However, the last few days, whenever I try and mount a cdrom that is in the drive, I get the following error message:

```
root@ubuntu:/home/chris # mount /media/cdrom0
mount: can't open /etc/mtab for writing: Input/output error
```

I have tried different disks and all get the same error. If you need more information just post here and I'll try and get back soon.

---

### Post by diebels on 2005-04-20
So it is not automounted?

---

### Post by Jones on 2005-04-21
well its not automounted and when I try to manually mount the drive, it won't mount and gives me the error.

---

### Post by diebels on 2005-04-21
Ubuntu is supposed to automount fine. But if it's not, is "mount /media/cdrom0" all you're giving mount to work on? Do you have a line for it in /etc/fstab? The error message looks a bit funny though.
Can you post output of:
cat /etc/fstab
cat /etc/mtab
ls -lah /dev/cd*

---

### Post by Jones on 2005-04-21
[QUOTE=diebels]Do you have a line for it in /etc/fstab?[/QUOTE]

uh not sure what that meant but heres the output for what you told me to do.


```
root@ubuntu:/home/chris # ls -lah /dev/cd*
lrwxrwxrwx    1 root     root            8 2005-03-27 18:13 /dev/cdrom -> /dev/hdc
brw-rw----    1 root     cdrom     24,   0 2004-10-12 16:23 /dev/cdu535

root@ubuntu:/home/chris # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

root@ubuntu:/home/chris # cat /etc/mtab
cat: /etc/mtab: Input/output error
```

---

### Post by diebels on 2005-04-21
Looks like you have some file corruption. Do a reboot with fsck:
"shutdown -F -r now"

---

### Post by Jones on 2005-04-22
alright. Thanks for the replys. I'll respond tomorow if this works!

---

### Post by Jones on 2005-04-22
Awsome. It works now! Thanks for all your help man.

---

