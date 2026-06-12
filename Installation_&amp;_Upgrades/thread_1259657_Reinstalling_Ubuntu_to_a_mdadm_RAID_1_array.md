---
title: "Reinstalling Ubuntu to a mdadm RAID 1 array"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by Kazade on 2009-09-06
Last time I installed Ubuntu, I set up a nice software RAID 1 array with the following layout:

/dev/md0  "/" 15G
/dev/md1  "/home" 276G
/dev/md2  linux-swap 5G

I installed this using the Alternate CD. Now I want to reinstall Ubuntu, just replacing the root partition. So I've got a new Live CD and I want to know how to reinstall. I figured that seeing as the array is already partitioned and set up, there should be a way for me to install with the LiveCD that will leave the /home partition untouched, anyone know how I do this?

---

