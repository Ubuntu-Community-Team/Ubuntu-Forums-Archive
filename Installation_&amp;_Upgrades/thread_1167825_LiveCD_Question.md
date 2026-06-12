---
title: "LiveCD Question"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Stavro on 2009-05-23
Hi, I have the Ubuntu 9.04 LiveCD and I was just wondering, how easy is it to use this disc to upgrade an older Ubuntu (7.04) which is currently dual booting with XP?

If possible, is this the best route? If an upgrade is not the best road, I assume I should just wipe the partition where 7.04 resides and install 9.04 to that. XP should remain intact in such a scenario? What about GRUB? I would have liked to keep the existing EXT3 file system, but permissions confuse me, perhaps it&#8217;s not possible to access home files afterwards?

---

### Post by Happy_Man on 2009-05-23
From 7.04 to 9.04 it is best to do a full wipe and reinstall.

So long as you make sure to not touch the Windows partition when reinstalling, everything should go fine. GRUB will update along with Ubuntu.

---

### Post by lindsay7 on 2009-05-23
It should not be hard to do this. If you have a separate hom partition, good you can keep what is in it. If you do not, copy what is there somewhere so that you can put it back after the update.

When you do the upgrade with the live cd, use the manual option. It will show the existing partitions and you can click on each one to set it up. There is a small box that you check if you want to format the partition and you can choose the file system. i.e. fat, ext3, ext4, etc. You can also set the mount points for each partition. The partition where Ubuntu goes should be set as / and you need to format it. If you have a home partition DO NOT FORMAT it. That way you will keep what is there. The swap partiton will take care of itself.  If you have window on a partion, just leave it alone.

When you run the live cd you can get all the way to this point without changing anything so just take a look at what you need to do up until the point that you actually edit any of the partitions.

---

### Post by Stavro on 2009-05-23
Thanks a bunch for the replies.

---

