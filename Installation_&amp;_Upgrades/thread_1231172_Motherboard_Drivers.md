---
title: "Motherboard Drivers"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by david35580 on 2009-08-04
Hi Folks,
I'm a newbie, but thought this might be best in 'Installation and Upgrades' as it involves a new build.
I'm about to put together my first Linux only machine and want to load it with 9.04 X64.
It will be around an ASUS M3N WS Motherboard, Phenom 9650 CPU and a 500GB SATA HDD. I have 4GB or RAM also.

My question is about installing the drivers for the motherboard and HDD. The DVD drive will be IDE still and will presumably work straight off the bat, but I've previously (Socket A board) had to install SATA drivers via a floppy because Windows XP didn't seem to support them (or something like that).

Provided the HDD spins (I'm assuming a modern board won't need a set of floppy SATA drivers to work it), I then intend to install Ubuntu and then the ASUS DVD with it's proprietory Motherboard drivers on it.
Will there be any conflicts if I install Ubuntu and then the ASUS drivers? Or will Ubuntu drive everything adequately (I'm assuming not)?

SO: just incase you can't dig the actual questions out of my lengthy and tortuous prose:
1. Do you think the SATA HDD will work straight off? (not a Linux question I know, but I'm depending on your generous souls),
2. Will there be any problems with 9.04 and the ASUS drivers? and 
3. Is that the correct way round to install things in this case?
Thank,
David

---

### Post by keplerspeed on 2009-08-04
I havnt seen any issues lately with SATA. My guess, it will work out of the box. The last machine I built, I didnt have to install any drivers, ubuntu drove it all.

---

### Post by kayvortex on 2009-08-04
The SATA disk should work fine; but unless the drivers provided by ASUS are for linux they will be useless. But, it's not normally a problem since Ubuntu will detect your hardware and use whatever drivers it has. In any case, what you'll probably find is that the ASUS disk will contain other programs that are not really needed (although, the the fact that it's on a DVD rather than a CD means it's worth looking to see exactly what's on it). 

I revamped my computer a few years back with virtually every part being new (ABIT motherboard, SATA disks, power supply, graphics card, RAM) and installing Ubuntu on it was no more problem than doing it on a pre-built system. The only thing you should do, as with all newly built systems is keep a check on temperatures and voltages etc. The ASUS DVD will likely contain a program that will do this, but it will also likely be a windows-only program; so, instead, you can use *gkrellm*, *hddtemp*, and *lm-sensors* in Ubuntu to do the same thing.

---

### Post by Mark Phelps on 2009-08-04
> **david35580 said:**
> ... I then intend to install Ubuntu and then the ASUS DVD with it's proprietory Motherboard drivers on it.
Will there be any conflicts if I install Ubuntu and then the ASUS drivers? Or will Ubuntu drive everything adequately (I'm assuming not)?
Unless ASUS has suddenly started providing Linux drivers and SW on their disks (which I doubt), you will not be able to install anything from the ASUS DVD.  All that stuff is intended for MS Windows, not GNU/Linux.

You would do best to boot from the X64 Ubuntu CD in LiveCD mode and confirm that it detects your hard drive and all other hardware devices before you attempt an install.

---

### Post by david35580 on 2009-08-04
Thanks everyone.
Looks like I'm in for an interesting saturday.
David

---

