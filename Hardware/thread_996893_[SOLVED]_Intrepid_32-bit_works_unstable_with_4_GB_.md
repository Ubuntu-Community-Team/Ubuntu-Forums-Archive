---
title: "[SOLVED] Intrepid 32-bit works unstable with 4 GB of RAM"
date: 2008-11-29
forum: Hardware
---

### Post by Elegorod on 2008-11-29
Intrepid 32-bit workes normally with 2 GB of RAM. When I bought and installed 4 GB (2x2 GB), Ubuntu boots and shows 3.5 GB in System monitor. But system often freezes, so the only way is to press reset button (even Ctrl-Alt-F1 doesn't work). Windows XP 32-bit starts to boot and goes to reboot (doesn't shows the list of users)
Current kernel is 2.6.27-10-generic.
How to make Ubuntu work stable? 3.5 GB instead of 4 isn't a main problem.

---

### Post by Skripka on 2008-11-29
Is your system stable under XP?  There is such a thing as defective RAM--especially if you run RAM that is not a major brand.

EDIT: Also, figure out which DIMM is only being read as 1.5GB and remove it, and try running--also switching DIMMs in their slots.  Check your voltages and timings too in BIOS-there are lots of things that can go askew in changing RAM.

---

### Post by sdennie on 2008-11-29
That does sound like bad RAM.  For 32-bit, it's normal to only see 3.5GB when using 4GB (there are ways around that) but, it shouldn't cause instability unless the RAM is bad or the BIOS isn't supporting that much RAM properly.  I would hit Escape on the grub menu and run the memory test option for a few hours to see what it says.

---

### Post by Elegorod on 2008-11-29
BIOS shows full 4 Gb, memtest86 also. Motherboard supports up to 8 Gb RAM.

---

### Post by Elegorod on 2008-12-07
The problem was that I inserted RAM badly, not to the end, and there was bad contact.
Now everything is working, memtest86 is passed, though Windows and Ubuntu show 3.5 Gb only.

---

