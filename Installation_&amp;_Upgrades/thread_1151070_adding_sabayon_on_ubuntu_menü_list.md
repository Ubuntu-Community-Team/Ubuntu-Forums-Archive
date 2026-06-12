---
title: "adding sabayon on ubuntu menü list"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by hatalar205 on 2009-05-06
I have installed my computer Sabayon 4.1 gnome without grub. Now I am trying to add an entry for Sabayon to ubuntu menü list. But unfortunatelly I couldn't do it. So I couldn't boot Sabayon.
Vista + Ubuntu + Sabayon is on my machine.

**fdisk -l output:**

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x885f41c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       19859   157975552    7  HPFS/NTFS
/dev/sda3           19859       32540   101858300    7  HPFS/NTFS
/dev/sda4           32540       38914    51198976    f  W95 Ext'd (LBA)
/dev/sda5           32540       36007    27848677+  83  Linux
/dev/sda6           36008       38913    23342413+  83  Linux

**and blkid output:**
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E8DC544FDC5419E0" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="12A25652A2563B05" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="947E58B17E588E3C" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="16d57299-851d-409d-8b08-9fb66f8c1847" TYPE="ext3" 
/dev/sda6: UUID="fa2537d2-e60b-4702-b434-cfe1a95f5537" SEC_TYPE="ext2" TYPE="ext3" 

Vista is on sda 2
Ubuntu is on sda5
Sabayon is on sda 6

Thanks in advance.

---

### Post by EXCiD3 on 2009-05-06
```
title Sabayon
root (hdX,Y)
chainloader +1 
```
Fill in the X and Y for the drive number and partition, remeber both start at 0, not 1.
 
Check out this thread if that doesn't work: [http://ubuntuforums.org/showthread.php?t=329640](http://ubuntuforums.org/showthread.php?t=329640)

---

### Post by hatalar205 on 2009-05-06
It didn't work. So I reinstalled ubuntu. Everything is Ok.
Thanks.

---

