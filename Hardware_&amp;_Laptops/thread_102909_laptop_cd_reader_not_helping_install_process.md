---
title: "laptop cd reader not helping install process"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by randum_idiot on 2005-12-13
My computer hangs during the installation of ubuntu 5.10, it gets up to the part where the title says "detecting hardware to find CD-ROM drives" at 86% where it says "loading module 'ide-cd' for 'linux ATAPI CD-ROM"

This computer does meet all the minimum requirements...

It is not because of a scratched/bad/dirty CD

I tried it with the live CD and it does the exact same thing...

My computer is an ACER travelmate 520iT and although i doubt it makes a difference on why it hangs i have the hard disk with 2 partitions already set up (both FAT32) with the main partition (10 GB) with windows 2000 pro and the other partition (5 GB) with win98se. The last 5 GB is left for UBUNTU (un-partitioned as yet).

I beleive i have figured the problem to be that i need to find an appropriate cd rom driver for ubuntu (found this out by booting the install into expert mode and removing that stage (loading module 'ide-cd' for 'linux ATAPI CD-ROM')

If anyone can find a Matshita CD-ROM CR-176 driver for ubuntu, it'd be much, much appreciated!!! I have actually found out from searching a bit that this brand is actually under the name MATSUSHITA which is apparently panansonic...

Anyone that can get me a driver disk that i can use when i try installing under "expert" would be much, much appreciated!

---

### Post by Trynemjoel on 2005-12-13
Having the exact same problem on my laptop. 

My CD-ROM is AOPEN DVD RW ISU8424E. I have looked around on the forum and cant say that ive found a sulution to the problem. Please give us a hand here, dont make me use windows on my lappy :(

---

### Post by ryanhuggins on 2005-12-26
I have the same problem on an IBM i Series 1400 (type 2611-452)  The CD drive is a Matsushita SR-8171.

Any help would be appreciated.  I tried searching for drivers, but they (panasonic) only makes dos and windows drivers.  I tried the dos ones for fun, but they didn't help.

Any ideas?

-Frustrated in CA
Ryan

---

### Post by ryanhuggins on 2005-12-26
I found a solution that worked for the live CD.  typing 
live pci=noacpi (Enter)   at the boot: prompt.

I found it from this page:  [http://www.ubuntuforums.org/showthread.php?t=88762](http://www.ubuntuforums.org/showthread.php?t=88762)

I'll be trying it with the install CD soon.:p

---

### Post by Jagged on 2006-04-29
I hope this works, I also have a IBM thinkpad 1400 i've been trying to get Ubuntu on with the same exact problem!

---

### Post by Jagged on 2006-04-30
It works! I am one happy Ubuntu user now!

---

