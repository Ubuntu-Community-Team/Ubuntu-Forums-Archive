---
title: "Can't get Vid card to work."
date: 2008-08-07
forum: Hardware
---

### Post by Trey5498 on 2008-08-07
Stats of PC:

Intel Processor with 2 gig of ram 
Vid Card:  Geforce 8500 GT
dual Dell 22 inch monitors
Ubuntu 8.04

I have this PC dual booted with Suse 11 As I am working on linux programming, these two OS will help to cover most Distros.  I can not get the video card to function correctly.  I installed the recommended driver and it did not work, it just sat there at 500X500 (something like that).  Would not go bigger and would not display the colors correctly.  And the NVidia download driver (from NVidia site) complained about the kernal and then stopped.  I also can not get the dual monitors to extend.  It just clones and I get double display.

---

### Post by phidia on 2008-08-07
To install from the nvidia site via their run file you need to have the correct kernel headers (uname -r) and the build-essential package installed.
Maybe you have build essential if you're coding. Some people here like to recommend installing nvidia through [envy]("http://albertomilone.com/nvidia_scripts1.html"). 
I don't know though if it will work-there are reports of the 8 & 9 series cards being stuck in low rez mode, but there are fixes too. I will have to find the thread that had success with that. [Here]("http://ubuntuforums.org/showthread.php?t=881314") it is.

---

### Post by Trey5498 on 2008-08-07
So How do I solve the issue with the graphix card and the monitors?

---

### Post by phidia on 2008-08-07
> **Trey5498 said:**
> So How do I solve the issue with the graphix card and the monitors?

Did you check out those links I inserted?

---

### Post by Trey5498 on 2008-08-07
ninja edit lol

---

