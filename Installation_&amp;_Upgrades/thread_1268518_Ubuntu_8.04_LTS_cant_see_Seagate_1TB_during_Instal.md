---
title: "Ubuntu 8.04 LTS cant see Seagate 1TB during Installation"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by EJI on 2009-09-17
Hi Ubuntu Team,

I am having a problem installing Ubuntu 8.04 LTS 64bit Server on my machine.

**Problem:**
The hard drives are not detected for some reason during installation.


**Hardware:**
2 x ST31000528AS SEAGATE 1TB 3.5" SATAII, 3GB/S 7200RPM, 32MB Cache
4 x 2048mb 800Mhz Ram Modules
Intel DG43GT Motherboard
INTEL Q9550 CORE 2 QUAD S775, 2.83GHZ,1333FSB,12MB


**Attempts so far:**
I have tried the desktop version 8.04 64bit  and proceeded to enter Live Version.

Went  into Gparted, but no Hard disks detected, dont know if it is possible on this version.  

Ubuntu 9.04 Desktop does detect the hard drives, though but is not supported by the software we need to install.


Any ideas on how I can get Ubuntu 8.04 LTS to see Hard drives ?

Please help.

thanx

EJI

---

### Post by EJI on 2009-09-17
Tried reinstalling 8.04 LTS 64bit Server edition.
Still not able to detect hard disks to complete install.

Both hard drives are detected when checking BIOS.

---

### Post by bombcar on 2009-09-17
I have the same motherboard; so far it looks like the kernel included with 8.04 does not support the chipset.

The kernel is 2.6.24-24 so I'm looking further into it.

---

### Post by RJARRRPCGP on 2009-09-17
Looks like you're gonna be required to install Jaunty Jackalope. (or Intrepid Ibex)

Likely, because the motherboard and chipset are newer than Hardy Heron.

---

### Post by EJI on 2009-09-21
[@RJARRRPCGP I have considered that option, but unfortunately, the software, Plesk 8.6 only supports Ubuntu 8.04  .. ]("http://ubuntuforums.org/member.php?u=28754")

Will see if I can figure something out.

regards

EJI

---

### Post by EJI on 2009-10-21
We aborted this mission.

Thanx for your help.

---

