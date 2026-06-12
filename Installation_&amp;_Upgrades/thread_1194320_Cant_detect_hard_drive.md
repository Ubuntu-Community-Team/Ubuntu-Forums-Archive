---
title: "Cant detect hard drive"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by SteelWo1f on 2009-06-22
I bought a bunch of new servers with core i7 950 processors and all the fixings. Unfortunately Ubuntu 9.10 cant seem to detect the hard drives. From a live CD I am able to mount the hard drives, but from the installation menu I just get the message:

"One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?

Activate Serial ATA Raid devices?"

Select Yes or No does not make a difference. Either way, then next menu is the disk partitioner, and no hard drives are available.

Desktop edition will find the hard drives without a problem, but not server edition.

I really need help. I have 10 of these servers here and I need to get Ubuntu on them.

---

### Post by Peter M Mccabe on 2009-07-04
I have the same problem except with a maxtor hard drive and the problem is with that brand of hard drive I tried a spare wd drive and the operating system loaded fine I could not use the wd for this purpose. There is a work around to this problem and that is to install server 8.04 and upgrade it to 9.04 you probably could start with 8.10 but I did not have a 8.10 disk. 
in my case it detected as a serial raid drive.

---

### Post by SteelWo1f on 2009-07-06
Unfortunately I cannot use 8.04 because it can hardly detect any of the hardware on the box.

I did find that this problem is caused by several different older wd hard drives (one 250GB and one 400GB). So I slapped in a newer 500GB drive and it worked like a charm. Odd to say the least.

---

