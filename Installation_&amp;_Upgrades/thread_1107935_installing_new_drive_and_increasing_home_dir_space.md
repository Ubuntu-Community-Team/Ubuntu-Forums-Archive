---
title: "installing new drive and increasing /home dir space"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by mscoxoh on 2009-03-27
I've found several posts/docs that deal with adding a second drive, but they all assume the user just wants to add a new partition. Can I increase my existing space/partition? I'm running 7.10 server and I'm only using it for Squid/DansGuardian, and for Samba to backup household PCs' hard drives (Mac TimeMachine, etc). I'm not concerned about "best practices" in spanning partitions (unless there's some big performance hit) because I can rebuild the thing easily if a drive fails and no data is lost. Here is how I'm partitioned now:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       60801   488135025    5  Extended
/dev/sda5              32       60801   488134993+  8e  Linux LVM

Real basic, right? I'm going to add a 1TB drive along with the existing 500gb drive and just want to make all the /home directories see 1.5tb of space. Can I do this, and how? Thanks!

Michael 
(I only have *very* basic linux skills, BTW)

---

