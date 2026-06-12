---
title: "Cannot Suspend in Lucid"
date: 2010-08-01
forum: Hardware
---

### Post by smithj33 on 2010-08-01
The system halts on Not Enough Free Swap. I have Hibernate disabled because I know I don't have enough swap for that and only want to suspend. Suspend works some of the time, but typically I get this:

Aug  1 00:36:03 Carnivore kernel: [82746.136593] PM: writing image.
Aug  1 00:36:03 Carnivore kernel: [82746.136600] PM: Free swap pages: 46233
Aug  1 00:36:03 Carnivore kernel: [82746.136602] PM: Not enough free swap

I didn't think Suspend used Swap? I have only read about needing a large Swap if you are trying to Hibernate. 
---------------------------------------------------------------------------------------------------------------------
~Update - I fixed the above issues by just increasing my swap partition to 4GB. Now Hibernate is not working. The system does everything like it is hibernating, but then actually shuts off.

Any help?

Thanks!
---------------------------------------------------------------------------------------------------------------------
~Update 2 - When I created a new Swap partition the UUID changed and /etc/initramfs-tools/conf.d/resume was not updated. Still doesn't explain why I couldn't Suspend to Disk with a small Swap space. Oh well.....

---

