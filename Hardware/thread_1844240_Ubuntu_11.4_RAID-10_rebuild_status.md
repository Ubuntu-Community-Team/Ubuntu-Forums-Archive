---
title: "Ubuntu 11.4 RAID-10 rebuild status?"
date: 2011-09-14
forum: Hardware
---

### Post by fixerdave on 2011-09-14
More of a curiosity than a problem...

I have a box that supports Intel Rapid Storage Technology SATA2 raid arrays - so I built one, works just fine.  I left my OS disk alone and just threw an extra 4 drives in the system, used the pre-boot Intel menu to configure them as RAID-10 and installed Ubuntu 11.4 on the single drive.  Nothing fancy, no dual boot, no extra raid packages installed, nothing.  In Disk Utility, I just picked the raid drive and formatted it... done.  The raid array comes up a little odd in Ubuntu proper, showing 2 of them in the places menu, only one of which works, and the order is a little random on each boot.  But, it works just fine.

So, the other day, I start getting SMART events (the computer, not me... I'm still waiting for those).  One of the raid drives was failing.  No problem, I have a spare, so I threw it in.  The Intel pre-boot setup declares the array as "rebuilding in the OS" and so I boot into Ubuntu.

So... how do I see if the drive is actually rebuilding in Ubuntu.  Disk Utility shows everything as fine.  No rebuilding status anywhere.  I'm assuming the array is rebuilding in some fashion as the drive light's been on steady for the last while, computer running a tad slower.  Is there any utility out there (cl or gui) that lets me see what it's doing now?

---

