---
title: "dual boot setup trouble"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by ggundrum on 2009-02-24
I recently built a new pc and decided to give ubuntu a shot, i really enjoy it except for the lack of gaming compatibility. To fix this i attempted to setup my system for a dual boot of ubuntu and xp. I created a partition space for windows using the partition editor, but everytime i boot windows from a disk it freezes at "setup is starting windows" screen. I know that the xp disks are valid, but for some reason i get hung up at this point everytime. Any help would be much appreciated!

My Setup:
ASUS P5N-D Mobo, Intel Duo Quad 2.66GHz
Corsair 4Gb DDR2, XFX GeForce 9800 Gt
Hitachi 1Tb SATA HD

---

### Post by taurus on 2009-02-24
Did you format that new partition to ntfs?  From Ubuntu, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ggundrum on 2009-02-24
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076299

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      119710   961570543+  83  Linux
/dev/sda2          119711      120658     7614810    5  Extended
/dev/sda5          120657      120658       16065   82  Linux swap / Solaris
/dev/sda6          119711      120655     7590649+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa6daa6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20022   160826683+   7  HPFS/NTFS

---

### Post by taurus on 2009-02-24
Are you trying to install windows /dev/sdb1?

---

### Post by ggundrum on 2009-02-24
it doesnt matter thats another harddrive i have in its smaller but i am not able to get far enough in the windows setup to choose where to install the xp. my partitions could be completely wrong, thats kinda what i need help with, i am very new to all this.

---

### Post by taurus on 2009-02-24
So you have two harddrives on your machine, first one with 1TB and the second one with 165GB?

Right now, you have Ubuntu on the first partition of the first harddrive, /dev/sda1, while somehow you have two swap partitions (both logical partitions) on the first harddrive, /dev/sda5 & /dev/sda6.  Then, you have windows (or whatever it is on the second harddrive since it's formatted to ntfs filesystem), /dev/sdb1.

---

### Post by ggundrum on 2009-02-24
yeah i took the 165 out of my old computer it was running xp, but now its just connected to retrieve all my old data, i could disconnect it if need be. I have tried booting windows with out the 165 connected and i get same error.

---

### Post by taurus on 2009-02-24
Right now, you don't have any space or an empty partition on your first harddrive, /dev/sda, to install windows on.  Therefore, you probably should boot your machine with Ubuntu LiveCD.  Then, run gparted (System -> Administration -> Partition Editor) and resize /dev/sda1, creating some empty space at the front of the harddrive.  Create a partition out of that unallocated space and format it to ntfs filesystem.  Now see if you can install windows on that partition.

---

### Post by ggundrum on 2009-02-24
i tried that and the windows setup still froze at "setup is starting windows"
here is my new fdisk

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076299

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      119710   961570543+  83  Linux
/dev/sda2          119711      120658     7614810    5  Extended
/dev/sda3          120659      121601     7574647+   7  HPFS/NTFS
/dev/sda5          120657      120658       16065   82  Linux swap / Solaris
/dev/sda6          119711      120655     7590649+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa6daa6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       20022   160826683+   7  HPFS/NTFS

---

### Post by taurus on 2009-02-24
And you think the windows disc is good!

---

### Post by ggundrum on 2009-02-24
yeah my buddy used these disks to put xp on his comp, the same freeze occured when attempting to put vista on too. thats why i think it might have something to do with the ubuntu

---

