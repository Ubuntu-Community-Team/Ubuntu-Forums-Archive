---
title: "Partitioning questions"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by kcredden on 2008-12-03
Hey folks: Got a partitioning problem.

I reciently re-installed linux, and tried this time to repartition it. Instead of what I wanted, what I see now, is that SDB1, holds the OS and programs plus my /home directory, and SDB5 isn't being accessed. Also SDC1 now has my /usr directory and a bunch of files in it. I didn't want to move or erase anything until I heard from you.

What my plans are:

a) I want the SDB1 partition to be around 20g, and hold just the OS and Programs. 
b) The SDB5 directory will be my /Home directory, and use the remainder of the harddrive. (around 180g)
c) SDC1 will be my storage drive (around 296g of storage) and it's blank
d) SDC5 can be the swap drive if needed. (This already was generated when I re-installed linux and allowed the installer to automatically repartition SDC)
e) Then finally being able to label each partition like SDB1 as "boot", SDB5 as "work", SDC1 as "Storage" which shows up in a file manager like Dolphin, or Thundar. I feel I can do that but I'm not sure how to do this right.

I ran off a fdisk -l printout, but isn't sure if this will help out. I can't make a copy of the K/System settings/advanced/disk & file systems for you too, which may have more details.

Fdisk info: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89b789b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1323    10626966    7  HPFS/NTFS
/dev/sda2            1324        2668    10803712+   7  HPFS/NTFS
/dev/sda3            2669        9729    56717482+   5  Extended
/dev/sda5            2669        3181     4120641    b  W95 FAT32
/dev/sda6            3182        7031    30925093+   c  W95 FAT32 (LBA)
/dev/sda7            7032        9729    21671653+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e45b14c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433       24321   175823392+   5  Extended
/dev/sdb5            2433       24321   175823361   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a1f10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38536   309540388+  83  Linux
/dev/sdc2           38537       38913     3028252+   5  Extended
/dev/sdc5           38537       38913     3028221   82  Linux swap / Solaris

So any advice you can give, will be appreciated. I can use Gparted if needed.

- Kc

My basic system is:

Kubuntu 8.04.1 w/KDE 3.x
1g memory
Disk 1: PATA (SDA), 80g (for Windows)
Disk 2: SATA (SDB), 200g (Linux boot)
Disk 3: SATA (SDC), 320g (linux)
Intel P4 3ghz 
Asus motherboard
nVidia GeForce 7300 video
Dual monitor.

---

### Post by Pumalite on 2008-12-03
I'd use '/' and /swap only, but if you want to partition your drive; you can use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Here is the documentation:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

