---
title: "Having trouble getting SATA drive to mount"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by jackmacokc on 2005-01-17
Here's my fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda1       /mnt/windows_c  ntfs    umask=0222      0       0
/dev/sda2       /mnt/windows_d  vfat    umask=000       0       0
none            /proc/bus/usb   usbfs   defaults        0       0
``` 

for some reason when i boot, i get the error "mount: special device /dev/sda1 does not exist" and the same for sda2.

any ideas on why this is happening? when i get into x, i can sudo mount -a and they all mount just fine.

here's /proc/partitions
```
major minor  #blocks  name

   3     0  117220824 hda
   3     1  116720824 hda1
   3     2          1 hda2
   3     5     499936 hda5
 254     0  116720824 dm-0
 254     1     499936 dm-1
   8     0  195360984 sda
   8     1   40957686 sda1
   8     2  154400715 sda2
```

---

### Post by Tubuntu on 2005-02-12
I had same kind problem and only solution what i found was to add "mount -a" command in bootmisc.sh file. 

#sudo gedit /etc/init.d/bootmisc.sh

Add this to end of the file and save (but before line ": exit 0") 
mount -a 

Boot computer and it should work

---

