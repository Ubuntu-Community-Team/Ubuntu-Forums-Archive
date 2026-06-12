---
title: "Graphics card stops computer booting to BIOS"
date: 2009-03-27
forum: Hardware
---

### Post by Drone022 on 2009-03-27
Hey,

I've been using this computer for about 4 years now but the other day when I restarted it the computer wouldnt boot correctly, it couldnt even reach the BIOS stage.

After messing around inside for a while (removing each drive one at a time, resetting CMOS etc.), I took out my graphics card (Nvidia Geforce 6200 Turbocache) and it seemed to work fine again. It managed to boot to GRUB but when I tried to boot ubuntu it failed and I was left with a black screen. I reset my x config with xfix and things seem to be alright now. Actually, ubuntu is coping better with the loss of my graphics card than windows xp is. So im now using the motherboards onboard graphics.

What could have gone wrong with my graphics card, motherboard or powersupply that would cause my computer to not even reach BIOS when booting? Putting my graphics card back in still causes the same problem. I fixed the ubunutu problem I had by taking it out but I'm curious as to why this is happening. I cant seem to find a decent answer through google.

Any help/info is appreciated.

Specs: 4 year old HP pavilion
Processor: AMD Athlon 64 Processor 3700+
Motherboard: ATI IXP 400 (i think)
Graphics: Nvidia Geforce 6200 turbocache
RAM: 1GB DDR398 (199MHz)
HD: 300GB SATA
OS: Ubuntu 8.10/Windows XP Dual Boot

---

### Post by norwoods on 2009-03-27
do you have a display on each video output?  maybe you bios is showing up on an output with no display.
this is something you setup in bios.

---

### Post by Drone022 on 2009-03-27
Pretty sure I had my display on the right output, I've had to switch it to the mobo's output now the GeForce card is gone.

When I switched on my computer the PSU and CPU fans started at full speed, they usually do this initially for about a second but this time they didnt stop and the computer couldnt continue booting.

---

### Post by markbuntu on 2009-03-27
4 years...the bios battery could be dead so it can't save any changes.

---

### Post by Drone022 on 2009-03-28
> 4 years...the bios battery could be dead so it can't save any changes. 

BIOS battery seems to be fine, changes i make to the BIOS settings save ok. Problem is when i stick in my graphics card and the computer cant even reach BIOS.

---

### Post by markbuntu on 2009-03-28
Can you put the card in a different slot?

---

### Post by Delta28 on 2009-03-28
are you sure your hitting the right button for BIOS to come up?

---

### Post by Dr Small on 2009-03-28
It sounds like your video card is bad (try it in another system to be sure) or the PCI card slot is bad.

---

### Post by Drone022 on 2009-08-05
> It sounds like your video card is bad (try it in another system to be sure) or the PCI card slot is bad.

Yeah, my video card was bad by the way. K-Ray-zee.

---

