---
title: "IBM T60 - partitioning hangs"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by ziphnor on 2007-04-23
Hi,

I just tried to install Feisty on my work laptop IBM T60 (Core Duo T2400). It apparently has a SCSI disk, containing a Windows XP partition and some IBM crap quick restore / diagnostics. When i booted feisty and clicked install, the installation hung in the partitioning phase. I just saw 'how do you want to partition?' and the 'busy' cursor, but nothing happened. 

I then ran fdisk, nuked the partitions, and now it seems to work. Thought this might be useful to anyone else with the same issue.

Z

---

### Post by Hookheathen on 2007-05-14
Hi Z,

I am experiencing precisely similar problems when attempting to load Feisty F onto my Thinkpad X40 - the partitioning window hangs. You say you ran fdisk and "nuked the partitions" but what then? Apart from removing the "IBM crap" did it also dispense with Win XP altogether? This is not what I wish to do and wonder if by removing these partitions you could still dual boot into Win - in case of extreme need!

Any guidance gratefully appreciated.

HH

---

