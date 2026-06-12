---
title: "ati accelerated driver"
date: 2008-08-06
forum: Hardware
---

### Post by Jujumasta on 2008-08-06
i enabled this under admin>hardware, but after restarting the laptop hangs with a black screen. control-alt-f1 works, but f7 does not. is there a way i can disable the accelerated driver (from terminal?)

---

### Post by overdrank on 2008-08-06
> **Jujumasta said:**
> i enabled this under admin>hardware, but after restarting the laptop hangs with a black screen. control-alt-f1 works, but f7 does not. is there a way i can disable the accelerated driver (from terminal?)

Hi and have you tried booting to recovery mode and use the xfix option?

---

### Post by Vorian Grey on 2008-08-06
It may be your card is not compatible with the newest ATI driver. Mine is not, so I use EnvyNG (found in Synaptic) and it downloads the right driver for my card. 

I've found the easiest way to back out of this is to run the Live CD and open Nautilus file manager. Go to the partition that you have Ubuntu installed onto, and go to/etc/x11 and open xorg.conf. Find the line that has "fglrx" and change it to vesa and then restart.

---

