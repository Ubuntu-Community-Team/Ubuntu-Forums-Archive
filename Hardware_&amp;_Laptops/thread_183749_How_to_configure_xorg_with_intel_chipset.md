---
title: "How to configure xorg with intel chipset?"
date: 2006-05-28
forum: Hardware &amp; Laptops
---

### Post by jsmidt on 2006-05-28
My laptop does not have a video card.  It runs a Intel 945G Express Chipset which has a built in Intel Graphics Media Accelerator 950 which handles the graphics.  See:

[http://www.intel.com/products/chipsets/gma950/](http://www.intel.com/products/chipsets/gma950/)
[http://www.intel.com/support/chipsets/sb/CS-020683.htm](http://www.intel.com/support/chipsets/sb/CS-020683.htm)

I can download the driver for the Intel 945G Express Chipset but I was then wondering how I configure xorg.conf to use the driver.  I'm new at the configuring hardware side of things.

---

### Post by araz on 2006-05-28
Have you tried "sudo dpkg-reconfigure -phigh xserver-xorg"?

---

