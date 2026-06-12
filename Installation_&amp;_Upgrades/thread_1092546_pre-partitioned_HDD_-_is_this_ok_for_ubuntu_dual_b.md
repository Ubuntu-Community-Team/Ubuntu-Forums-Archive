---
title: "pre-partitioned HDD - is this ok for ubuntu dual boot"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by PDave on 2009-03-10
So last night I reinstalled XP on my machine, i gave xp 60 gb for the "C" drive, and 15 for the "D" drive. I was anticipating using the D drive for my ubuntu install. But from reading the various install guides online, it doesn't seem like this is an option - it looks like the only option is to try and resize the main drive. Is this true? 
Also, what happens if my computer loses power during the install?

---

### Post by Neo_The_User on 2009-03-10
No. It's not. D Drive is your CD-ROM drive. Change it. If it looses power during the install after it formats, you're good. If it looses power during install, you'll need to fix it.

---

### Post by PDave on 2009-03-10
On my computer C: Partition 1 of HDD (60GB), D: Partition 2 of HDD(15GB), E: CD-ROM drive. 

Are you saying that Ubuntu will think that "D" is the CD-rom drive?

---

### Post by kestrel1 on 2009-03-10
> **Neo_The_User said:**
> No. It's not. D Drive is your CD-ROM drive. Change it. If it looses power during the install after it formats, you're good. If it looses power during install, you'll need to fix it.
The D drive is not the CD Rom.
It sounds like it is a 15gb partition on the main hard drive or it is a seperate drive all together.
15gb will be fine for Ubuntu, it doesn't require a huge amuont, but you could resize your windows drive if you wish.
We don't use drive letters in the linux world, we tend to stick to partitions.

---

### Post by linuxisevolution on 2009-03-10
> **PDave said:**
> On my computer C: Partition 1 of HDD (60GB), D: Partition 2 of HDD(15GB), E: CD-ROM drive. 

Are you saying that Ubuntu will think that "D" is the CD-rom drive?

No, the drive letter thing is SO 1970's. ubuntu uses names, like /dev/sda2.

During the Ubuntu install select manual and select your 15gb partition and format it. Then simply set it as ext3 filesystem and / as the mount point.

---

### Post by Neo_The_User on 2009-03-10
> **PDave said:**
> On my computer C: Partition 1 of HDD (60GB), D: Partition 2 of HDD(15GB), E: CD-ROM drive. 

Are you saying that Ubuntu will think that "D" is the CD-rom drive?

Not anymore based on that. And in most cases, The D drive is usually the CD-ROM drive. In Ubuntu, CD-ROM drive is /dev/sr0 (actually /dev/scd0)

---

### Post by Elfy on 2009-03-10
Did you leave the 15Gb unformatted? If so I think that oyu should be able to point the installer at that empty space - at whioch point it will create the necessary partitions - it will need 2 - one for the install and one for swap.

If not choose manual and create the 2 partitions in the empty space. If you need to hibernate then swap should equal RAM, if not then I usually do 512MB swap for 1Gb or greater RAM and 1.5xRAM for less than 1GB.

> Also, what happens if my computer loses power during the install?You will need to start again. If the partitions have been created prior to a power fail then they should be there when you restart - in which case you would choose manual to work with your existing partitions.

---

