---
title: "unable to mount new hdd"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by BlacKsheep88 on 2007-07-13
I recently purchased a Seagate SATA drive and I formatted it to ext3 with Gparted, and put it in my fstab, which I've pasted here;


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1ced29c2-f88a-475e-bc1a-6e3f055d8d70 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=62e6169b-ecdc-4683-b085-175c3fc7d8a4 none            swap    sw              0       0
 /dev/hdd        /media/cdrom0   udf,iso9660 user,auto     0       0
 /dev/sda /media/Data ext3 user,rw,auto 0 0
```

Whenever I run mount -a, I get this message;

```
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` 
dmesg | tail shows; "[ 4542.992923] VFS: Can't find ext3 filesystem on dev sda."

Any tips?

---

### Post by merlinus on 2007-07-13
Try /dev/sda1 instead of /dev/sda

Also, you may need to manually create the mountpoint, if you have not already done so.

-merlin

---

