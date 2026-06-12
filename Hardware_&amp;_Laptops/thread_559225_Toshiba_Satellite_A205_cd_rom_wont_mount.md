---
title: "Toshiba Satellite A205 cd rom wont mount"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by mrmuffin009 on 2007-09-24
this god forsaken computer has so many problems, but one at a time

when ever i try to mount the cd-rom it gives me this

Unable to mount the selected volume.
mount: special device /dev/hda does not exist

here is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=296b04a7-8a54-4e0c-9ca3-7aac01fca581 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3b475cba-bec8-40d4-9a20-357bdd71b81f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,angela     0       0

i dont know what to do. im running the newest version of ubuntu. help?

--stu

---

