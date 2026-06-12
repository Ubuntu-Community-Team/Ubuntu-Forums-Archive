---
title: "Pre dual boot prepwork questions"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by BrandtP on 2009-07-03
Hi,
 
I have reviewed multiple posts about dual booting, yet I still have questions.
I currently have Windows XP installed on my single IDE HDD system, but I'm likely going to buy a larger drive. I want to set up a dual boot with Windows XP & Ubuntu. After partitioning the new drive, will the new partition size be preserved if I copy the contents via ghost image of my old drive to the new C: partition? I presume prior to installatin I would partition the drive into a C: and however extra partitions I want.
 
Should I decide to utilize 2 drives, the new one is likely to be SATA and larger. My current drive is IDE. I would prefer the new drive be used for Windows due to my gaming needs. Will this make a difference?
 
Thanks very much in advance for the help.

---

### Post by starcraft.man on 2009-07-03
> **BrandtP said:**
> 
After partitioning the new drive, will the new partition size be preserved if I copy the contents via ghost image of my old drive to the new C: partition? I presume prior to installatin I would partition the drive into a C: and however extra partitions I want.
 
Should I decide to utilize 2 drives, the new one is likely to be SATA and larger. My current drive is IDE. I would prefer the new drive be used for Windows due to my gaming needs. Will this make a difference?
 
Thanks very much in advance for the help.

Yes to your first question, that should work. Before hand, ensure you've backed up all vital data to somewhere safe please. Then repartition both drives into the configuration you want, then restore the image you've made of Windows to the new SATA drive partition. It is important to note, if you installed XP on the IDE drive you can't just restore that image to a SATA drive, it will fail to properly run since XP natively lacks SATA drivers. If it's not XP, shouldn't be a problem.

As to your second question, I suggest you put both OSes on the SATA drive for performance sake. A likely boot set up would be the following:

- Primary partition
--> Extended/logical partition

SATA
- Windows
- Storage (you'll probably have excess space left over from others, just make it an NTFS partition)
--> / (root directory)
--> Swap
--> /home 

IDE
- NTFS Storage (Whole drive, NTFS is you want easy compatability with Windows, ext3/4 if you just want to use it for Ubuntu)

Alternatively, you could put your /home partition on the IDE drive. I do recommend keeping the OSes both on SATA, much better IMO.

If you need a partitioner I use [gparted ]("http://gparted.sourceforge.net/download.php")for all my needs. See the documentation section if you need a bit of help understanding it. You don't need to use their live CD, it's on the Ubuntu live (if not installed then in the repos).

Any questions, just post back.

---

