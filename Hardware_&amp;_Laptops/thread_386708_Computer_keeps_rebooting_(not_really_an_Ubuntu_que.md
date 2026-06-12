---
title: "Computer keeps rebooting (not really an Ubuntu question, but...)"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by Ian Maxwell on 2007-03-17
Last night, when I went to my PC, the CD drive was being accessed over and over again, and nothing was appearing on the screen, and no keystroke seemed to do anything. When I turned off the computer and turned it back on, this happened again---the computer kept accessing the CD drive and not starting up. When I unhooked the CD drive and tried again, the computer got a little farther into the boot process (as far as a few lines into the linux kernel startup or less) and then reset. This is the case even if I open the BIOS setup at startup; within less than a minute the system will reboot.

I don't really know that much about fixing computers (I can replace bad components myself, but I don't know enough to guess which components are bad). My first guess is the power supply, solely because it seems to make sense *a priori,* but on doing some reading I see that faulty memory can also be responsible for random reboots.

I wasn't doing anything special with my computer in the past few days, but we *did* have a series of blackouts the other day (and I don't have a UPS at the moment).

Any clues?

---

### Post by gray-squirrel on 2007-03-17
It could also be possible that there is an overheating problem, either inside the case in general or the CPU and/or memory chips are overheated.

---

### Post by dentonlt on 2007-03-17
Echo the 'probably overheating'.  Perhaps your fans bit the dust?

If you think it's the memory/chips, try running Memtest.  You can get that from many places as a bootable CD iso.  The Ubuntu Live CD has Memtest on it, too.

Good luck!

---

### Post by berylmichael on 2007-03-17
It is possible that this is a power issue. This is indicative of when the cables are connected the wrong way (reversed). When you said that you unhooked the CD drive, did you mean that you disconnected both the data and the power connections? If not, try that to see if that helps.

Michael

---

### Post by Ian Maxwell on 2007-03-18
Well, this problem is solved. My ten-year-old PC had a perfectly functional (if no-name) PSU that is now powering my current system. I guess that was the problem.

Thanks for the suggestions, all.

---

