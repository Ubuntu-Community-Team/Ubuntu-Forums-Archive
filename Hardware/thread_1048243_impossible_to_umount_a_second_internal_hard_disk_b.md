---
title: "impossible to umount a second internal hard disk by a user"
date: 2009-01-23
forum: Hardware
---

### Post by oliv66 on 2009-01-23
Hi all,

I am under intrepid Ibex (ubuntu 8.10).
My PC has two internal hard disks (sda and sdb).

I have two questions :

1/ I would like under Gnome (Nautilus) to allow users to umount my second hard disk without being a root.

My /etc/fstab is :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=eb456c31-7eb0-4147-b562-af31f0f507e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=2044244b-a759-4588-95ca-7ac59e004d65 /home           ext3    relatime        0       2
# /dev/sda3
UUID=dfdcebe3-2a01-4d2e-b9a9-c901c8802056 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## /dev/sdb1 added by olivier
UUID=a31baf39-6f5c-42b3-95b1-bdb439169828 /media/sdb ext3 relatime  0 2

Concerning the last line, I also tried after the UUID ext3 rw,user,dev,exec, auto, 0 2 with no success.
I also tried :
ext3 rw,user,gid=100,uid=1000,auto,exec 0 2 with no success.

2/ I would like only user called olivier can umount under Gnome (nautilus) the second internak Hard disk ?

Thanks for your help,

Olivier

---

