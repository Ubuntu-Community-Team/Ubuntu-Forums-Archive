---
title: "RAID setup problem"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by gate on 2009-02-01
Hi all, I have been trying to install a server with a software RAID but when I boot the system, I get "file not found" (Error 15) from GRUB.

setup:
3 80GB HDDs
1 1 TB HDD (not in use yet, but plugged in)

sda1, 255 MB ext3, /boot
sda2, 79.75 GB RAID, md0
sdb1, 255 MB FAT32, /mnt/sdb1
sdb2, 79.75 GB RAID, md0
sdd1, 255 MB FAT32, /mnt/sdd1
sdd2, 79.75 GB RAID, md0

md0 contains an LVM

LVM volumes: 
3 GB swap
remaining is EXT3 root

Is this something fundamentally wrong with the setup or could it be something more innocuous like GRUB is trying to load /boot from the wrong drive?

---

### Post by gate on 2009-02-01
Reinstalling grub results in a grub console, any suggestions?

---

### Post by gate on 2009-02-05
HAH!

 The problem was the device.map, it doesn't seem that the ubuntu installer created it properly. All I had to do to fix the problem was add 2 lines to it (both may not have been neccecary)

the lines were

```

(hd4) /dev/<LVMNAME>/<LVMVOLUME1>
(hd5) /dev/<LVMNAME>/<LVMVOLUME2>

```

Where LVMNAME was the name of the volume group and the LVMVOLUME# was the name of each of my 2 volumes. After changing that, a grub-install /dev/sda from the rescue install fixed it.

Will file a bug and post the number here.

---

