---
title: "Sil3512 Raid Contr. - Raid 0 - U11.10 - LiveCD works, installed version doesn't"
date: 2012-02-22
forum: Hardware
---

### Post by steve696 on 2012-02-22
Sil3512 Raid Controller
Raid 0
Ubuntu 11.10
Kernel version 3.0.0-12-generic

I've got two hard disks with 2TB each which are paired in a hardware raid array. When I boot from an usb stick I can use the 4TB. But after the installation there was no 4TB volume, there were only two 2TB disks without a volume. Every time I boot from the live usb disk, which was also my installation medium, I can access the raid 0 volume.

Plan b would be to use software raid, but I wanted to ask the community first.
Could you please give me some hints what I could do to make the raid volume available?

There must be a possibility to find out the difference between these two configurations with the exact same hardware and with the  same operating system.

[B]
_additional data from the live cd system:_[/B]

**lspci | grep sil **
  09:02.0 Network controller: Intersil Corporation ISL3874 [Prism 2.5]/ISL3872 [Prism 3] (rev 01) 
 
   **fdisk -l**
 ...
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes 
 255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x00000000 
 Disk /dev/sdd doesn't contain a valid partition table 
  
 Disk /dev/sde: 2000.4 GB, 2000398934016 bytes 
 255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 4096 bytes 
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
 Disk identifier: 0x00000000 
 Disk /dev/sde doesn't contain a valid partition table 
 
[I]There is no difference between the entries above and the result of the installed version.
The next paragraph can only be found on the live cd:
[/I]
 Disk /dev/mapper/sil_biacdddccaaj: 4000.8 GB, 4000795754496 bytes 
 255 heads, 63 sectors/track, 486402 cylinders, total 7814054208 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 4096 bytes 
 I/O size (minimum/optimal): 16384 bytes / 32768 bytes 
 Disk identifier: 0x00000000 
 Disk /dev/mapper/sil_biacdddccaaj doesn't contain a valid partition table
 
 …(other disks)...
 
 **sudo dmsetup info **
 Name:              sil_biacdddccaaj 
 State:             ACTIVE 
 Read Ahead:        256 
 Tables present:    LIVE 
 Open count:        1 
 Event number:      0 
 Major, minor:      253, 0 
 Number of targets: 1 
 UUID: DMRAID-sil_biacdddccaaj

---

### Post by steve696 on 2012-02-26
Unfortunatley there were no responses to this topic so far. I deactivated the hardware raid and used software raid. I've got a workaround solution, but I'm still interested in the cause of this effect.

---

