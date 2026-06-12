---
title: "Mounting UDF DVD's"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by ibrahim.salah on 2008-02-14
[SIZE="4"]Hey everyone
I got a problem mounting an UFD DVD 
here is my fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=625a48f0-eaa0-4e18-88e2-5a5d25b07062 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B4A80833A807F2A2 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=473A-EAF9  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=78afc2fe-34f6-43b8-88e4-d7e2373d4426 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
i tried changing udf,iso9660 into auto but it didn't work
i installed udftools but i don't know how to use it...anyone can help please?
[/SIZE]

---

### Post by mrsteveman1 on 2008-02-14
You shouldn't need to put the iso9660 filesystem in there as well.


When a dvd has multiple filesystems its because the same files are described by each of them, though they are all in the same place. Basically all the files on the disc should be accessible from the UDF file table, so the iso9660 table isnt needed.

---

### Post by stevejesus on 2008-02-14
I am hoping you can make the text in your post just a little bigger...  I can't read it. LOL

---

