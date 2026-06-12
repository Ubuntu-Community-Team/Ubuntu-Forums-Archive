---
title: "How do I uninstall GRUB? Sounds simple, but...."
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by picardo on 2009-06-04
Here is the thing. I have two versions of GRUB right now. The first one gives the usual GRUB ERROR 17...and then the second one kicks in. 

How I ended up with two GRUBs on one computer is a harrowing tale for another day. But the short of it is, I deleted the partition of Ubuntu, right after installing Wubi and assuming I didn't need it anymore, and that is how I started getting the errors 17. So I created another partition and installed Ubuntu. That seems to have installed a GRUB parallel to the defunct GRUB.

Did I look at the posts on this forum? yes, and this thread was very helpful:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

But I couldn't find the file "devices.map" on the mounted partitions. (Ubuntu was not installed anymore at that point, after all.) How would I disable GRUB now? I want to get rid of the Ubuntu installed on the new partition too.

Please tell me there is a way to remove the GRUB and Ubuntu on partition.

---

### Post by zvacet on 2009-06-05
If I understand you right you want to remove Ubuntu and grub.In that case read [this]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe") after that you can remove ubuntu partition with [Gparted live CD.]("http://gparted.sourceforge.net/")

---

