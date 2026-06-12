---
title: "Partition problems (transistion from heron to 9.04)"
date: 2009-05-24
forum: Hardware
---

### Post by wuffeemoz on 2009-05-24
okay, so am fairly new at this ubuntu thing, but have been able to handle it on my computer where i don' t mind formating during installation, but i was trying to get my brother's laptop to work for him and have encountered a problem. He had 8.04 on his and the best option for his wifi card to work was to upgrade to 9.04, but he had like 80gigs of media on his windows partition. his old linux partition wasn't used due to lack of internet, so i minimized it during installation of 9.04 (works great btw) and any way, it is not bothering anybody but he is losing like 5 gigs of disk space to something that he is not using. Is there anyway to delete this old partion and format it to fat32 or something without damaging the windows part, or should i just remove the 8.04 option from the grub page and just put it out of sight and mind? Thanks in advance guis.

---

### Post by coffeecat on 2009-05-24
Are you dual-booting Windows and 9.04 from the laptop? That is, are you using grub from the 9.04 partition? If so, there's no reason why you shouldn't reformat the 5GB partition to something Windows can read and delete the 8.04 reference from the grub menu.

Before you do anything, boot up into 9.04, open a terminal and post the output of:

```
sudo fdisk -l
```... and tell us which partition is which. That is, which is 9.04, which 8.04, which Windows and whatever else there might be there such as manufacturer's restore/utility partitions.

Personally, I would use NTFS rather than fat32, because it's a more robust filesystem and 9.04 can read and write to it out of the box. Which version of Windows is it? Vista should autodetect a new fat32/ntfs partition and assign it a drive letter without you doing anything. I can't remember whether XP does as well, but you could always go into Device Manager somewhere in Control Panel and do this yourself.

**Edit:** you can reformat the 5GB partition with Gparted from the live CD, or install Gparted to 9.04. Or, if that's Vista, Windows can do this for you. Windows can't read Linux partitions out of the box, but it can detect that there's a partition there. But post the output of fdisk first and **backup** everything before you do a reformat. Also, make sure you can reinstall Windows if necessary. Reformatting a partition usually goes OK, but things occasionally go wrong - the partition table can get corrupted which means that if you haven't backed up, you've lost everything.

---

