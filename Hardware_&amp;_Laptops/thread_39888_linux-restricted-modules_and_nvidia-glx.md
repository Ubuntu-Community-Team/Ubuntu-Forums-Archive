---
title: "linux-restricted-modules and nvidia-glx"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by pkoufalas on 2005-06-06
G'day all, I've installed Ubuntu 5.04 to my Toshiba Satellite P20 laptop (dual P4) from a DVD that came with a magazine. It didn't recognise my LCD widescreen, but it did exit cleanly from gdm. Having earlier installed Knoppix 3.6 on the same laptop, I was able to modify xorg.conf to add the relevant ModeLine for the 17" WXGA LCD screen, and gdm restarted without problems with 1440x900 resolution.

But, I'm not sure how to go from using the free nv driver for the laptop's GeForce FX Go5200 to using the proprietary nvidia driver. For the Knoppix 3.6 installation I built the nvidia driver using nvidia's package (an earlier version of it). I was going to do that again but noticed that Ubuntu 5.04 comes with the nvidia kernel driver + common files. So I changed xorg.conf to use the nvidia driver instead of nv, but was surprised to note that it couldn't find the nvidia driver. I tried adding a ModulePath but that didn't help, tried loading the kernel module at bootup (modules.conf) but that didn't help either. Looking at this forum, it seems that nvidia-glx is necessary. I noticed that the linux-restricted package didn't install any nvidia modules to X11R6/

Can someone explain why nvidia-glx is needed, how it differs from the free glx and the proprietary nvidia kernel driver, and if it is necessary rather than optional for using the proprietary nvidia driver, why it wasn't included in linux-restricted-modules?

My apologies if the answer is obvious, and for probably knowing but forgetting the answer in the first place!

Cheers,
Paul.

---

### Post by pkoufalas on 2005-06-06
Found some answers at [http://ubuntuforums.org/archive/index.php/t-12823.html](http://ubuntuforums.org/archive/index.php/t-12823.html)

---

