---
title: "3 partition do it all flash disk"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by bewareofthesandman on 2009-10-12
Hi,

I'm trying to make a 16g flash disk that can boot ubuntu, have a shared partition visible to windows and a bootable partition for bootable cd/dvds (ex: windows 7 installation, ultimate boot cd etc).

So far this is what I have:
Partition    file system  mountpoint
/dev/sdc1    fat32        /media/data     -4g shared partition
/dev/sdc2    fat32        /media/DVD      -4g bootable cd/dvd
/dev/sdc3    ext3         /media/disk-1   -8g Ubuntu boot

sdc1 works like it should in both ubuntu and windows
sdc3 boots without a problem
but i can't have sdc2 load anything from grub

thoughts?
thank you

---

### Post by Mighty_Joe on 2009-10-12
> **bewareofthesandman said:**
> 
but i can't have sdc2 load anything from grub


What are you trying to do?  Boot an ISO file from that partition?

---

### Post by bewareofthesandman on 2009-10-12
Yes, but not the compressed file; it's the copied files from an ISO mount.
I'm doing a boot installation disk, it would work if it were on the sole partition going straight to the installation but I'd like to put it in the USB key I carry around the most, which is partitioned.

---

### Post by Mighty_Joe on 2009-10-13
Search the forum for "isolinux".  I've seen some people in here trying to do the same thing.  I've tried booting compressed ISOs with Grub (actually Grub4Dos) and gotten nothing but frustration.  The isolinux posts seem to get better results.

---

### Post by bewareofthesandman on 2009-10-13
alright thanks!

---

