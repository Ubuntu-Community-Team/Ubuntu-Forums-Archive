---
title: "Disk Utility reports my FakeRAID as unallocated space"
date: 2012-03-04
forum: Hardware
---

### Post by mercury80 on 2012-03-04
Hi
I've been using Windows 2008 R2 on a server at home. Since I don't like Windows, I want to give my FakeRAID another go on Ubuntu. It seems like Ubuntu 11.10 works out of the box contrary to my last experience with this FakeRAID.

I have 4x2TB disks, configured as 2x4TB (RAID 0) on a [add on card]("http://www.speeddragon.com/index.php?controller=Default&action=ProductInfo&Id=35"). The two RAIDs works well in Windows, but when I boot into Ubuntu, the two raids come up as unallocated space. Tempting to just repartition the drives and see if it works, but I would like to keep the data in the RAID (and I don't have 8TB of free space anywhere).

Any ideas?

Extra info:
Attached a screen shot of my disk utility 
Booted Ubuntu 11.10 from a live-CD

---

### Post by oldfred on 2012-03-04
I do not know RAID. But have some links to info:

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)
[https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html)

Many partitioning tools do not work with RAID, as you have to use other tools to manage it.
Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

With gpt partitioning and BIOS booting you will need an additional bios_grub partition of 1MB for grub2's boot loader to install correctly. I assume you need this in RAID, but know you have to have it in standard desktops. Not sure exactly how to create in a RAID system.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.
However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

---

### Post by mercury80 on 2012-03-04
Just tested [the new beta]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1")... and it works! But the list of drives in Disk Utilities is a bit strange, the RAIDs are listed twice. /dev/dm-0 (not working) is partitioned as GUID, and /dev/dm-3 is said to not be partitioned (but works). I attached a new screen shot.

Guess I'll be installing a beta on my server... This could be fun.

---

