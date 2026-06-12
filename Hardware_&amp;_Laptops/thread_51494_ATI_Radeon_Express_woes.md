---
title: "ATI Radeon Express woes"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by mortoray on 2005-07-24
On a motherboard with the ATI RS480/RX480 chipset (which for Video is a Radeon Express 200 chip), the (K)Ubuntu install will not configure a working system.  I'm working on an AMD64 system so perhaps it works better with the 32bit install.

The <xorg.cong> uses the "ati" driver, but upon entering X the system will lock up with several failure notices in the </var/log/Xorg.0.log>.  To fix this problem quickly one can add:
    Option   "noaccel"
directly beneath the driver line in the <xorg.conf>.  This of course isn't optimal, but everything does work then.

Alternately, what I ended up doing, was to download the newest Radeon Express drivers from ATI.  I used alien to convert the package and then dpk -force-all -i to install it (the force being needed to override a few Mesa files, probably an ignore option may be better, I'm not sure what impact I've had on the 3D/GL system yet)

Then I simply changed the Driver "Ati" to Driver "fglrx" in <xorg.conf> (removing "noaccel") and everything works (at least all that I tested now).

---

### Post by tbasten on 2005-07-24
Try 
```
fgl_gears
```

---

### Post by gymsmoke on 2006-03-30
My son has an ati express 200 and is having the same problem.  I looked up the ati drivers on the site, but there are 4 versions of the driver available for download.  Can you tell me which version you used for Ubuntu 5.10 ?

---

