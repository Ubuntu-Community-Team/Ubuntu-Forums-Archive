---
title: "mounting networkfolders on boot up problem"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by Swiss2K on 2006-01-08
**This is my Fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /media/Extended  vfat    iocharset=utf8,umask=000   0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.1.33/Maxtor300GB        /media/Server300GB  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.33/Maxtor120GB        /media/Server120GB  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
[B]
When i do 'sudo mount -a' I get this error message:[/B]

mount: wrong fs type, bad option, bad superblock on //192.168.1.33/Maxtor120GB,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[B]
obviously I checked all the names and also my login and pass. It seems to be set ok. What is going wrong[/B]?

---

### Post by Swiss2K on 2006-01-09
I've still no luck getting these networkfolders mounted. 

Please help, Anybody??

---

### Post by GoldBuggie on 2006-01-09
From the error msg I would assume you haven't installed smbfs.
```
sudo apt-get install smbfs
```

---

### Post by Swiss2K on 2006-01-09
[QUOTE=GoldBuggie]From the error msg I would assume you haven't installed smbfs.
```
sudo apt-get install smbfs
```[/QUOTE]

This was the problem and installing smbfs was the solution!:p 

Thanks GoldBuggie

---

