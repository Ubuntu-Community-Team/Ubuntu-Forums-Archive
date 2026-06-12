---
title: "Laptop Boot Problem"
date: 2011-07-10
forum: Hardware
---

### Post by mb-VAIO-VPCCB on 2011-07-10
Hello, running Ubuntu 11.04 on a new Vaio laptop and have begun to have boot problems. The error message that I can see when trying to boot in recovery mode is as follows:

"udevd-work [77]: '/sbin/modprobe -bv pci:v00001002d00006741sv0000104Dsd00009080bc03sc00i00' unexpected exit with status 0x0009"

I have read some threads [here]("http://ubuntuforums.org/archive/index.php/t-1713332.html") that indicate it might be a problem with switchable graphics but I am having trouble turning them off in the BIOS. Also, previous threads ask for further information from the user having problems so I thought I would post mine here to begin. Here is the information from running "sudo fdisk -lu":


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2588644

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    23975935    11986944   27  Unknown
/dev/sda2   *    23975936    24180735      102400    7  HPFS/NTFS
/dev/sda3        24180736   669569023   322694144    7  HPFS/NTFS
/dev/sda4       669571070   976771071   153600001    f  W95 Ext'd (LBA)
/dev/sda5       669571072   771971071    51200000    7  HPFS/NTFS
/dev/sda6       771973120   968566783    98296832   83  Linux
/dev/sda7       968568832   976771071     4101120   82  Linux swap / Solaris

Disk /dev/dm-0: 4199 MB, 4199546880 bytes
255 heads, 63 sectors/track, 510 cylinders, total 8202240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1847d86a

Disk /dev/dm-0 doesn't contain a valid partition table

__________________________________________________________________________

It does manage to boot 20% of the time. Can anyone offer suggestions on how to prevent this hang up?

I am a beginner with Ubuntu but have so far been able to tweak or fix any issues reading old threads on these forums. Thank you for any assistance!

-m

---

