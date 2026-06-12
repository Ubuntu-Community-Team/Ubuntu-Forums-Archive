---
title: "sata drive doesnt mount at boot"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by Brando569 on 2005-09-28
my maxtor diamond max +9 doesnt mount at boot even thought it has the exact same options as other drives (which are IDE), it'll mount just fine when i type mount /dev/sda1, any reson why this is happening? heres my fstab:

/dev/sda1	/media/stuff	ntfs		nls=utf8,umask=0222,auto	0     0

---

### Post by pompomtom on 2005-10-04
I have a similar problem, but with a slight (and very odd, imho) difference. My SATA drive is split into three partitions - /, swap, and one other (to be mounted at /media/sda6). The / and swap work fine, but the other one doesn't mount at boot. As with the OP, it mounts fine if I mount it manually.
Anyone got any clues?
(FYI: fstab is as follows:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/sda1       /media/boot     ext3 defaults 0 0
/dev/sda6       /media/sda6     ext3 defaults 0 0
/dev/hdb1       /media/d2       ext2 defaults 0 0
/dev/hda1       /media/boot     ext3 defaults 0 0
/dev/hda5       /media/d3       ext3 defaults 0 0
/dev/hda6       /media/hda6     ext3 defaults 0 0
```

---

### Post by Brando569 on 2005-10-04
mine is only one partition cuz i used it for windows storage (mainly downloads/unattended installation stuff etc...) now im deciding the fate of it.... when it tries to get mounted at boot up i get this: "special device /dev/sda doesnt exist"  but yet when i get into ubuntu, go to konsole and type sudo mount /dev/sda1 it works perfectly. its really annoying cuz i have all of my music on there, each time i want to listen to it i have to mount it (that is if i rebooted linux) only work around i can think of is to write a shell script and have it run when you login, but i dunno how to add things to the startup of your session yet (which i would like to know how to do)

---

