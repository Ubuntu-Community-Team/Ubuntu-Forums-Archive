---
title: "Quick Question about Kernel Upgrades"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by SteveONCSU on 2009-08-13
Quick one, I've made a number of enhancements to my system.  When the kernel is upgraded, will I loose any of this?

---

### Post by Revolutionary101 on 2009-08-13
Most if not all of your upgrades (if they are programs settings, desktop apperance) will stay the same.

---

### Post by Rambetter on 2009-08-13
What kinds of enhancements did you make?
If you patched your kernel manually then yes you will lost those when you use the package system to upgrade your kernel.
Otherwise, for example if you installed lots of software either by using the packages system or by compiling it yourself, you will not lose the changes nor will your software break.

The only thing that has broken for me in the past when doing a kernel upgrade is something like an nvidia driver, but if you're using the package system to install your nvidia kernel (instead of compiling it yourself) this should not break.

---

### Post by SteveONCSU on 2009-08-13
I'm talking specifically kernel patches.  So for example, I just got the HDAPS sensor working on my thinkpad.

---

