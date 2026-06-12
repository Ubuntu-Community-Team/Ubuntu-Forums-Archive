---
title: "asus w3v and external monitor"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by jeremytaylor on 2007-02-06
Hi all, 
I know there are a million (approximately) posts about getting an external monitor, or more precisely a projector, to work with the vga out of a laptop but none seem to be working for me. 

I don't want anything fancy just a cloned desktop while i give a presentation, even if that means the display on my widescreen laptop has to be distorted.

I am using the default radeon drivers (please don't suggest switching to fglrx I'm enjoying my aiglx stuff too much). 

I have tried including 
Option "MonitorLayout" "LVDS, AUTO"
or
Option "MonitorLayout" "LVDS,CRT"
in my device section. With AUTO I get an unreliable signal which is highly corrupted on my external monitor. With CRT all looks to be going well but when I try to change the resolution so as to match the projector the gnome screen resolution app won't allow any changes and lists the refresh rate as -13000 or so (not quite that number but I can't remember what it was). 

Has anyone any advice?

Many thanks
Jeremy

---

