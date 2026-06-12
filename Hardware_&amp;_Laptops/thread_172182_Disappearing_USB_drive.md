---
title: "Disappearing USB drive"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by Sauli on 2006-05-08
When I plug in my Lacie 250G USB connector to my Ubuntu 5.10 PC the Lacie drive icon comes visible in the Nautilus file browser as unmounted. What is strange  at this point is that also an other volume, labeled '512 bytes Volume' gets also mounted. I don't know what this is.

Then more strange things happen.

If I do nothing the Lacie drive icon, and the mysterious '512 bytes Volume' disappear after 30 seconds and then after 5 seconds they come back.

If I click the Lacie icon and mount it I can go and explore the files for a while after which Nautilus file browser kicks me back to my /home/user directory.


I have tried to isolate the problem and noticed that:
1. External Firewire Lacie hard drive works fine 
2. The same USB Lacie hard drive which has the problem in Ubuntu works fine in Windows


I'm not sure but it may be that the USB drive worked fine before I tried to repartition it with gparted.  My intention was to repartition part of the fat32 filesystem volume to ntfs in order to capture some big video files there. During the repartition something happened and as result the partition didn't change - I believe.  Now I don't know what is the cause and what is the effect - did the repartitioning corrupt the filesystem or did a faulty USB drive handling prevent the repartitioning.

Any hints anyone ?

Sauli

---

