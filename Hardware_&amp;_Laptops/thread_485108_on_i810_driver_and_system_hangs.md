---
title: "? on i810 driver and system hangs"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by eroica on 2007-06-26
hello,
Have been running Feisty and have been having these annoying crashes w/o anything in logs showing up. Most of the time it seems to be when screen saver has kicked in and screen will not come back on. I have to do a hard reset. It happens at least once or twice a day. I was wondering if it might be the video driver. I currently have the xserver-xorg-video-i810 driver installed. Can someone tell me if the xserver-xorg-video-intel driver would be any better (xorg.conf shows me using Intel Corporation 82810E DC-133 CGC chip controller). I cant find anything about what this driver is supposed to be used for. I was also wondering if a kernel upgrade might solve it. Can anyone tell me how one goes about upgrading the kernel in Ubuntu. thanx .....

---

### Post by walkerk on 2007-06-26
Not sure about your system but the first thing I did was replace the i810 driver with the xserver-xorg-video-intel driver.. works much better on my system..

---

### Post by dabl on 2007-06-26
I had much better luck with the xserver-xorg-video-intel on a new e-machines PC.  That's one data point for you.

---

### Post by eroica on 2007-06-27
and to update to the xserver-xorg-video-intel driver is it just install it from synaptic? Any other manual changes needed to xorg.conf etc....

---

