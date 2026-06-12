---
title: "DualScreen PCI/AGP"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by n8mensch on 2005-07-04
hi there, 

i've got a few problems getting my two gfx cards running.
My GFX Config so far:

Matrox Millenium (PCI) with a Dell Monitor 
Nvidia card (AGP) with a Belinea Monitor

both are working fine singel, my question is: how do i get them working 
in dualscreen mode ? i know that it is possible, because i've had it once
running on my old debian system, but the xorg.conf looks very different 
comparing to my old XF86config-4.

can anybody help me ?

thnx :)

---

### Post by netrattler on 2005-07-04
Here is a link on how to setup Xinerama it was written for xfree86 but will work for xorg with no problems, I've used it myself until I switched to twinview. Only problem with Xinerama is that you only get video acceleration on one screen. If your Nvidia card had dual video outputs I would then take the Matrox card out and run twinview because that will give you acceleration on both monitors.

Xinerama
[http://docs.linux.com/article.pl?sid=03/10/05/025207&tid=](http://docs.linux.com/article.pl?sid=03/10/05/025207&tid=)

Joe

---

