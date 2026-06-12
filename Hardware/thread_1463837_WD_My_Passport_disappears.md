---
title: "WD My Passport disappears"
date: 2010-04-27
forum: Hardware
---

### Post by TechGriffin on 2010-04-27
I've seen similar posts, but nothing that really seems to fix this issue. I've recently bought a Western Digital "My Passport". I'm primarily a Windows user, and the device works fine with Windows. The device works fine with Ubuntu as long as it is plugged in when I boot and is available until removed. If I remove the device and plug it back in, Ubuntu does not completely recognize the device.

Let me explain what I mean by, "completely recognize." In Windows and Ubuntu, the hard drive shows up as two devices, a CD, and a storage drive when working properly. The only time I will see both devices in Ubuntu is if I boot Ubuntu with the device already plugged in and don't remove it. If I remove the device and plug it back in while running Ubuntu, only the CD device shows and not the storage device.

I'm by no means an expert with computers, and especially Ubuntu. I'm probably missing something ridiculously simple here. If it helps, the "CD device" that I refer to contains the autorun functions for the hard drive. Thanks!

---

### Post by TechGriffin on 2010-04-27
Also, sudo fdisk -l returns this:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *        1316       16044   118303720    7  HPFS/NTFS
/dev/sda3           16045       19457    27414922+  83  Linux
/dev/sda4              11         259     2000092+   5  Extended
/dev/sda5              11         259     2000061   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052f35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121516   976074752    7  HPFS/NTFS

---

### Post by devicerandom on 2010-04-27
Odd. I have two WD Passport myself and they work without a hitch. But they must be older models, since they do not have a separate partition like yours for the autorun utilities.

I would personally just reformat the drive (you don't really need the autorun stuff) and see if it works.

---

### Post by Caletara on 2010-04-28
I have a passport and it works fine too. If you're going to be using it primarily for linux/ubuntu I would reformat it to ext3 or ext4. Otherwise, make sure it's plugged in correctly before you boot up so the OS will recognize and mount it safely.

---

