---
title: "Confusion about 3tb drive sector size"
date: 2014-09-22
forum: Hardware
---

### Post by skir0987 on 2014-09-22
Hi,

I am trying to create an ubuntu server with two 3tb drives (one Seagate, one Toshiba). These drives were originally in their external enclosures. I believe one is formatted as HFS+ and the other as NTFS. The drives were originally discovered as 2TB and 3TB, but they are now both discovered as 3TB after updating the bios (Gigabyte DS4 Mobo) and enabling AHCI. However, now no partitions are being recognized. gdisk says that each drive has a sector size of 512 bytes. 

I was reading about emulated 512 byte sector sizes (512e) vs. the drives actually having a 4096 byte sector size, but am now very confused. Does anyone know if the drives are supposed to have 512 byte sector sizes or if they are supposed to be 4096? I ran testdisk on each drive and it seemed to discover what seemed to be the correct partition table (on the HFS+ one, there was an EFI partition then a very large HFS partition), but could not list files due to some error about HFS browsing not being compiled into testdisk. So, now, I'm stuck. Does anyone have any suggestions? I'd like to preserve the data on the drives if possible, and I do not have a big enough drive to back them up as there is approximately 4TB of data across both drives.

Thanks,
Shep


EDIT: found this: [http://www.tomshardware.com/answers/id-1859483/external-hdd-internal-showing-computer.html](http://www.tomshardware.com/answers/id-1859483/external-hdd-internal-showing-computer.html)

> [COLOR=#070F14][FONT=Verdana]Seagate's 3TB external are configured with 4KB sector sizes and MBR partitions. When you remove the drive from its enclosure and attach it directly to a SATA port, you expose the drive's native 512e LBAs. Your PC[/FONT][/COLOR][COLOR=#070F14][FONT=Verdana] then sees a 512e sectored drive with a 4KB sectored file system. This renders your data inaccessible.[/FONT][/COLOR]

Does this stand, or is there a way to fix this non-destructively?

---

### Post by oldfred on 2014-09-23
The issue is MBR partitions. No drive over 2TiB should be MBR, but some are configured that way for older systems. But then that is a non-standard method.

You should be using gpt partitioning.

Do not know enough to know if you can convert with the logical sector size being 4K. Systems normally have logical sector sizes of 512 even with the physical sectors of 4K.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

