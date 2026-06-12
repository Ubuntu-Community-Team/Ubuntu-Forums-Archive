---
title: "Ubuntu 9.10 Intel raid support"
date: 2010-04-05
forum: Hardware
---

### Post by joker535 on 2010-04-05
I have a home built machine using an Intel S5000XVN (S5000XVNSATAR)workstation board with dual L5310 quad core xeons and 8G of FBDIMM ram. I am running Ubuntu 9.10 64 bit desktop. I just got a great deal on a pair of Intel X25 SSD's and I would like to run them as a raid 0 for performance as a boot drive. I would prefer to use the onboard raid controller for this but I can't get the ubuntu installer to see it. I searched and turned up nothing. Is there any way to use the hardware raid controller for this?

Thanks

Bob

---

### Post by joker535 on 2010-04-07
Well I got no response here so I ended up going with the software raid for now. I read all kinds of tutorials about this but none of them worked. I ended up killing a couple of hours experimenting with it and finally got it working. Just in case someone else was trying to do this here is what I have and what I did.

Hardware-Intel S5000XVNSATAR dual 771 mainboard with dual quad core L5310 xeons and 8 x 1G FBDIMM ram. Drives are a pair of Intel X25s running off the onboard SATA controller with RADI disabled and AHCI enabled. I am running ubuntu 9.10 64 bit from the alternate install CD.

You start the install as normal and when you get to the partitioning you choose manual. I created a 0.5G partition and set it to bootable, a 1.7 G partition, and then the last partition (bootable) used the rest of the space. The small partition is for /boot and the 1.7 is for swap. According to the documentation I found you can not have /boot on a raid 0 as the ubuntu bootloader will only work with software raid if a raid 1 is used.  Both drives were set up identical. I then went into the software raid and created the first raid as a raid1 with 2 devices and no spares then joined the two .5G partitions to it. I then created a raid o with the two 1.7G partitions for swap and the final raid 0 for root. Once I choose finished I set each partion to be formatted and assigned its respective duty (/boot, swap, and /). Fromt here the install went just as any other ubuntu install and it works great. 

My hardware has a built in 12-15 second hardware test before the BIOS comes up but from the time the BIOS finishes to the login for the ubuntu user is just under 8 seconds. Much better then my old hard drive. I am going to see if I can run a benchmark test to put some numbers to this for comparison.

If anyone else is doing this, I wish you the best of luck.

Bob

---

