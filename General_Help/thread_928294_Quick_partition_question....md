---
title: "Quick partition question..."
date: 2008-09-23
forum: General Help
---

### Post by earthpigg on 2008-09-23
My computer's HD is currently: 
-130 gig windows vista partition, which i never use.
-30 gig ubuntu, ext3 (that's default, right? not at the computer, so i cant check... but its whatever default is).
-unopened OEM 64 bit vista sitting around in a desk drawer.

Objective:
-130 gig Ubuntu, with that 64 bit OEM Vista installed in one virtual enviornment or another. 
-30 gig to play around with other distros on.

tell me if what is bouncing around in my head will work:
1. using gparted for all of this, format the current vista partition.
2. resize my currently in-use Ubuntu partition from 30 to ~130 gigs, leaving the 30 as my distro playground.
3. cruze over to the virtualization forum and learn how to virtualize.


anything i am missing? reason i ask is because i know NTFS can act weird when you resize it to much or in certain ways...

---

### Post by tuxxy on 2008-09-23
1. using gparted for all of this, format the current vista partition.

**Yes you can format the current and create new partitions using gparted**

2. resize my currently in-use Ubuntu partition from 30 to ~130 gigs, leaving the 30 as my distro playground.

**Yes, delete your windows partition then resize your ubuntu **

3. cruze over to the virtualization forum and learn how to virtualize.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

**Download the PUEL version, [heres a guide]("https://wiki.ubuntu.com/VirtualBox") on creating a new virtual drive.**

---

### Post by earthpigg on 2008-09-23
thanks, chief.

---

