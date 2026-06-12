---
title: "shutdown while compiling the kernel"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by diantel on 2005-11-22
I have an Acer Aspire 1524, AMD 64 with Breezy 32 bits.

Every time I want to compile the kernel my computer shows a message that  maximum temperature has reached and shutdowns. 

The computer is really hot but the fan seems to work well. I don't know why it is not able to compile.

I've tried to compile the kernel in text mode also to reduce the CPU usage and works partially because it doesn't finish the compilation. 

Also in the boot process shows a message that cpu scaling is not supported. I don't know what I did. I can't change the CPU speed, is always at maximum.

I think my computer should be able to compile at maximum speed. I want to know if my computer is failing or if it is a configuration problem.


It is normal? Anyone happened something similar? 


P.D. sorry for my english :)

---

### Post by maher on 2005-11-22
the same thing happened to me  on my ACER Aspire 1522 wlmi. you may try to contact their support service, because this is not linux related (at least it was not, in my case), not to mention other oddities. I kept mine for 5 months then sold it out.
now i have a Fujitsu Siemens laptop (m7405) and i see the difference.

---

### Post by diantel on 2005-11-22
Thanks for the answer, I've found the same on the internet. 

It is a hardware problem not linux. :(

---

### Post by blackpaw on 2005-11-23
I had the same, had to throttle the speed of my laptop to 75% (or even lower) to get a kernel compiled. I also put it on higher "feet" to get cool air from below on it.

well, notebooks are not designed to work 100% all the time, it seems. ;)


andreas

---

### Post by diantel on 2005-11-23
Finally I was able to compile the kernel. I had a problem with powernowd ( I suppose). I choosed userspace and automatically the computer slows down the CPU and not reach too much temperature. 

The speed during the compilation now is not at 2.2 GHz all the time, sometimes is at 1.8 or 2 Ghz. 

I agree you, blackpaw, notebooks (at least this model) are not design to be all the time at his maximum speed 2.2 Ghz but works fine with userspace. Now it is at 800 Mhz and the fan is silent.

---

