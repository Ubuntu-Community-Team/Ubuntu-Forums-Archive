---
title: "Partition Help"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by expendable1 on 2009-10-13
I have an asus netbook (1005HA) with xp preloaded.  I would like to dual boot with ubuntu.  When i click "install" I get an error message "The ext4 file system creation in partition #2 of SCSI1 (0,0,0) (sda) failed"


My setup preference would be 10gigs for ubuntu, 1028mb for the swap, and the rest for the /home folder.  

I've added some screenshots of what my partition looks like. Any help would be appreciated

[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by expendable1 on 2009-10-13
a copy of my terminal:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0bf6260

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9407    75561696    7  HPFS/NTFS
/dev/sda3           18814       19451     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda4            9408       18813    75553695    5  Extended
/dev/sda5           18689       18813     1003968   82  Linux swap / Solaris
/dev/sda6            9408       16256    55014529+  83  Linux
/dev/sda7           16257       18688    19535008+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026b56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     7839688+   b  W95 FAT32

---

### Post by presence1960 on 2009-10-13
> **expendable1 said:**
> a copy of my terminal:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0bf6260

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9407    75561696    7  HPFS/NTFS
/dev/sda3           18814       19451     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda4            9408       18813    75553695    5  Extended
/dev/sda5           18689       18813     1003968   82  Linux swap / Solaris
/dev/sda6            9408       16256    55014529+  83  Linux
/dev/sda7           16257       18688    19535008+  83  Linux

Partition table entries are not in disk order



Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026b56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     7839688+   b  W95 FAT32

Your screenshots do not even come close to what your partition table says. Do this please:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mikewhatever on 2009-10-13
Are you trying to resize sda2, the second partition? If that's the case, you need to delete the extended partition first and then recreate it. Make all of Ubuntu partitions logical because you won't be able to create more then four primary partitions.

---

