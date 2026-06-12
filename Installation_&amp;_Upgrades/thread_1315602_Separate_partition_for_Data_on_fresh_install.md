---
title: "Separate partition for Data on fresh install?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by DedMoroz on 2009-11-05
Ive read about it in the past, but just dont know how to do it. Are there any good walk throughs or instructions detailing how I can create a separate partition for my OS and another for my data? 

I want to install 9.10 on a computer at work, its used only for music... we have like 80gb of songs and right now Im transferring them all to a USB drive. Its currently running 8.04. We have a bad wifi connection where the computer is at, so updating to 8.10, then 9.04, then 9.10 seems ridiculous when I can just do a clean install of Karmic, plus I can install it with EXT4 too.

So... any ideas how I can partition the drive correctly? I dont recall Ubuntu installation giving such an option either. Thanks for any help!

---

### Post by DedMoroz on 2009-11-05
Am I wanting to make a separate /home partition?

---

### Post by mechro on 2009-11-05
> **DedMoroz said:**
> Am I wanting to make a separate /home partition?

That's a personal choice. I don't have a separate /home partition and prefer to transfer files and settings between versions/distros. If you're new to Ubuntu I wouldn't bother worrying about a separate /home partition. What would suit you would be a / partition plus a data partition mounted as /media/data.

During the installation you'll need to go for the manual partitioning  options. Read this guide here and come back with any questions...

[http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide](http://www.basicconfig.com/ubuntu_desktop_manual_partition_guide)

---

