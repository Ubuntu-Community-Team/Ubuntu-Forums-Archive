---
title: "Problems with privlages on secondary drives"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by ThorPrime on 2005-10-18
I have been having serious issues trying to get write permissions for non-root users on a couple secondary drives. One is a 160GB Fat drive in the case and one is an HFSplus firewire drive.

My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/sharedrive vfat  group,auto,fmask=0111,dmask=0000
#/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Both drives read fine for all users and I can write to the fat drive with root. 

Any way to get both drive r/w for all users?

---

### Post by aysiu on 2005-10-18
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by ThorPrime on 2005-10-19
Ok, I got the FAT drive to work fine now.

But is there any way to get the HFS drive to mount in a r/w mode?

---

