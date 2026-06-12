---
title: "Dual boot, but installer graphic shows 100% Ubuntu"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by nick1122 on 2008-12-11
Trying to install ubuntu 8.10 on my laptop with vista on it, so its a dual boot.

I have shrunk the Vista partition, and when I run the Ubuntu installer I choose "guided - use largest continuous free space" option. But the graphic above indicates that 100% of the hard disk will be Ubuntu. I have installed other distro's using this method fine, but just want to double check that choosing this option will not format the vista partition.

Is the graphic just wrong, or do I need to choose a different option?

---

### Post by Partyboi2 on 2008-12-11
You could use the manual partitioning option and create a / (root, ext3 with the mount point set to /)  and a /swap partition (approx x2 of onboard ram eg 512mb +1gig prob no more then 2-3 gig)

eg. 40 gig of space and 1 gig ram
/ = 38gig
/swap = 2gig

---

