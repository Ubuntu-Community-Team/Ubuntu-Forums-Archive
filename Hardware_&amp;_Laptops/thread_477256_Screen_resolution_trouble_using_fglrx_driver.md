---
title: "Screen resolution trouble using fglrx driver"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by NS2-10 on 2007-06-18
I have a ACER Aspire 5670 Laptop (1.6 Ghz Duo Core, 1GB RAM, widescreen) and a ATI X1400 Radeon Graphics Card.

In accordance to what I read in the forums I installed the restricted fglrx drivers for my card and all went well. I can currently use Beryl nicely and I have full 3D support.

The problem is that the maximum screen resolution I can choose is 1024x768, whereas my computer surely must be able to run a much higher res.

What should I do to?

PS If this helps, when I run fglrx info I get the following info:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

---

### Post by Brent Bice on 2007-06-19
I'm seeing the same problem on a Dell D610 laptop. I've tried massaging /etc/X11/xorg.conf manually to include additional resolutions but that didn't help.  I also tried running:
aticonfig --resolution=0,1280x1024,1024x768
but that didn't do it either.  I found that if I ran this first the above no longer gave me an error message:
aticonfig --initial --force --input=/etc/X11/xorg.conf

 But even after I used aticonfig --initial --force to create a brand new xorg.conf file and then ran the aticonfig --resolution command I *still* can't set a resolution higher than 1024x768. In my case, fglrxinfo yields:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Any ideas on how to get some higher resolutions enabled anyone?

---

### Post by un1x01d on 2007-06-20
you can just edit the /etc/X11/xorg.conf file and add under Depth
Modes "1280x800"

and restart X. and everything should work.

---

