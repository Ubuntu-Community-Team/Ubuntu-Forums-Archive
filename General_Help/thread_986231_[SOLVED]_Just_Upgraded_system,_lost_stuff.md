---
title: "[SOLVED] Just Upgraded system, lost stuff"
date: 2008-11-18
forum: General Help
---

### Post by Forbees on 2008-11-18
i was away from home for a few days, came back and had about 250meg of upgrades to do

clicked the update button, had to restart

i no longer have graphic support, they said something about my card or driver, but it all worked fine b4 the upgrade

i got it running in low graphics mode right now

now AWN, no Compiz . . . . its horrible :(


how do i fix? i'm tempted to reinstall the kernal and see if that does it

---

### Post by ShadowWraith on 2008-11-18
Did you upgrade from Ubuntu 8.04 to 8.10? What are your machine's specifications, what graphics card are you using?

---

### Post by DieB on 2008-11-18
pls also tell your brand of graphic card (see > lspci in an terminal) and the kernel version (> uname -r in the terminal)

---

### Post by Forbees on 2008-11-18
> **ShadowWraith said:**
> Did you upgrade from Ubuntu 8.04 to 8.10? What are your machine's specifications, what graphics card are you using?

i was already on intrepid, that upgrade worked fine

this was just a normal "system out of date" upgrade thing

i'm using a ATI radon 2600pro (pciE) intrepid ibex . . . amd dual 3.0ghz, 2g ddr2 ram.

everything was working fine in intrepid until this newer upgrade

---

### Post by deadowl on 2008-11-18
I know that a lot of the times I am asked to use a proprietary driver that simply doesn't work.

You can check it out/try toggling in System->Administration->Hardware Drivers

---

### Post by DieB on 2008-11-19
For me it looks most like a kernel update. Pls go in synaptics and check in the chronic what exactly did get upgraded. if there were a new kernel install at that time too - we might just have found the problem.

---

### Post by Forbees on 2008-11-19
it's all good now

i had to reinstall windows to be able to play Left 4 Dead

KICK *** GAME

so that meant i had to re-compile the kernal to get grub back (symple live cd terminal install has never worked for me)

now everything works again

---

