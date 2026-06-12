---
title: "Mounting problems of Floppy Disk"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by ubuntu504 on 2005-05-10
Hi :) 

I have a problem with Kubuntu 5.04 LIVE CD after having bootet the system into the KDE Desktop Environment.

I can't access the Floppy Disk. I have tried as root to mount the Floppy Disk as follows:

$mount -t ext2 /dev/fd0 /mnt

I wanted to have /mnt/floppy but couldn't make it work, and the above doesn't work either. Does someone else have experienced this problem or a similar problem?

Please reply soon!!!

Kind regards

Preben Lauritzen Duus
Duusix Software :?

---

### Post by Alexander Kirillov on 2005-05-10
[QUOTE=ubuntu504]Hi :) 

I have a problem with Kubuntu 5.04 LIVE CD after having bootet the system into the KDE Desktop Environment.

I can't access the Floppy Disk. I have tried as root to mount the Floppy Disk as follows:

$mount -t ext2 /dev/fd0 /mnt

I wanted to have /mnt/floppy but couldn't make it work, and the above doesn't work either. Does someone else have experienced this problem or a similar problem?

Please reply soon!!!

Kind regards

Preben Lauritzen Duus
Duusix Software :?[/QUOTE]
 almost all floppy disks around have vfat filesystem, not ext2.

---

