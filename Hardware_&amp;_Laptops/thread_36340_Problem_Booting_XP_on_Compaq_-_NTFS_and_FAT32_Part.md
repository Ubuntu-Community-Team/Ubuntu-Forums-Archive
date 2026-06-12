---
title: "Problem Booting XP on Compaq - NTFS and FAT32 Partitions appear to be merged as one"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by eminence on 2005-05-23
In order to install Ubuntu, I bought a 200GB Maxtor HDD so I wouldn't have to screw with resizing the NTFS partition on my other hard drive (Seagate 120GB). I had the Seagate as master and Maxtor as slave on ATA.

I installed Ubuntu, and it seemed to go flawlessly, until I tried to boot windows with GRUB. It tried to load Compaq's QuickRestore partition (FAT32, hda1 in linux) that appears before the NTFS main partition that is used by windows. There is no hda2 or anything made for the NTFS. The NTFS partition was not even recognized by the installer, but I had forgotten about the QuickRestore partition and didn't think anything of it when the partitioner said the Seagate only had one partition (FAT32) and a few megs of free space at the end.

I only partitioned and installed anything on the Maxtor drive, so I never touched the actual partitions of the Seagate (windows) drive, but I did put GRUB on the MBR of it. Now, I can't access windows or anything that I had on it. And no, QuickRestore doesn't load either.

So my question is: does anyone know how to get my windows NTFS partition working again? and if so, how?

Thanks in advance,

eminence

---

