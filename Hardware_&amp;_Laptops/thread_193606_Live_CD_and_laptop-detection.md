---
title: "Live CD and laptop-detection"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by wasteed on 2006-06-10
I've got a brand spanking new Toshiba Tecra M5 laptop which I fully intend to run as a   Linux only laptop -but only if I'm convinced it will be well supported. So I tried the 6.06 live CD. Everything boots up fine but there are 2 problems: 

#1 there is no indication that the live CD thinks it is running on a laptop - the file /var/run/laptop-mode-state doesn't exist, and there is no choice to hibernate or suspend at the logout window. Should I expect the live CD to detect a laptop, or is this only possible from the 6.06 alternative CD? I also want to find out how it handles ACPI power management, before I install.

#2 The M5 has a duo Centrino core. The live CD only detects 1 processor however
(as indicated by cat /proc/cpuinfo). Is there any way to tell the live CD it is running on a smp machine?  Or, as other posts have said, you can only do this post-install by installing the i686-smp kernel.

Once I can be sure these are solvable I will go ahead with the install...

---

### Post by blackjack6.21.91 on 2006-06-10
The live CD detected my laptop, but I'm pretty sure that you can tell your system you've got a laptop after install.

And yeah.  Just install the smp kernel after your install and both processors should be used.

Fish and chips,
blackjack

---

