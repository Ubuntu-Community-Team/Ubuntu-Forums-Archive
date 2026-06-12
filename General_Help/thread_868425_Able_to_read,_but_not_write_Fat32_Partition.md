---
title: "Able to read, but not write Fat32 Partition"
date: 2008-07-23
forum: General Help
---

### Post by Charlie_On on 2008-07-23
Hello everyone, I have 4 partitions in my 80 gb Hard Drive, one for WinXP(fat32), one for Ubuntu (Ext3), a Swap partition, and a 60 gb partition for games, video, music, etc. (sda6, fat32).
 First, i wanted to mount the fat32 partition, and somehow managed to do it. But now, I can read it and execute its programs but I can't edit anything inside it. 

fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=15deb847-1c42-4918-9ceb-1c7dd3b64d8c /               ext3    relatime,errors=remount-ro 0       1
/dev/sda5       /media/Win32           swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda6     /media/programas     vfat     relatime     0     0


What do I have to do to make sda6 writable?

---

### Post by unutbu on 2008-07-23
Try
```
/dev/sda6 /media/programas vfat relatime,dmask=027,fmask=137 0 0
```

The above was found on both these pages:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab),
 [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) 

where there is a lot of other great information too.

---

### Post by Charlie_On on 2008-07-24
Thanks a lot, it worked, but now I have another problem ](*,)

 I can access and edit the partition, but only in root mode (through gksu nautilus). If I try to download a file, or install an .exe program with wine inside that partition, it crashes and says the program can't access that folder. I thought i could start those programs with the terminal in root mode, is there any other way to do it?

---

### Post by unutbu on 2008-07-24
Try
```
/dev/sda6 /media/programas vfat relatime,uid=1000,gid=1000,dmask=027,fmask=137 0 0
```

This will make you the owner of all files when sda6 mounts. (I'm assuming you are the user with uid=1000. You can check this by typing 'id').

---

### Post by Charlie_On on 2008-07-24
Awesome, problem solved. Thanks a lot.

---

