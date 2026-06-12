---
title: "Intel 82845G i810/i915 driver issues"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by lysdexia on 2006-11-03
Hi,

I've recently installed Ubuntu on a friend's laptop, and am having issues with the graphics driver.

The graphics chipset on the machine is an Intel 82845G chipset, and is currently using the i810 driver.

The problem is that I can't seem to get any resolution above 640x480 to work. Further, if I shutdown X, I can't seem to restart it even with a low resolution.

If the resolution is above 640x480, on startup the screen is simply blank.

I have tried solving this problem by following suggestions from some unofficial Edgy Eft guide, which suggested installing the i915 driver. 

I did this, but although lsmod shows the i915 module as being present, when I use it in xorg.conf, the Xorg.0.log file shows that the module was not found.

Any suggestions?

Thanks

Chris

---

### Post by jerrylamos on 2006-11-06
(your username cracks me up!)

Best I could get on my IBM NetVista with the Intel 82845G/i810 was 640x480 until tonight, when I found a fix in another post (where?).  Their, and my, Bios setting for shared video ram was 1024KB.  When changed to 8192KB, the max, the problems vanished, Edgy CDLive runs great, and resolution is 1024x768 like I wanted.
Cheers, jerry

---

### Post by Bols on 2006-11-12
When using the i915 module you have to set the driver to i810 in your xorg.conf.

---

### Post by nolagirl05 on 2006-12-17
> **jerrylamos said:**
> (your username cracks me up!)

Best I could get on my IBM NetVista with the Intel 82845G/i810 was 640x480 until tonight, when I found a fix in another post (where?).  Their, and my, Bios setting for shared video ram was 1024KB.  When changed to 8192KB, the max, the problems vanished, Edgy CDLive runs great, and resolution is 1024x768 like I wanted.
Cheers, jerry

I am having this same problem...can you provide details about how to fix this?  Thanks!

---

