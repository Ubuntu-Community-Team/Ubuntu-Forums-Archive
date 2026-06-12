---
title: "How to tweak Laptop color setings"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by khalido on 2007-07-29
I recently bought a basic Acer laptop, an Aspire 5570Z.

It has the Intel i945 graphics chipset. Everything works fine* with Ubuntu 7.04, but the colors are a bit washed out. I installed the i915 drivers, and am running at the right resolution and color depth, but can't see any way to tweak the color settings. I.e the same laptop running windows, i can go to the display settings and change the color profile. Is there a way to do the same thing in linux?

* had to struggle mightily to get the atheros wireless to work

---

### Post by NilsE on 2007-07-29
Try changing the theme.  It is under the system menu

---

### Post by luispa on 2007-07-31
There's an interesting utility called gammapage.py. Type this in the command line:
gammapage.py

If you don't have it installed you should type:
apt-get install gammapage 
or
apt-get install gammapage.py

I hope this help you.

---

