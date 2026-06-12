---
title: "Separate home partition"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2008-12-11
Hi. I want to have a separate partition for the home directory. I would be very grateful if someone would tell me where I can find a guide which leads me through the steps of a manual partitioning of the disk on install. I have done a search on this forum and not come up with what I am looking for.
I have also googled to no avail. All the guides I find by googling are for adding a home partition after the install. Just so you know my skill level I have tried following one of those and not been able to complete it! One of the things that has floored me in the past is having to chose the size of partitions. I have an 80gb drive.
Cheers.

---

### Post by taurus on 2008-12-11
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ajgreeny on 2008-12-11
At the partitioning part of the install procedure, choose manual, and then choose the disk you want to use.  Now you kust delete any partitions already on there and then make new ones.  I suggest a max of 10GB for / (root), 1GB for swap, but that will depend on how much ram you have; I have 1GB each of ram and swap, and use the remaining space as /home.  Each time you make a new partition you have to choose the mount point.  For root you will need to enter** /**, for home you choose **/home** and for swap there is no mount point.

If this sounds complicated, don't worry, I think it will all become clear as you proceed along the install.

See also [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Scroll down to the last diagram and you will see info similar to what I have just written.  I could have saved myself a few minutes typing if I'd looked earlier.

Good luck, and I hope this helps.

---

### Post by triplemaya on 2008-12-29
Many thanks ajgreeny and taurus, much appreciated. ( There's a lull in the proceedings at present as I can't get my onboard graphics to work above very primitive resolution with the latest Ubuntu distro, and displayconfig-gtk seems to be deprecated:confused:, but I will be returning to battle in the new year!)

---

