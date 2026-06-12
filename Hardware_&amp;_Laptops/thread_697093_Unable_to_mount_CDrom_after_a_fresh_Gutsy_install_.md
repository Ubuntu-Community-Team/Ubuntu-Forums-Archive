---
title: "Unable to mount CDrom after a fresh Gutsy install with updates.."
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by vierranet on 2008-02-14
Unable to mount CDrom after a fresh Gutsy install with updates..

Did:
$ cat /etc/fstab

Received:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=51e89799-3f70-42cb-8bc9-ad2ad4758f06 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=45f30dcc-985f-4747-a935-7c7c84549837 none            swap    sw              0       0
/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

--------------------------------------------------------------------------------------------------------
Tried:
$ sudo mount /dev/sdb/media/cdrom0

Received:
mount: can't find /dev/sdb/media/cdrom0 in /etc/fstab or /etc/mtab


Any ideas will be appreciated...

](*,)](*,)

---

