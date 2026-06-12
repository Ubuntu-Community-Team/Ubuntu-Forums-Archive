---
title: "Do the advanced format [4k sector] drives still take a preformance hit?"
date: 2010-04-26
forum: Hardware
---

### Post by discord on 2010-04-26
I was going to buy a wd6400bevt 2.5" drive and put it in a portable USB case, but wanna wait until we can partition these things properly in 9.10. Somebody please let me know when I won't take a performance and or size hit. I'm not planning on using the ubuntu installer, rather plan on using gparted, since I'm not installing OS to the disk,just using it for external storage.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/530071](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/530071)
[http://ubuntuforums.org/showthread.php?t=1407098](http://ubuntuforums.org/showthread.php?t=1407098)

---

### Post by srs5694 on 2010-04-26
If you're prepared to partition the disk before installing Ubuntu (using System Rescue CD, PartedMagic, or a similar tool), you shouldn't have any problems; but you do need to know what you're doing. (It's conceivable that you could partition the disk properly with Ubuntu's installer, but I don't know that for a fact.) I recommend using fdisk (for MBR) or gdisk (for GPT) to do the partitioning; parted (text-mode for MBR or GPT) and GParted (GUI for MBR or GPT) are a bit more awkward for this. Also, all of these tools have seen dramatic changes in their last few versions related to partition alignment, so you're best off using the very latest version you can find. (I don't know how up-to-date the various emergency discs are in this respect. I recommend you compare version numbers for the on-disc tools to those on the partitioning tools' respective home pages.)

Be sure that your partitions start on 8-sector (4096-byte) boundaries. In fdisk or parted, set the units to sectors ('u' in fdisk, 'unit s' in parted); gdisk defaults to sectors for its display. Type your sector start points in sector values that you've verified (via a calculator) are on 8-sector boundaries, such as 64 or 2048 for the first sector. Display your complete partition table when you're done to verify that all partitions start on 8-sector boundaries.

If you plan to multi-boot, be aware that Windows Vista and 7 both create partitions on 2048-sector (1MiB) boundaries by default, so if you use their partitioners, you'll be set for any partitions you create that way. Windows XP and earlier, OTOH, create partitions on cylinder boundaries, which usually don't correspond to 8-sector values. Thus, if you plan to install Windows XP or earlier, you should create the Windows partitions in some other way. That topic can get a bit hairy, in fact, so post again or Google it if XP compatibility is important to you.

---

### Post by discord on 2010-04-26
Hi, thanks for the reply! I do not plan on using the drive as a boot disk, just as external storage. So if I partition in fdisk as you say, then I will not take a performance hit, as the drive will be setup correctly. I'm not really using windows these days. Best!

---

### Post by srs5694 on 2010-04-27
Boot vs. non-boot is irrelevant. Multi-booting (whether the disk is used as the boot disk or not) may be relevant because you may end up using tools in two or more OSes to set up the disk. What *is* relevant is getting those partition start sector numbers right!

---

### Post by ALLurGroceries on 2010-04-27
Just found this devworks article on my feedreader... addresses your question: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=drs-#gpt_solution]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=drs-#gpt_solution")

---

