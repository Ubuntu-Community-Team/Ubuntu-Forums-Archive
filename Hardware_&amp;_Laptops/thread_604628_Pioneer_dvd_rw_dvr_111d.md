---
title: "Pioneer_dvd_rw_dvr_111d"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by Roque2 on 2007-11-06
I have 2 dvdr's the one in the title is my + and - r writer and my other is just a slave - r writer. Now my problem is that my master pioneer will read disks and boot disks but it will not write while my other drive which is the slave will do all the above and write. I have look at the harware info page in gutsy and they look the same other than the hdd and the hdc that loads them. any clue what could be going on.


this is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a3082da6-6a7e-4742-9893-c9befb626f6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5b8e2a5c-f2b0-4cca-833a-b7788afa2f16 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Roque2 on 2007-11-09
Guess no one knows.

---

