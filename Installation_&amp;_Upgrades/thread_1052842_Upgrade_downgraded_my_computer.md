---
title: "Upgrade downgraded my computer"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by MayorBobster on 2009-01-28
Hi.  I recently put a computer together.  I installed Ubuntu Gutsy on it because its what I had on CD at hand.  A few days later, downloaded Ibex-64 because Gutsy (32 bit) could not access all of my system memory.  The CD install went really well, but when I ran update manager, one of the 322 updates killed X windows and networking.  I could not get X to re-start because it said I needed kernel sources not available.  So I re-installed Ibex from CD and built a 2.6.28 kernel.  It started and ran very well.  Everything worked well (networking, X windows, etc.).  But there was the big nasty red arrow from update manager wanting to wreck havoc on my system again.  I hoped I could avoid the network issues by de-selecting anything that looked like it would touch the network, but after the upgrade, I am once again back to DOS 5 (no graphical user interface, no network).  I went into /etc/network/interfaces and found:
auto lo
iface lo inet loopback
(and nothing else).
...and if I add
auto eth0
iface eth0 inet dhcp
...and then run /etc/init.d/networking restart, I get
socket: address family not supported by protocol (yadda yadda).
It complains that I don't have networking in my kernel (but it sure worked for the update, and prior to the update, and the kernel I build is just as bad as the stock Ubuntu one since it did exactly the same thing at this point, and I also moved 80 GB of data from an old computer to this one with that kernel (all prior to update).  So the question is: how do I get my system back?  I don't want to re-install, only to have update manager desperate to kill my system again, and I need the custom kernel for some hardware not in the Ubuntu kernel (I also don't want to keep running off the live CD).  My hardware:  Intel X58 chipset, Intel Core i7 processor@ 2.66 GHz.  12GB (DDR3) ram.  Networking is integrated onto the motherboard (Asus P6T deluxe), provided by two Marvell Yukon 88E8056 controllers (there are two lan ports).  Graphics are provided by an Nvidia GT 3850.  It was originally an ATI card, but it went back to the store because it couldn't keep video coming to the monitor for more than 5 minutes (and no, not a heat issue), and I've also had to flash my new Seagate SATA 500GB disks so they don't brick.  All I wanted was a new good-working computer...  Anyway, thanks in advance for any advice.
MayorBobster

---

### Post by MayorBobster on 2009-02-08
OK.  After a lot of research, I found that this problem occurs occasionally on various distributions of Linux.  The problem is real.  No X windows and no networking.  The problem: FATAL: binfmt_misc not found.  Now I had support (as a module) for binfmt_misc in the kernel I built (I don't know if the stock Ubuntu kernel does or not), but having it as a module will not keep this problem from occuring (it crashed my machine with the stock ubuntu ibex kernel just as nicely as it did with my kernel).  I am building a new kernel with support compiled into the kernel.  I will add dmesg and kern.log files to this so folk can at least be warned.:o

---

