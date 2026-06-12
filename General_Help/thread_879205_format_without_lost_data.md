---
title: "format without lost data"
date: 2008-08-03
forum: General Help
---

### Post by dersu on 2008-08-03
Hi,
I think I played a lot with my linux and now gnome doesn't work.
I decide to re install hardy. But I have data on my disc.
I have a external disc which was normally mounted at the beginning with gnome, but with fluxbox it isn't mounted. I dont know if it is related with my gnome problem.
Znyway I want to mount my external disc (usb) to backup my datas.
Help please.

---

### Post by tamoneya on 2008-08-03
open up a terminal and type in this:```
sudo fdisk -l
```
Post the results here and then I can tell you how to mount the disc

---

### Post by dersu on 2008-08-03
Ok, I have this.
But still I can't go on my disc. :(

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86b7a0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9544    76662148+  83  Linux
/dev/sda2            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   c  W95 FAT32 (LBA)
memet@Hal-2008:~$ sudo mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab

---

### Post by tamoneya on 2008-08-03
that wasnt supposed to fix the problem.  It just tells me how to fix the problem.

The following commands will make the disk accessible at /media/external.

```
sudo mkdir /media/external
sudo mount -t vfat /dev/sdb1 /media/external
```

---

### Post by dersu on 2008-08-03
Thank u.

---

