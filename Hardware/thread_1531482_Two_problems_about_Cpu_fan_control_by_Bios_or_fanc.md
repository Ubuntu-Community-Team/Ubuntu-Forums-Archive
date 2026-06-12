---
title: "Two problems about Cpu fan control by Bios or fancontrol app"
date: 2010-07-15
forum: Hardware
---

### Post by mark.altern on 2010-07-15
Hey guys, the personal laptop I am using is the thinkpad t400, as in my signature. I have very strange 2 problems with CPU fan controls. First one:

Before Ubuntu 10.04, I was using 9.10 and the cpu fancontrol is working OK, without me installing any fancontrol software. I guess the BIOS control it through acpi.  It works perfectly. 

Now after I did a clean install of 10.04, I found the BIOS doesn't do it correctly: since the start-up cpu fan speed is about 1886rmp, when the cpu temp goes to 55c, it cramp up to 2600rmp, then after that even the cpu have been idle for a long while and temp drop to 37c, the fan wouldn't slow down, but keep running 2600rmp. 

Interestingly, the other exact same laptop, which I didn't do clean install of 10.04 but did an upgrade from 9.10 to 10.04, doesn't suffer from this problem. The Cpu fan works normally, goes up and slow down!

My second problems: So my solution is to use fancontrol software which is installed by default by ubuntu and I only need a proper /etc/fancontrol file. But strange thing is that, form time to time, the fancontrol will not start up in a new boot. In 90% of time, fancontrol starts up as expected, but randomly at about 10% times, it will not start up. Why is that? 

Any ideas on either problems are extremely welcomed. 
Thanks, guys.

---

### Post by mark.altern on 2010-07-15
any thinkpad users? do you have similar problems?

---

