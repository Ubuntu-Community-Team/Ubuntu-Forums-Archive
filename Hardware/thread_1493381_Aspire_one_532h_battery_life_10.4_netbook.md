---
title: "Aspire one 532h battery life 10.4 netbook"
date: 2010-05-25
forum: Hardware
---

### Post by jfaberna on 2010-05-25
I have a new Aspire One 532h-2588 netbook. It came with a hard drive with Win7, but I pulled that drive and installed an 80GB Intel SSD. I'd expect that to really improve my battery life.

However, after testing with Ubuntu 10.4 Netbook (which works great BTW), I found that if I close the lid to go into suspend, when I'm not using the netbook, it gets confused and reports that I'm out of battery on the 4th or 5th resume. The battery is not the problem because, if I set the power management to never turn anything off, it will run doing nothing for 6 hours with the WiFi on. The scenario below causes the problem:
1. remove A/C charger and boot
2. check email browse web for 2 min. close lid
3. LED on left turns from solid blue to blinking orange every 4 secs. 
4. wait a few hours.
5. open lid, press power button.
6. repeat 2-5.

after 5-6 hours when I come out of suspend, the critical battery alert comes on and the system shuts down.

The total powered up times is maybe 15 minutes. the sleep total is 5-6 hours.

Either the suspend function draws as much power as full on or the battery testing software has a bug.

Any ideas?

6. repeat

---

### Post by exchaoordo on 2010-05-26
This seems of a piece with the problem I and others are having with the Aspire One 532's interaction with the battery monitor.  There are various behaviors, but are all versions of: the battery monitor fluctuates wildly from full to empty causing hibernation or similar.  It's not the battery because it works fine in other OS's.

---

### Post by jfaberna on 2010-05-26
Okay, this is good to know that I'm not alone. Win 7 has no issues with the critical battery alert until I'm really low on power. Hopefully this gets reported. I'm not sure of the method to do so.

---

### Post by jfaberna on 2011-01-06
This appears to be solved in the UNR 10.10

JIm A

---

