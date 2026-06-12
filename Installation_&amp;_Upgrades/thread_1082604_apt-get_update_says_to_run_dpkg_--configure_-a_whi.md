---
title: "apt-get update says to run dpkg --configure -a which fails"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by busstation16 on 2009-02-28
ubuntu stopped running updates even from the command line, and told me to run "dpkg --configure -a"  this failed too, nothing i red online fixed it.  It turned out my /boot partition (at 32 mb) was too small to unpack whatever update it was trying to get.  I booted the live CD, and expanded the partition to ~100mb, and the update worked fine.

Just thought id share.

:guitar:

---

### Post by taurus on 2009-02-28
Remove the older kernels (in synaptic) from your machine to free up space in /boot since you have a small partition for /boot.

---

