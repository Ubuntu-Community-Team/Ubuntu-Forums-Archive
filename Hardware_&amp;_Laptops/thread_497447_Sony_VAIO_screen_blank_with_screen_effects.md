---
title: "Sony VAIO screen blank with screen effects"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by dawsonj on 2007-07-10
When I turn on screen effects and it has to use restricted drivers the screen is blank on reboot however plugging in an external monitor revealed it is sending the output to it rather than the internal screen.

Hardware info says I have a NV17 [GeForce4 420 Go]

THe SONY is a PCG-FR700

Ubuntu Feisty Fawn with all updates.

---

### Post by goo3r on 2007-07-13
I am having the same problem with my geforce4 go. I really have been struggling with this.

---

### Post by goo3r on 2007-07-13
I figured mine out hopefully this helps you too. It turns out you have to edit the xorg.conf file. Then add Option "UseDisplayDevice" "DPF" after Depthdefault in the Section "Screen" I hope this helps!

---

### Post by dawsonj on 2007-07-16
thanks I tried this and it did not work unfortunately

where did you get that information from?
perhaps my particular laptop requires a different option?
thanks again

---

