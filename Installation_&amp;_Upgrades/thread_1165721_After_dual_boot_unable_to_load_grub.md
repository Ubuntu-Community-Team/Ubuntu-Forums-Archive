---
title: "After dual boot unable to load grub"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by devosion on 2009-05-20
I have used the following two guides in order to dual-boot Ubuntu 9.04 and Windows 7:

[http://ubuntuforums.org/showthread.php?t=1035999]("http://ubuntuforums.org/showthread.php?t=1035999")

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Currently im stuck with Windows 7 not recognizing grub and it booting up without recognizing any other installed OS'. I have reinstalled grub on via both guides, and I have ensured the menu.lst file is properly setup to accompany both drives (sda for Windows and sdb for Linux). I am currently attempting to get Windows 7 to recognize grub via the second how to, but it seems this solution only seems to allow the Windows 7 bootloader to recognize grub and not overwrite it. I'd like to use grub as my bootloader and not the Windows 7 bootloader. If it helps I have grub has recognized its installation on my linux partition as (hd0,1) and the windows partition is on (hd0,0).

---

### Post by damis648 on 2009-05-20
The most common error here is likely that when running
```
grub> setup (hdx)
```
you may have accidentally used
```
grub> setup (hdx,y)
```
Make sure to install to the drive, not the partition.

---

### Post by devosion on 2009-05-20
I went ahead and inputted all the commands for setuping grub and overwriting the bootloader with that in mind, then restarted. Windows 7 again was the only thing that loaded. Any other ideas?

---

### Post by devosion on 2009-05-20
Here is a copy of my fdisk -l if it helps:

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78121984    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f4f8f4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         851     6835626   83  Linux
/dev/sdb2             852       19335   148472730   83  Linux
/dev/sdb3           19336       19457      979965   82  Linux swap / Solaris


---

### Post by devosion on 2009-05-21
This was taking a longer amount of time than I expected to resolve so I just went ahead and reinstalled ubuntu on root, and that fixed the problem.

---

