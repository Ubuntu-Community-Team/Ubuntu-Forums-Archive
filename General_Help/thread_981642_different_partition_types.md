---
title: "different partition types"
date: 2008-11-13
forum: General Help
---

### Post by Immort4lKill3r on 2008-11-13
i just started using ubuntu, after installing a dual boot setup with xp and vista on my laptop[intelcore2duo, 4gbRAM, 250SATAHDD, 2mbL2, from zt technologies, called the element, and a bunch of numbers[from newegg, and lucky i got it when i did, they're'nt avalable and more, and at 800$ w/a duallayerdvdburner, 4gigsDDR2RAM, 17'display, vista preinstalled, wifi, 802.11A/B/G capable wireless card, 1.3mpwebcam, sd mem slot, and ALOT more, like an eSATA[e for EXTERNAL] and is the ****.]]]but after i installed xp onto vista, [streamlining the drivers of my SATA HDD on the xp disk] and using diskpart command to slice it down. but when i put xp back on it just didnt bring anything new, or cool, or impressive or that showcases its true power, AND the xp 64bit driver for my nvidia 512mb 8100m gt card. that put the last nail in the coffin. so i reformatted again, using ubuntu, but when i came across the partitioning[which is a million times better, easier, user friendly, [and YES, ACTUALLY SIMPLE, OMG!!]

onto my question, when partitioning my drive, making a logical D:\ drive (thats right, right?? what's the difference between logical or primary), w/ ab 8gigs of memory] and a swap of ab 500[i think] but when i was partitioning i noticed that there are ALOT of different filestructures to pick from. i chose the first one, only knowing what FAT is and how much it blows due rediculous clustersizes] and clicked next. it said something about how it needs an ubuntu drive and after a little trial and error found that referenceFS[or somethin like that] actually worked. Why? and whats the best one to pick? is one good for one thing and not another? whats the ups and downs?
i just want to know whats best for the laptop. vista is still on it. and i did search around for em, no luck
-ubuntu's addictive, i'm just getting started...

---

### Post by psusi on 2008-11-14
Drive letters are a DOSism; they don't exist in *nix.  The difference between primary and logical partitions is that there is only room to define 4 partitions in the MBR.  If you want more, then you use one of the 4 primary partition slots to make a logical partition that has its own partition table which can define a logical drive, and optionally chain to another logical partition.  The chaining part is all taken care of behind the scenes so you just see logical drives which start counting from partition 5 and go up.  The partition 4 that is used to contain logical partition 5 is left hidden, which is why the numbers will skip from 3 to 5 if you have 3 primary partitions with at least one logical partition.

As for filesystem type, best to stick with the default ext3.  It is simple and reliable.  ReiserFS is a tree structured system that handles many small files a bit better than ext3, but has not been updated in a few years and isn't likely to now that the author, Hanz Reiser, is in jail for the murder of his wife.

---

