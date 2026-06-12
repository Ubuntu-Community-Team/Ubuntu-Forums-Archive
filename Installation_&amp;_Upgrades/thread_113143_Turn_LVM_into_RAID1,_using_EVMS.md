---
title: "Turn LVM into RAID1, using EVMS"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by pfm102 on 2006-01-05
Hi

I have just completed a server install of Ubuntu 5.10.  I partitioned my hda using LVM, because that sounded like a good idea (what with allowing me to defer how partitions can grow to fill the drive), and I hadn't used it before so decided to give it a whirl.  

I was confused, in the installer, with how to accomplish what I wanted, though - I have 2 identical drives, and want to set up software RAID1, with LVM, preferably managed by this other useful thing I found when googling, EVMS (which I found to my joy is part of the server default install).  The installer didn't make it clear how to do both LVM and RAID - at least, I didn't understand how that might be possible.

So, at the moment, I have my system on hda's set of LVM volumes, and currently hdc is sitting there empty and lonely.

I am aiming at Ubuntu server, using LVM on top of RAID1 if I've understood correctly, and this is possible.

I would like to find out either:
a) how to set up RAID1 on my existing setup
b) how to install Ubuntu server (ie, what to do in the partitioning step) such that I achieve my aim as above

I don't mind wiping and starting over, if that is simplest, since I'm treating this as a learning exercise.  I would like to do things in the accepted Right Way - and by all means, please point me at resources for that ideal.

Thanks in advance!

---

