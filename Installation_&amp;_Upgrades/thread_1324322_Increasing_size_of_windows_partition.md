---
title: "Increasing size of windows partition"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by Bloch on 2009-11-12
When I installed ubuntu I left only 8GB for windows XP. It was enough for the occasional times when windows was required -- for example for an official online secure tax returns facility that only works with windows.

But for work reasons I need to use a certain windows software. Wine is not a solution. 

I need to increase the windows partition by a couple of gigs. I don't want to risk damaging the windows installation - I have no install disk.

Other posts generally give help on increasing the ubuntu partition. Can someone advise me if the reverse can be done?

---

### Post by darkod on 2009-11-12
I see no reason not to work.
You would probably have to boot with the ubuntu CD as live CD and use Gparted. That way the hard drive is not mounted and Gparted can work with it.

The thing is that any partition resize includes some risk for the data. Can you take an image of the XP partition mayb with some ubuntu tool/app? I am new to ubuntu so I can not suggest any app, just an idea.

---

### Post by ajgreeny on 2009-11-12
As it is XP, not vista it should be no problem to do both operations using gparted on the live Ubuntu CD.

Boot to live CD, run Partition Editor, shrink Ubuntu partition size and then enlarge winXP partition size.  If you were using vista it would be much safer to shrink ubuntu with gparted and then boot to vista and use its own disk management for the enlargement of its own partition.

---

