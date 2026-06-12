---
title: "Backlight Won't turn on - Gateway!"
date: 2010-04-08
forum: Hardware
---

### Post by DBCD on 2010-04-08
Hey all

Ever since I installed Ubuntu 9.04 onto my Gateway MT3423 Laptop, I've been having issues with my backlight - namely, it works only sporadically. Interestingly enough it will nearly always turn on for a second just before the boot loader appears and also for a second if use the laptop key to use two monitors.

Any advice?

Thanks!

---

### Post by emanuel.b on 2010-04-08
Hi!

First of all, I'd plug it in to an external monitor, then check if you have all the restricted drivers. Which graphics card does your laptop have?

---

### Post by jflaker on 2010-04-08
Likely not due to Linux.

I've worked on Laptops as a benchtech and can tell you....if the light isn't lighting up, the backlight is likely bad.  The LCD backlight is always on, the light level is software controlled (BIOS) via key combination.

options:
-Find a place that fixes them and have it repaired (probably not worth it)
-Find a the same model laptop on ebay that is for parts only...cannibalize the LCD. (worth the time if you can find it on the cheap)
-Replace the laptop.  Walmart has an HP full sized laptop for $348 and a more powerful model for $528

---

### Post by DBCD on 2010-04-09
Hey Emanuel - mind telling me how to check for that? I don't even know what restricted drivers I need.... Also, I'm using an NVIDIA GeForce Go 6100 graphics card.

---

### Post by emanuel.b on 2010-04-09
> **DBCD said:**
> Hey Emanuel - mind telling me how to check for that? I don't even know what restricted drivers I need.... Also, I'm using an NVIDIA GeForce Go 6100 graphics card.

Don't mind at all! First you go to "System -> Administration -> Hardware Drivers" and see if there are any. If not, the next version of Ubuntu, 10.04, is supposed to have better support for NVIDIA drivers. So you could upgrade to the BETA now, or wait until the full version comes out at the end of the month...

---

