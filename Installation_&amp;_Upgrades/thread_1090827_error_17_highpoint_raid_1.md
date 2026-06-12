---
title: "error 17 highpoint raid 1"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by alltechslo on 2009-03-08
I installed 8.04 on a 500gb hard drive. Everything was fine. 

I setup a highpoint raid controller and installed another 500gb hard drive. Then set the controller to raid 1 configuration. Duplicated the 8.04 install.

After the duplication I get error 17?

Can I not use a hardware raid controller? Any suggestions would be helpful. I am pretty green with linux.

---

### Post by dstew on 2009-03-08
I think that controller is not a true hardware RAID, but rather a "FakeRAID". See the [FakeRAID How-To]("https://help.ubuntu.com/community/FakeRaidHowto"). Some people have been able to get Highpoint controllers working with Ubuntu, but it is not easy. Highpoint apparently provides drivers for Linux, but you have to complile the modules yourself. See [this web page]("http://apocryph.org/2007/09/19/ubuntu_feisty_fawn_highpoint_rocketraid_2220_and_satan/") for one person's experience.

---

### Post by ridleyrumpus on 2009-03-11
I have tried to load Ubuntu onto a hard drive that was previously on a highpoint controller, the motherboard in use now does not have a highpoint controller.

When installing Ubuntu it gets to the partioner and then says it has detected a SATA controller and do you want to use it, if I say yes then the partitions are listed as HPT**** ie it seems to remember it was on a HPT controller. 

If I say No and try to set up some new partitions it seems to go OK but then will not boot. If I then go back into partitioner it then detects the previous HPT partitions again.

How do I get rid of the old partitions?

Ridley

---

### Post by dstew on 2009-03-12
I don't have any direct experience with Highpoint controllers or partitions, but in general you would need to delete the partitions using a partition editor like GParted. Then, you would create new partitions out of the unallocated space.

Deleting partitions involves editing the partition table of the disk, and does not require reading or mounting the partitions themselves. So, it probably doesn't make any difference what kind of partitions they are. They should all be easily deletable.

---

