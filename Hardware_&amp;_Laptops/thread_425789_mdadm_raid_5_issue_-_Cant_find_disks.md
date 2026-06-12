---
title: "mdadm raid 5 issue - Cant find disks"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by Gruelius on 2007-04-27
Hi everyone,
Ive recently got a problem, for some reason mdadm cant assemble my raid array anymore. The individual disks are there with the same names but it only wants to find three.

This is my mdadm.conf file
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=3eeec131:2639150d:8a2dcafc:57dfe331

This is an example of the error
root@tuxserver:~# mdadm --assemble --scan --force /dev/md0
mdadm: /dev/md0 assembled from 3 drives - not enough to start the array.

Im stumped.. im pretty noob as well :P
Thanks in advance
J

---

### Post by Gruelius on 2007-04-28
root@tuxserver:~# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=5 /dev/hdb /dev/hde /dev/hdf /dev/hdg /dev/hdh
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/hdb appears to contain an ext2fs file system
    size=781443584K  mtime=Sat Apr 28 02:36:34 2007
mdadm: /dev/hdb appears to be part of a raid array:
    level=raid5 devices=5 ctime=Fri Apr 27 16:11:12 2007
mdadm: /dev/hde appears to be part of a raid array:
    level=raid5 devices=5 ctime=Fri Apr 27 16:11:12 2007
mdadm: /dev/hdf appears to be part of a raid array:
    level=raid5 devices=5 ctime=Fri Apr 27 16:11:12 2007
mdadm: /dev/hdg appears to be part of a raid array:
    level=raid5 devices=5 ctime=Fri Apr 27 16:11:12 2007
mdadm: /dev/hdh appears to contain an ext2fs file system
    size=1049879040K  mtime=Sat Apr 28 06:22:04 2007
mdadm: /dev/hdh appears to be part of a raid array:
    level=raid5 devices=5 ctime=Fri Apr 27 16:11:12 2007
mdadm: size set to 195360896K
Continue creating array? 


Does this mean that two of my disks have been edited and are now bung? What could have caused this?

---

