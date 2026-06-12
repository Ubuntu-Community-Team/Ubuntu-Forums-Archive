---
title: "New external USB Hard Drive"
date: 2008-08-20
forum: Hardware
---

### Post by jim78 on 2008-08-20
Hi,

I've just got a new usb hd and formatted it with ext3 on ubuntu 8.04. It mounts at startup and I can click into it, but can't write to it. I tried to edit fstab but it wasn't in there. I tried adding the last bit (#/dev/sdf1 etc) but it hasn't worked. what have  I done wrong?

Thanks, James.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=385444ce-2452-4fc0-9b7c-516ba3418f78 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6eedb004-d214-434e-ab11-82741eab4777 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/sdf1
UUID=76dbce49-8e95-498e-87c7-03e3e5c385d7    /media/disk       ext3     user ,auto,exec        0       0

---

