---
title: "Problem Mobility Radeon 9700 - Acer Travelmate 4002 - Ubuntu Intrepid 8.10"
date: 2009-01-12
forum: Hardware
---

### Post by CoolBurn on 2009-01-12
Hi all!

Recently i had installed Ubuntu 8.10 Intrepid in my Acer TravelMate 4002WLmi Laptop.

- Kernel Installed -> 2.6.28 (Recompiled by myself)
- Xorg version -> 7.4
- Driver working at now: xorg-video-ati-radeon (modprobe radeon)
- Agp module loaded.

Here's my big problem:

I can't install fglrx driver for my ATI Mobility Radeon 9700 / 9800.

If I try to install ATI privative driver: Downloaded from ATI.COM, the installation finally succerful but when I run: fglrxinfo i get "Segmentation Fault".

There's a command for list ATI devices detected (fglrxinfo -l maybe?) And the response is:   No ATI Card Found.

I can run glxgears with 300 fps average.

--> In Ubuntu Hoary i got 1300 fps. ( with fglrx loaded OK!)

Some help will be appreciated T.T

Thanks in advance! :)

---

