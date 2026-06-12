---
title: "Pre-partitioned hdd for dual-boot?"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by Traprock on 2008-12-27
Hi Ubuntu Helpers,
new to Linux, keen to go the evolutionary route via dual-boot, with view to ultimately windows-free. I am running XP, and have downloaded ubuntu 8.10. My hdd is 150gb, XP is on 80gb NTFS partition, 80gb NTFS partition is empty. All the dual-boot tutorials assume one partition only with existing windows OS. My readings indicate that partitioning via 8.10 install is fairly 'automatic'. So, should I remove the second partition and let the install do its thing, or can I install to the second partition OK?
Does it all become obvious during the install? Also, is it correct to assume that future data will be stored in the windows partition, eg 'my documents' and therefore the 1st partition should be kept larger? Or am I missing something here?
Any advice or pointings to help appreciated.

---

### Post by Partyboi2 on 2008-12-27
> Also, is it correct to assume that future data will be stored in the windows partition, eg 'my documents' and therefore the 1st partition should be kept larger? Or am I missing something here?
When you install ubuntu it will install to its own partition unless you choose to install inside windows using the wubi installler. Ubuntu uses ext3 as its native filesystem even though it can read/write to ntfs. 

> My readings indicate that partitioning via 8.10 install is fairly 'automatic'. So, should I remove the second partition and let the install do its thing, or can I install to the second partition OK? At the partitioning stage of the install you should be able to select the 2nd partition to install ubuntu to. Just make sure you select the correct partition to use not your windows one and remember to backup your important stuff.

---

### Post by albinootje on 2008-12-27
> **Traprock said:**
> 
Does it all become obvious during the install?

It will become obvious during the installation.

You will need at least a Linux swap, and a Linux / partition.
/ being the mountpoint for your Linux partition.
As a rule of thumb make the swap twice as the amount of RAM that you have.

---

