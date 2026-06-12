---
title: "CD RW trouble"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by ronbrooks on 2007-06-03
Can't record to the CD RW drive.  It keeps telling me that the drive is read only.  When I go into the property's it will say that the drive is owned by root and access to files only.  I have tried to change it but it will not let me. 

I was thinking that there was something wrong with the drive but it will burn CD's when I use K3B on the system.  I have tried to disconnect the drive and connect it again but the same thing happens.  

Here is my /etc/fstab settings

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d721f4f7-a75c-4338-8158-3ed69621bdfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c91225d7-d997-4771-be9c-a19619e48b2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

#Hard drive mount
/dev/hdb1 /media/Drive1 vfat users,noauto,uid=1000,gid=100,umask=007 0 0
/dev/hdb5 /media/Drive2 vfat users,noauto,uid=1000,gid=100,umask=007 0 0
/dev/hdb6 /media/Drive3 vfat users,noauto,uid=1000,gid=100,umask=007 0 0

The /dev/hdc is the CD RW drive.

Any Idea on this

---

