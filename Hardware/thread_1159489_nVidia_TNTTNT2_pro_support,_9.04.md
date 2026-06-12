---
title: "nVidia TNT/TNT2 pro support, 9.04"
date: 2009-05-14
forum: Hardware
---

### Post by Snow Keld on 2009-05-14
> nVidia “legacy” video support
The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

alright, my graphics card used nVidia TNT/TNT2 pro driver on 8.04

i never bothered with 8.10, but i want to upgrade now.

i have made an installation in another partition of 9.04 to try and get my graphics card working before i make the complete transition.


so about this quote i found about the 9.04 release means that i can use a driver, but it wont be the same one???

but no 3d acceleration means what? cuz i want to be able to play game still :(

i'll be getting a new comp pretty soon, but till then if its an easy fix i'd like to use 9.04 (but with my graphics card)


ANY help will be very much appreciated, you guys are awesome :D

---

### Post by terrox on 2009-06-24
ubuntu 9.04 uses Xorg 1.6.0 
TNT2 needs Nvidia legacy 71.86.xx drivers
Nvidia Legacy 71.86.10 is not compatible with Xorg 1.6.0

As far as I know it is impossible to get 3D acceleration with your TNT2 in Ubuntu 8.10 or 9.04 right now. And there is no word on if it will ever be compatible and it has been over 6 months.

---

### Post by terrox on 2009-06-27
71.86.11 is out but not sure if it is a fix. [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

