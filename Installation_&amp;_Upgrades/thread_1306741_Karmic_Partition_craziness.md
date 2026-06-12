---
title: "Karmic Partition craziness"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Abaddon on 2009-10-30
Hi All,

I tried a Dist-upgrade from my Jaunty install which resulted in some fstab badness and me being unable to boot.  No major drama, I had been meaning to do a clean install anyway.  The only problem is the installer doesn't want to play the game with my partitions.

I've got 2x 500Gb HDDs, non-RAID.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083b37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    7  HPFS/NTFS  ## WinXP
/dev/sda2            6080       60801   439554465    5  Extended  
/dev/sda5            6080        9118    24410736   83  Linux  ## Ubuntu
/dev/sda6            9119       12157    24410736   83  Linux  ## Spare - install Kubuntu on it when I'm bored
/dev/sda7           12158       24315    97659103+  83  Linux  ## Home
/dev/sda8           24316       60801   293073763+  83  Linux  ## Data

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00087b3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           59587       60801     9759487+  82  Linux swap / Solaris
/dev/sdb2               1       23112   185647108+   7  HPFS/NTFS  ## WinXp Games
/dev/sdb3           23113       59586   292977405    b  W95 FAT32  ## Shared data partition

```

So, I was going to reformat /dev/sda5 and use /dev/sda6 as my new /home/ so I could copy over all the stuff I want to keep from my old home partition manually. No big deal.

However, the installer doesn't want to let me do that... the only drive I can install to is a RAID of both my drives - which will require borking all my data. - see screenies.

How can I separate my drives and install just to the partition I want??

TIA!

---

