---
title: "Touchpad goes crazy with WiFi"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by Jaffas on 2006-06-03
Hi,

We have just installed Ubuntu Dapper on a new HP dv5116nr laptop. The touchpad worked 'out of the box' and we recently got the wireless internet connection working using the bcm43xx module. The problem is, whenever we start Network Manager or Wifi-Radar, the touchpad becomes un-usable. It jerks and bounces all over the screen, clicking and right-clicking willy-nilly! Does anyone have a solution?

Jaffas

---

### Post by dutchman25 on 2006-08-28
I am having the exact same problem you described.  I think it has something to do with the bcm43xx module and synaptics driver not sharing nicely the interrupts.  I have searched and searched but have not been able to find anything that works.

Have you tried using ndiswrapper for wireless instead of bcm43xx?  I wish I could, but I am having a hard time getting ndiswrapper to work on my 64-bit Broadcom 4319 card.

---

