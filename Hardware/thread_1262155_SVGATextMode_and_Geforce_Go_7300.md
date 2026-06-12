---
title: "SVGATextMode and Geforce Go 7300"
date: 2009-09-09
forum: Hardware
---

### Post by sdunatunga on 2009-09-09
Hi All,

I am trying to get this program working with my laptop's videocard but I almost always end up with a garbled display. I know something is wrong in the configuration but I have no idea where to find the requested information (the clocks line).

The only reason I started messing around with this is because I compiled the nvidiafb driver into the kernel, not knowing it would disable the 3D nvidia driver (doh!), but the text mode with nvidiafb enabled was SUPER nice (seemed to be 132x43, although I didn't measure it). Since I spend half my time in the console (outside of X), I wanted this mode, but with the vesafb driver I can only do 80x60 VGA max OR 1024x768 VESA. I have 1024x768 set up right now (with vga=791) but it clearly is not the same mode nvidiafb set up.

Thanks,
sdunatunga

---

