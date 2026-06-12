---
title: "Installation Advice Needed"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by gwales on 2009-04-17
I have a new Windows Visa laptop with 2 320 Gb hard drives.

The windows system disk (bootable) already has 4 partitions and I have shrunk the main system partition to create 46Gb of unallocated space. I can't do anything with this since I have 4 primaries already.

What would be the best strategy to achieve a dual boot set up?

Back up one of the data carrying primaries and make it extended?

All advice appreciated! 

Gary

---

### Post by lisati on 2009-04-17
> **gwales said:**
> 
Back up one of the data carrying primaries and make it extended?

I'm inclined to think along similar lines to you on this one, with making a backup (always a good idea when tinkering with partitions) and changing one partition to an extended one.

I'm not sure if the Ubuntu installer will take care of this automatically for you if you choose the "guided: use the largest contiguous/continuous free space" option, maybe other users can fill us in.

---

### Post by arashiko28 on 2009-04-17
I think it's better if you go manually that way you can choose the partition without a chance of error.
Now, if you choose guided, you're allowed to toggle the division bar, and adjust the amount of space you want or need.
Always backup, things can go perfectly fine or stupidly wrong.

---

### Post by zvacet on 2009-04-17
> I can't do anything with this since I have 4 primaries already.

Yes,you can.from unallocated space make extended partition and then you can make logical partition inside extended one.You may wish to download [Gparted live CD]("http://gparted.sourceforge.net/") to do that.After that choose manual way to install Ubuntu.

---

