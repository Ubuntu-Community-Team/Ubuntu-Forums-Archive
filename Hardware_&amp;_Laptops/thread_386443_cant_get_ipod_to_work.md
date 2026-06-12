---
title: "cant get ipod to work"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by sarracenia88 on 2007-03-17
i am trying to get my younger brother's ipod to work in ubuntu but each time i try to mount it, it gives a message saying, 

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted. 

mount: wrong fs type, bad option, bad superblock on /dev/sdb,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

We have music on the ipod that was put on there by a computer using itunes in winxp.


i would like to mount it in ubuntu.

oh here is my dmesg tail output

raptor22@raptor22-edgy:~$ dmesg | tail
[23592.242158] FAT: count of clusters too big (246935)
[23592.242166] VFS: Can't find a valid FAT filesystem on dev sdb.
[23877.668889] FAT: count of clusters too big (246935)
[23877.668896] VFS: Can't find a valid FAT filesystem on dev sdb.
[23892.924147] FAT: count of clusters too big (246935)
[23892.924154] VFS: Can't find a valid FAT filesystem on dev sdb.
[23898.257409] FAT: count of clusters too big (246935)
[23898.257415] VFS: Can't find a valid FAT filesystem on dev sdb.
[23997.781593] FAT: count of clusters too big (246935)
[23997.781599] VFS: Can't find a valid FAT filesystem on dev sdb.
raptor22@raptor22-edgy:~$

---

