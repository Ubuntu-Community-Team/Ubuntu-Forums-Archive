---
title: "Unable to mount 217 GB Extended"
date: 2010-09-09
forum: Hardware
---

### Post by vitalife on 2010-09-09
I'm on Ubuntu 9.10, when I want to mount an NTFS partition, the following error occurs
```
Unable to mount 217 Extended, Message did not receive a reply (timeout by message bus).
```
I want to mention that I have another ntfs partition that opens all right. How can I solve this problem?

---

### Post by arrange on 2010-09-09
Is it just a data partition, or does it contain an operating system? Have you shut down Windows properly, or unmounted the partition, when you last used it?

?Can you post the output from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)```
sudo fdisk -l
```

---

### Post by vitalife on 2010-09-10
Yes, it's just a data partition. I use it maybe 2 or 3 dayss ago, eveything was working, but i tried some resizing operation with Hiren's BootCD. Here's the output, and the partitions with problem is /dev/sda5.
```

omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc844d92e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       29039   212282910    f  W95 Ext'd (LBA)
/dev/sda3           29040       29300     2096482+  82  Linux swap / Solaris
/dev/sda4           29301       30352     8450190   83  Linux
/dev/sda5            2612       29039   212282878+   7  HPFS/NTFS

```
I also want to mention, that this errors appears when i'm trying to open /dev/sda5 through nautilus, but when i tried to open with Dolphin, he was openned already, and after that i can open/mount it in nautilus. Why this happens?

---

### Post by arrange on 2010-09-10
OK, so can you now try mounting it manually? Unmount it if it is mounted (e.g. in Dolphin) and then```
sudo mount -t ntfs /dev/sda5 /mnt
tail -20 /var/log/syslog
```Post the output here.

---

### Post by vitalife on 2010-09-10
Here's the output:

```
Sep 10 10:08:31 vitali-ubuntu ntfs-3g[2793]: Version 2009.4.4 external FUSE 27
Sep 10 10:08:31 vitali-ubuntu ntfs-3g[2793]: Mounted /dev/sda5 (Read-Write, label "LocalD", NTFS 3.1)
Sep 10 10:08:31 vitali-ubuntu ntfs-3g[2793]: Cmdline options: rw
Sep 10 10:08:31 vitali-ubuntu ntfs-3g[2793]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096

```
Ups, thanks.

---

### Post by arrange on 2010-09-10
All looks OK, so if you unmount it now```
sudo umount /mnt
```are you then able to mount it via Nautilus?

BTW I would remove the MAC and IP addresses from the above output for security reasons ;)

---

### Post by vitalife on 2010-09-10
Nope, the same error.:sad:

---

### Post by xllxjustinxllx on 2010-09-10
Open up the system tab, go to administration, click disk utility and then when disk utility opens select the partition and click the mount box. It will mount it by uuid to /media. After that try to browse through it with nautilus.

I have to do that process sometimes with my windows partition.

---

### Post by vitalife on 2010-09-10
No sorry, that give the same error Message did not receive a reply (timeout by message bus). 

I tried creating a mounting point, editing *fstab*, mean i put uuid in fstab, then mounting through root, and it works.(If someone need detailed info,just ask)

---

