---
title: "Hard disk space problem !!"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by h3ndric on 2004-12-01
Anybody out there please help me to solve this prob. Is there anyway i can fix my problem ? I have one HDD which is connected thru pcmcia and it has 112 GB size in FAT32, but when i browse from windows, i still have 4 GB, but in linux if i use df -h i see all 100% used up (112 GB), but if i use du -sh in that drive i see 108 but still i cannot copy anything into it, as it return error message that my drive already full.

The capture of the shell command is like this :

h3ndric@progenic:/mnt/D $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.3G  2.2G  1.9G  53% /
tmpfs                 126M     0  126M   0% /dev/shm
/dev/hda1              24G   22G  2.2G  91% /mnt/C
/dev/sda5             112G  112G   69M 100% /mnt/D
h3ndric@progenic:/mnt/D $ du -sh
108G    .

Thx for the help

---

### Post by az on 2004-12-01
/dev/sda5 112G 112G 69M 100% /mnt/D

How is it mounted?

Show your /etc/fstab.

---

### Post by h3ndric on 2004-12-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/C  vfat    defaults,auto,uid=1000,gid=1000 0       0
/dev/sda5       /mnt/D  vfat    defaults,auto,uid=1000,gid=1000 0       0

This is my fstab file and actually i have to mount my /mnt/D manually because when first starting the linux, i run automount first then the hotplug, as my hdd is connected thru pcmcia which is starting later after the automount, so I have to mount it manually, and beside that i have samba that started automatically to share files in my /mnt/D directory. Hopefully this information can helped.

---

