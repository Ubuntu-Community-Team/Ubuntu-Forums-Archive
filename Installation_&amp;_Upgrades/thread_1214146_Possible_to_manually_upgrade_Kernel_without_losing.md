---
title: "Possible to manually upgrade Kernel without losing access to restricted drivers?"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by fifth_rune on 2009-07-15
Am currently running Jaunty with Intel video card. Did an update to version 2.6.30 of the kernel and noticed significant improvements in the video/CPU issues I had been having. However, doing this caused me to lose access to restricted drivers including my wireless card. Is there a way to update the kernel and keep access to this driver OR (less preferable) a way to install the driver manually once I update?

---

### Post by triplesick on 2009-09-06
me too, bumpity bump!  plz answer guyz lol!

---

### Post by falconindy on 2009-09-06
Follow directions on this blog.

[http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid-using-git/](http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid-using-git/)

 Note that compiling a kernel after 2.6.28-15.49 requires some modifications to the process listed. If you dig through the comments (near the end) you'll see that someone has posted the necessary modifications (denoted as compiling for karmic).

---

### Post by pdoes on 2009-09-08
Thanks for the plug falconindy but I believe in this case the OP has compiled a vanilla kernel, 2.6.30 is not yet in the official repo for Jaunty.

---

### Post by pdoes on 2009-09-08
To help me figure it out can you tell me one driver that is restricted and you want in your vanilla kernel?

---

