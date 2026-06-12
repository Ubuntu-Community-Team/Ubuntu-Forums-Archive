---
title: "admin issues"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by sataniceaden saklura on 2005-12-15
hey all im sorry to bother you all but i am having troubles i want to access my ntfs drives that i have to watch and alos make movies onto but ubuntu wont alow me to writee to the drives as it says that i am not the administrator is there a way i can change this??:confused:

---

### Post by frodon on 2005-12-15
You have to know that there is no reliable write support for NTFS under linux so your problem is more your partition file system than admin privileges.
However you shouldn't have any problem with the read support. If you have some , please join your fstab file in the next post, use this command to open the file : ```
sudo gedit /etc/fstab
```

---

### Post by sataniceaden saklura on 2005-12-15
ok i can read them but not all the time not to sure why so that means i cant write to it:(  cause if i go back to my windows it dosnt read the drive any more:( 

this if my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /mnt/disc1  ntfs    rw,defaults,umask=0222   0       0
/dev/hdd1       /mnt/disc2  ntfs    rw,defaults,umask=0222   0       0

---

### Post by sataniceaden saklura on 2005-12-15
just another add on if i unmount the drive will it read in xp again?

---

### Post by frodon on 2005-12-15
It's a little bit strange that the behaviour changed under windows. However i you want to write on your partition under linux you should create a new partition or format it and use FAT32 file system if you want to use your drive with both windows and linux

---

