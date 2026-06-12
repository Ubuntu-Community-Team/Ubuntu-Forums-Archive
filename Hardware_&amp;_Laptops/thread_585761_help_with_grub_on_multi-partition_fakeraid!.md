---
title: "help with grub on multi-partition fakeraid!"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by heavydawson on 2007-10-21
I've got a Promise Fasttrak 378 (Software RAID) RAID 0 array partitioned in 3.
Partition 1 is a 100 GB NTFS Win XP volume
Partition 2 is a 8.5gb Ext3 volume
Partition 3 is a 1.5gb SWAP volume.
I want to install Ubuntu 7.10 on the EXT3 volume, but am having some problems. I boot the live CD, use DMRAID to activate the partitions, and then install Ubuntu on Partition 2. At the last stage before the final install setup stage, I tell GRUB to install on hd(0). The install went ahead, but at the very end, there was a fatal error when GRUB tried to install. I tried to re-run the installation setting the install location to hd(0,0) but only got the same error.

Can anyone help me setup GRUB so I can dual-boot Windows / Ubuntu?
What value do I need to enter at the end of the ubuntu install stage?
Maybe I just need to install GRUB manually to replace the Windows bootloader, and configure it to pick up both the Win XP and Ubuntu installs.

Any help at all would be great thanks guys!

---

