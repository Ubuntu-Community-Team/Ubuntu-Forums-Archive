---
title: "[SOLVED] partition won't mount"
date: 2008-10-04
forum: Hardware
---

### Post by spotsworth on 2008-10-04
hi,
i recently went from dual boot to single and had trouble mounting the formatted partition.  now its  has reverted back to not being mountable, and i have no idea why.  it was functional when i turned my laptop off...?
any help would be graetly appreciated.
-spots

---

### Post by Patb on 2008-10-04
Spots, could you please open a terminal and post the output of each of the following commands:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```
Armed with that information, someone should be able to help you. 

Cheers, Pat.

---

### Post by spotsworth on 2008-10-04
this is the output. 
 i looked through this last night, but i only have a vague idea of what it means.  i got it to mount last night by editing fstab  it had read more like sda1 and i changed it to: auto defaults 0 2; and then: sudo mount /dev/sda2 /media/sda2.


```
sudo fdisk -l:

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        2938    23559322+  83  Linux
/dev/sda3            2939:        6935    32105902+  83  Linux
/dev/sda4            6936        7113     1429785    5  Extended
/dev/sda5            6936        7113     1429753+  82  Linux swap / Solaris

sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0310" TYPE="vfat" 
/dev/sda2: UUID="d1375ee7-9ef9-46da-8dd2-8f1c3bc6e6f8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="e5a3e7a3-aefe-4aa4-b7a3-610699c4e3e7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3041a4ed-bf51-4f1d-a53b-806a9c7a4306" 


cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e5a3e7a3-aefe-4aa4-b7a3-610699c4e3e7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-0310  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C038D38C38D38038 /media/sda2     auto    defaults  0       2
# /dev/sda5
UUID=3041a4ed-bf51-4f1d-a53b-806a9c7a4306 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



```

i want it to mount automatically when i start my laptop, and preferably not show up on my desktop.  i had to sudo mount again today...?


muchas gracias
spots

---

### Post by Patb on 2008-10-05
Spots, fstab is not mounting your /dev/sda2 because the UUID is incorrectly defined.  The UUID probably changed when that partition was reformatted for the single-boot system.  Edit fstab and change the line following "# /dev/sda2" to this:
```
UUID=d1375ee7-9ef9-46da-8dd2-8f1c3bc6e6f8   /media/sda2     ext3    defaults  0       2
```
Then reboot and see if it is mounted.  Let us know how it goes.  

Cheers, Pat

---

### Post by spotsworth on 2008-10-06
worked like a charm.  
muchas gracias

---

