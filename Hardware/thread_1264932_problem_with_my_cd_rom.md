---
title: "problem with my cd rom"
date: 2009-09-12
forum: Hardware
---

### Post by ivh90 on 2009-09-12
hi 
recently i updated to ubuntu 9.04, but i noticed that after the update my cd rom cant read any cds or dvds except for audio cds , it keeps giving me this error message : 
unable to mount volume 
[mntent]:line 9 in /etc/fstab is bad 
mount : cant find /media/cdrom0 in /etc/fstab or /etc/mtab

please help ! i really need to use my cd rom !

---

### Post by argosreality on 2009-09-12
Can you provide the output of your fstab? run > sudo gedit /etc/fstabfrom the terminal and then copy and paste the contents into here

---

### Post by ivh90 on 2009-09-13
ok here is the output :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5a8face9-ff81-4b6f-b5c7-23c297fc66b4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=13ce8d46-a4da-4b21-9c94-149309459551 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0/mnt/512Mb.swap  none  swap  sw  0 0

---

### Post by ivh90 on 2009-09-14
BUMP ! 
please help !

---

