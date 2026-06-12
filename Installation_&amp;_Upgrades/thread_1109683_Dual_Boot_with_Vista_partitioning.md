---
title: "Dual Boot with Vista partitioning?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by jefft113 on 2009-03-29
Hey guys, I am trying to set up my brothers laptop with 8.10 and keep vista he currently has. I have never attempted to partition a hard drive before. I freed space in vista, but I dont know how to make ubuntu install onto that free space. If I select "Guided - use largest contiguous free space", the "After" bar shows that it will use his entire hard drive. Anyone know the right way to do this?

---

### Post by pastalavista on 2009-03-29
Select 'manual' installation and it opens the partition editor. It is much easier to see exactly what you're doing. Just do nothing to the NTFS partitions and you'll be fine. Make a swap partition (about 1 gig) and the rest of the drive the / partition  (or to make easier upgrades also make a /home partition for personal files and settings)

---

### Post by jefft113 on 2009-03-29
Thanks, I have been looking at the manual partitioning. I tried making a swap, /, and /home but after I make 2 of the 3, the remaining space is listed as unusable, anyone clues as to why this would be?

---

### Post by pastalavista on 2009-03-29
I believe you're only allowed 4 physical partitions on 1 disk but you can have any number (I think) of 'logical' partitions. Do you have 2 NTFS drives? Probably and one of them is for backup nd recovery. I have an extended logical partition with my swap and /home partitions and / on a primary.

---

### Post by Mark Phelps on 2009-03-29
You can only have four Primary partitions on a drive.  Typical multiboot setup has the first partition as Primary and holding MS Windows, and an Extended (logical) partition holding all the Linux partitions.

And, since you have a laptop, I suspect you only have one physical drive.

Also, if you don't have a Vista DVD or a Vista recovery CD, then go to the Neosmart forums and download a recovery CD image through torrents and burn it.  When you install Ubuntu, if you write GRUB to the MBR, it will overwrite the MBR that Vista created.  If you later decide to remove Ubuntu, you will need the Vista medium to restore the original MBR so that you can boot directly to Vista again.

---

