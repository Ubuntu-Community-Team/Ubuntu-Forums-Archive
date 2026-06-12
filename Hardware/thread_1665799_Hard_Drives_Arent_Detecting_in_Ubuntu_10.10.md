---
title: "Hard Drives Arent Detecting in Ubuntu 10.10"
date: 2011-01-12
forum: Hardware
---

### Post by KingT22 on 2011-01-12
I've installed Ubuntu 10.10 as a dual boot system and its not detecting all of my hard disks. I've verified the drives are healthy and powered since I can see them all on the Windows XP operating system and they are showing up in the BIOS. 

I've pasted a copy of the **fdisk -l** below. There should be 2 more hard drives on this list 

Thanx in advance



Disk /dev/sda: 1000.2 GB, 1000204886016 bytes                      [SIZE=2][COLOR=Red] Ubuntu[/COLOR][/SIZE] [SIZE=2][COLOR=Red]Dual Boot Partition[/COLOR][/SIZE]
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002373c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13091   105146104+   7  HPFS/NTFS
/dev/sda2           13091      121602   871615489    5  Extended
/dev/sda5           13091      119368   853677056   83  Linux
/dev/sda6          119369      121602    17937408   82  Linux swap / Solaris



Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5fe7226

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001    7  HPFS/NTFS



Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f4b22ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS



Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2254220

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001    7  HPFS/NTFS



Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4df0a12

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001    7  HPFS/NTFS      [COLOR=Red]**Windows XP partition**[/COLOR]

---

### Post by cascade9 on 2011-01-13
What motherboard, and are the 'missing' drives SATA or IDE?

---

