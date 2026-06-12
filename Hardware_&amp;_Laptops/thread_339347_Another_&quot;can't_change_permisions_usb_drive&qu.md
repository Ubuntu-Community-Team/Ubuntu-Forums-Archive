---
title: "Another &quot;can't change permisions usb drive&quot;"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by albesan on 2007-01-15
Hello team,

Here is the issue: external usb drive (30GB), mounts, is FAT format, I can read but I can't write.
When I try to change permissions I get " operation not permited".

Outputs:

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0           0




 sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3648    29302556    b  W95 FAT32




 lsusb
Bus 005 Device 004: ID 0402:5621 ALi Corp. USB 2.0 Storage Device



The error I get when trying to change permisions:

sudo chown -R albesan:albesan /media/sdb1

chown: changing ownership of `/media/sdb1/Unknown Artist/Unknown Album/Unknown Artist/Unknown Album/Mazzy Star - So Tonight That I Might.mp3': Operation not permitted


Any coments apreciated, thanks.


a.

---

### Post by albesan on 2007-01-17
bumping it

---

### Post by calenti on 2007-01-26
I have the same issue with a 40 GB USB external drive. I have it in fstab but it won't mount at boot. I can mount it with -a and read from it but not change permissions, etc.

The link to my post is [http://ubuntuforums.org/showthread.php?p=2065064#post2065064](http://ubuntuforums.org/showthread.php?p=2065064#post2065064) - check it and if I get anything I'll try to get back here.

---

### Post by antar on 2007-01-26
I had a similar problem.

My external 250GB Western Digital hard drive was partitioned into two parts, and when I resized the partitions, Ubuntu decided "antar" was no longer the owner and wouldn't let me change permissions.

I ended up, on a whim, resizing the partitions again, and then waiting until Ubuntu was completely booted up and logged in before plugging in the external. Now it's fine, but I'm still not sure what was up.

---

