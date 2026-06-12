---
title: "blank screen on DELL Latitude D620"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by ntaylor0909 on 2007-05-07
I have Feisty running on a DELL Latitude D620. It has a Nvida video card. Feisty loaded great, and was running very well on it. I enabled the restricted drivers for the nvidia card, and then desktop effects. Everything was working fine until the Desktop cube stopped working. So I disabled the restricted Nvidia card driver and was going to re-enable the driver after a re-boot, but when I rebooted, I was able to log in, but after I logged in, I got a blank orange screen. it looks like the background for the splash screen. I get the same issue on bootup in recovery mode.

Any ideas?

---

### Post by mbeierl on 2007-05-07
Sounds like beryl is still trying to run, but the 3d acceleration is no longer there.  Try disabling beryl (maybe something like ```
chmod -x /usr/bin/beryl
``` would do the trick)

---

