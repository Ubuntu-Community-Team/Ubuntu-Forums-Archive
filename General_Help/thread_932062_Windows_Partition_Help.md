---
title: "Windows Partition Help"
date: 2008-09-28
forum: General Help
---

### Post by mattimus0674 on 2008-09-28
im trying to partition my desktop. When i first got to the partition window i had a guided option setting up my hard drive between windows and ubuntu. i set it at 25% XP and 75% ubuntu with the total hard drive being 250GB. Anyhow, it started the partition and was at 0% for about 10 minutes, then i powered off and back on. Then, while at the same screen there was no windows xp on it so i have no guide to set up between the two. I already checked to see if windows is still on my computer and it is, it boots up fine. My main question is how do i manually set-up the partition between window xp an ubuntu without is showing windows????

thanks,
matt

---

### Post by zvacet on 2008-09-28
You can choose manual way to partition and you should see all your partitions that way.Shrink your Windows the way you want and on unallocated space install Ubuntu.You can partition ubuntu this way:

1. root = 10GB                    mountpoint /
2. swap = ~ 2x ram
3. home = rest of free space      mountpoint /home

Of course you can partition Ubuntu to match your needs.This is just an example.other way to partition is to get [Gparted live Cd]("http://gparted.sourceforge.net/") and partition with it.

---

