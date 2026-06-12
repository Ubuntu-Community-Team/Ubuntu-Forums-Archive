---
title: "Nvidia Driver makes X server crash?"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by Jroller90 on 2007-04-23
I've tried a lot of different ways to get this to work, but when I enable my Nvidia Driver in either the desktop effects or the restricted driver manager the x server crashes upon a reboot. When this happens i use "dpkg-reconfigure xserver-xorg" set my driver to either "nv" or "vesa" because those are the only two that will take me to my desktop again. I installed the beta Nvidia driver with nvidia's interface thing and it was working for a little bit, i got Beryl running and everything was great until i rebooted... the x server crashed again. Please help!!!!

I have a Nvidia Geforce FX 5200, Pentium 4 3.06 GHz, 1 GB.

---

### Post by frogotronic on 2007-04-23
you need the nvidia-glx driver, NOT the nvidia-glx-new driver

---

### Post by Jroller90 on 2007-04-23
Wow, well i just reinstalled the Nvidia 9755 driver, made a few changes according to [http://ubuntuforums.org/showthread.php?t=420258&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=420258&highlight=install+nvidia) and now i'm up and running!

but thanks for the reply!

---

