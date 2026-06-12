---
title: "cdrom1 won't mount for burning"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by glidetothehoop on 2005-07-12
I'm having trouble trying to burn a cd.  I've tried nautilus and gnomebaker and both programs warn me that CDROM1 is not mounted.

When I try and mount manually here is what I get...

root@glide:/mnt # mount /media/cdrom1
mount: block device /dev/hdd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Here is my FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1	/mnt/hdb1       ext3    defaults        0       2	
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Any help you have would be greatly appreciated.

Glide.

---

