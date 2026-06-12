---
title: "Intrepid Ibex clean install on 250GB hard drive"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by stubrownuk on 2009-03-24
Since I prefer to get things right first time, I would be very pleased if someone could give me clear instructionhs on how to do the following:
1. I have a Dell Latitude D800, in which I have just installed a new 250GB hard drive. (The old hard drive died.)
2. I recognise that the BIOS limit is 137GB.
3. Please advise how I install Intrepid Ibex from a live CD onto this blank 250GB drive so as to avoid e.g. GRUB errors 17 and 18.

I am operating away from my home country at the moment, so grateful for any kind soul willing to help.

---

### Post by davidshere on 2009-03-24
> **stubrownuk said:**
> Since I prefer to get things right first time, I would be very pleased if someone could give me clear instructionhs on how to do the following:
1. I have a Dell Latitude D800, in which I have just installed a new 250GB hard drive. (The old hard drive died.)
2. I recognise that the BIOS limit is 137GB.
3. Please advise how I install Intrepid Ibex from a live CD onto this blank 250GB drive so as to avoid e.g. GRUB errors 17 and 18.

I am operating away from my home country at the moment, so grateful for any kind soul willing to help.

Without reprogramming (flashing) your bios to accept a larger drive, you'd have to create a 137GB partition on the drive, and then a second partition for the rest of the drive.

My motherboard is ~8 years old, and I put a 250GB hard drive on it, with one 250GB partition, with no problems.

---

### Post by stubrownuk on 2009-06-29
I have now got Janty working on two computers (a Dell Latitude D800 and a Dell Latitude E6500), both with 250GB hard drives, using a 300MB boot partition at the start of the drive. Has been working a treat the last couple of months. Since this seems well documented elsewhere I won't elaborate, but if anyone would like more information, send me an email and I'll provide the details.

---

