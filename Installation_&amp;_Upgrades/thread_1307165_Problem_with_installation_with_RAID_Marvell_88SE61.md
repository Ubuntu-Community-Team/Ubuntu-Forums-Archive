---
title: "Problem with installation with RAID Marvell 88SE6121"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Camicia on 2009-10-30
I bought a motherboard Foxconn P55A-S ([http://www.foxconnchannel.com/Product/Motherboards/detail_overview.aspx?id=en-us0000473](http://www.foxconnchannel.com/Product/Motherboards/detail_overview.aspx?id=en-us0000473)) that has a Marvell 88SE6121 controller (88SE61xx series).

I bought the motherboard having a RAID system so it could guarantee me that my data are safe if one HD dies. I would like to be able to replace that HD and expect that automatically or with a simple tool, I would be able to restore the system with all the HDs integer. I would also expect an increase in performances.

I have 4 HD by Hitachi Deskstar 500Gb each. I was thinking about using 3 of them in RAID 5 and 1 of them as a spare (maybe as a backup device for now).

I set up in the BIOS "Configure SATA as" -> "RAID". then pressing Ctrl-I, I could then access to an extended BIOS during the BIOS where the Intel (R) Rapid Storage Technology pop up. 

I set up a RAID 5 with the first 3 disks.

During the installation of Ubuntu 9.10 Server, It says that a RAID has been recognized and if I want to use it. However in this case only the 4th HD (the spare one) is displayed.

Looking on the Internet, I realized that the Marvell 88SE6121 is a "fake" Raid (the operations are run by the CPU). :-/

I found that Intel® Matrix Storage Manager (and I am not sure that it is completely related what I own) does support only RAID 1 and 0. So I decide to give it a shot.

I reconfigure a RAID 0+1 and this time the installation show me that I have 2 volumes of 500GB each (instead of one of 1Tb as expected). 
Trying to do something with one of the displayed drive I ended up with some partitions that I cannot remove. Plus the installation hung up on formatting one of this partition (showing 33% and not progressing for at least 15 min).

What do I want?
1)  Deleting the partition created on the first of the 2 drives in mirroring. I am not sure how you can do that from the installation.
2) Most important: Being able to take advantage of integrity or a RAID 1 or (better) RAID 5. Then it is nice to have: increased performance from RAID 0/1. 

How do I get it to work?

Thank you in advance,
   Camicia

---

### Post by Camicia on 2009-11-04
up :popcorn:

Still looking for help on this!!!

---

