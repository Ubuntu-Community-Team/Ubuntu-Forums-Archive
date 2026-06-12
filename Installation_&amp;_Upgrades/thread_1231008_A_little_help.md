---
title: "A little help?"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by Jdutch101 on 2009-08-04
Hey all,

sO, I am trying to install Ubuntu on my new "old" computer, but for some reason this is proving rather difficult. I am trying to install it on a P4 intel chip set, with an 80Gb HD set up as the master drive, and a 60Gb HD as as a slave drive. They are both IDE drives. The computer has two CD-Rom drives. One is an LG 52x Max drive and the other is a CD-R rewritable burner drive. So far, every attempt to install right from the disk menu fails when I put the disk in the burner drive. And once I made it to the partitioning loader when I put it in the other LG drive, but for some reason I continually get a frozen machine at varying points of installation. I'm not sure what the problem is. I know that the 80Gb HD is partitioned into a 32 gig and a 35 gig. could that be because of the physical pin configuration on the back of the drive? I know how to change the pin bridge so that one can distinguish master from slave, but I'm not sure about the limiting to 32gb capacity thing...

I know this sounds confused, but that's because its really annoying and I don't know a ton about computers...


Thanks
J

---

### Post by prshah on 2009-08-04
> **Jdutch101 said:**
> 
So far, every attempt to install right from the disk menu fails

some reason I continually get a frozen machine at varying points of installation. 

I know that the 80Gb HD is partitioned into a 32 gig and a 35 gig. could that be because of the physical pin configuration on the back of the drive?


The physical pin configuration to limit the drive's capacity to 32GB is for older motherboards that cannot see over 40GB. If your 80GB drive is recognized as an 80GB drive (or approx 72GB) then you don't need to make any configuration changes to the jumpers on the drive. Partitioning of the drive has nothing to do with jumpers on the drive.

I suspect your CD; either the disk or the drive is bad. I suggest you create a fresh disk, burnt at as as low a speed as possible. Then run the media check option available at the startup menu.

You can (and should) also run a memory check from the startup menu, especially if you have mismatched memory clips.

---

