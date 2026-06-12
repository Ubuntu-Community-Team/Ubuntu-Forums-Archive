---
title: "installing new harddrive???"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by wingdom on 2005-07-15
how do u install a second harddrive? i dont expect it to be too very hard, but i could be wrong

---

### Post by mo_x on 2005-07-15
[QUOTE=wingdom]how do u install a second harddrive? i dont expect it to be too very hard, but i could be wrong[/QUOTE]
 It is not that hard. Maybe you can give some more info, that makes it easier to give some advise.
What harddrive do you want to install, is it IDE or SATA?
What devices are already installed, harddrives, DVD and CD drives?
What OS are you using (I assume Ubuntu)?
It mostly comes down to:
- set jumpers right for master/slave settings (for IDE drives)
- put the drive in the case and connect power and IDE/SATA cable
- start computer and partition and format the new drive
- edit /etc/fstab to mount the partitions on the new drive

Gool luck !

Mo X

---

### Post by wingdom on 2005-07-15
it is IDE, i am running ubuntu, i have one cd read/writer installed, one harddrive, one floppy drive.
i have the new harddrive hooked up properly, but when i go to computer all i see is the floppy drive the cd-rw drive, and filesystem(im assuming thats the hdd).  y cant i see the other hdd?
(please explain what to do carefully, because i am still quite new to linux, and dont understand very much)

---

### Post by wingdom on 2005-07-15
bump

---

### Post by RastaMahata on 2005-07-15
run this in the console and paste the output in here:```
sudo fdisk -l
```This is supposed to list all the drives in your pc.

---

### Post by wingdom on 2005-07-15
Disk /dev/hdb: 8037 MB, 8037679104 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         933     7494291   83  Linux
/dev/hdb2             934         977      353430    5  Extended
/dev/hdb5             934         977      353398+  82  Linux swap / Solaris

Disk /dev/hdc: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1867    14996646    7  HPFS/NTFS

---

### Post by RastaMahata on 2005-07-15
[QUOTE=wingdom]Disk /dev/hdb: 8037 MB, 8037679104 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         933     7494291   83  Linux
/dev/hdb2             934         977      353430    5  Extended
/dev/hdb5             934         977      353398+  82  Linux swap / Solaris

Disk /dev/hdc: 15.3 GB, 15367790592 bytes
255 heads, 63 sectors/track, 1868 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1867    14996646    7  HPFS/NTFS[/QUOTE]
 it appears your new HDD is 15.3 gb big, and ntfs formatted, isnt it? Is this the Hard Drive you want to install?

Please type ```
cat /etc/fstab
``` and paste the output here, so I can now what hard drives are mounted on your system.

---

### Post by wingdom on 2005-07-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


yeah, that is the one i wanna add

---

### Post by RastaMahata on 2005-07-15
[QUOTE=wingdom]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


yeah, that is the one i wanna add[/QUOTE]
 then follow these instructions ;):
1. Create a mount point (so you can access your files within a folder). Lets name this folder HardDrive (You can change the name if you want, just edit the code):```
sudo mkdir /media/HardDrive
```
2. Tell fstab (the file which manages where to mount which drives) to mount your drive in the folder you just created. Open up your fstab file:```
sudo gedit /etc/fstab
```Now, edit it, adding to the bottom of it the following line```
/dev/hda1	/media/HardDrive	ntfs	auto,user,exec,umask=0222	0	0
```
3. Remount everything:```
sudo mount -a
```

You should see the hard drive in you "Computer" now ;)
Anyhow, its NTFS formatted, you better ask on how to format and mount the hard drive so you can edit the files in it. Good luck.

---

### Post by wingdom on 2005-07-15
mount: special device /dev/hda1 does not exist


what does this mean?  i see it there, and i know i have 2 reformat it to edit files, but do i have 2 do that to even look at it? there were some files i wanted to get off of there b4 i reformated it

---

### Post by mo_x on 2005-07-16
From what I can see is should be /dev/hdc1 instead of /dev/hda1. Change it in your /etc/fstab and try again.

---

