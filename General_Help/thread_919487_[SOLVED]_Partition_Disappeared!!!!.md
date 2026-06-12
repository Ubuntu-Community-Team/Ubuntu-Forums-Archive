---
title: "[SOLVED] Partition Disappeared!!!!"
date: 2008-09-14
forum: General Help
---

### Post by Julius1988 on 2008-09-14
I formatted a partition(sda6) from ntfs -> ext3 using qparted but the ext3 partition is not mounted up after the boot,"is there any settings i have to modify?"
Here is the fstab file.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=0e731726-79eb-4073-8e49-3b3d6b4883bb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3A280CA2280C5EEF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=68F943EB2C072575 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=44AC73FC55E7496C /media/sda6     ntfs     defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=86FD-A0D8  /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=328B2F130AC22876 /media/sda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=d2973430-107b-468d-9eb2-93267f184bb4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

what should i replace on sda6?

---

### Post by cdtech on 2008-09-14
What do you get with the command:
sudo fdisk -l

You may want to change this line:
# /dev/sda6
UUID=44AC73FC55E7496C /media/sda6 ntfs defaults,umask=007,gid=46 0 1
to:
**/dev/sda6 /media/sda6 ext3 defaults 0 1**
Just run "sudo mount -a" after you edit (no need to reboot)

---

### Post by Julius1988 on 2008-09-14
This is what i get after typing fdisk -l
> 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc164c164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       38913   261369517+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       19122    51199123+  83  Linux
/dev/sda7           19123       25496    51199123+   c  W95 FAT32 (LBA)
/dev/sda8           25497       31870    51199123+   7  HPFS/NTFS
/dev/sda9           31871       37949    48829536   83  Linux
/dev/sda10          37950       38913     7743298+  82  Linux swap / Solaris



after changing the line to what you have specified and running 'sudo mount -a' here is what i get
> 
NTFS signature is missing.
Failed to mount '/dev/sda6': Invalid argument
The device '/dev/sda6' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?


---

### Post by cdtech on 2008-09-14
I'm sorry I just updated my post, please re-read.

---

### Post by Julius1988 on 2008-09-14
thanks man it works like charm :)

---

### Post by cdtech on 2008-09-14
Your welcome........

---

