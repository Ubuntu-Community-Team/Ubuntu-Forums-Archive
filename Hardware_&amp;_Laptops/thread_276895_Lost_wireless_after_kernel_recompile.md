---
title: "Lost wireless after kernel recompile"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by brottman on 2006-10-13
Ok my laptop wireless was working GREAT with the restricted modules removed and just the 2.6.17 kernel that comes with Ubuntu Edgy. I did a straight copy of the .config in /boot to use for compiling 2.6.18, but when I boot 2.6.18, I no longer have wireless. My wireless card does not show up under either ifconfig or the network manager. What gives? 

What is different between the 2.6.17 kernel that comes with Ubuntu and the 2.6.18 kernel I compile myself?? It should be the exact same configuration. Grrrr.

My wireless in this laptop is a ipw2200.

---

### Post by brottman on 2006-10-14
Such a helpful forum! The answer was simple really, and it only took me an entire day to find such a simple answer.
/sarcasm off

I had to copy the ipw2200* firmware files from /lib/firmware/linux-2.17.10-generic  to  /lib/firmware  so they would load up with the new kernel.

---

### Post by Frogger on 2006-10-14
Are you running a native driver or ndiswrapper?

When I did a kernel recompile I had to recompile ndiswrapper also.

---

