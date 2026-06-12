---
title: "Best driver for nVidia GeForce 8600GT?"
date: 2014-09-03
forum: Hardware
---

### Post by Al1000 on 2014-09-03
MB including sound: Asus M2N32SLi deluxe
RAM: 3GB
CPU: AMD Athlon 4200 Dual Core
Graphics: nVidia GeForce 8600GT
OS: Kubuntu 14.04 32 bit

Hi,

All of the above hardware is around 10 years old, apart from a 2GB RAM stick that I recently fitted when an old 1GB stick stopped working. I am currently using the ''nVidia binary driver - version 331.38 from nVidia-331 (Recommended Driver)'' and haven't had any problems with it.

I'm not much of a gamer but I recently installed FlightGear, and while it works ok it's not very snappy. So I searched the internet for other drivers and found this:

[http://www.nvidia.co.uk/object/linux_display_ia32_100.14.09.html](http://www.nvidia.co.uk/object/linux_display_ia32_100.14.09.html)

What I am wondering is, is it worth trying this to see if it works better? Installing it seems to involve exiting Xserver, and I'm not sure if I am risking not being able to access the GUI if I install this and it doesn't work, or if it would be easy enough to revert to the driver I'm currently using.

I realise that the best gains to be had would be by upgrading the hardware, but when I do that I will probably replace all of what I have listed above and upgrade to a 64 bit OS as well, and I am keen to get the best out of what I have for the meantime.

Any advice much appreciated.

---

### Post by Vladlenin5000 on 2014-09-03
No, I think it isn't worth to try a different driver. 

331.38 is the recommended version and it should just work. 
The instructions you linked are for manually installing the driver, using a script from nvidia, instead of using the version in the repositories. The only reason people might have to go this route is to install a newer version than the one found in the official repos but even for that cases using a PPA is preferable.
Needless to say, newer driver versions should be tested only when: a) a particular program, namely a game, is know to work better with such version and/or b) you have bleeding edge hardware so new that the 'stable' driver doesn't support it hence the need for a bleeding edge version of the driver as well.

Your hardware won't benefit from a newer driver version.

---

### Post by Yellow Pasque on 2014-09-03
The 100.14.09 driver you linked to is ancient and won't even build on modern/supported versions of Ubuntu. Dead end there...

The 340.xx driver series is the last that will support the 8x00 series cards, but I doubt it will give you any noticeable performance boost over the 331.xx driver that's already packaged with Ubuntu. It didn't make my 8400GS noticeably faster anyway...

---

### Post by Al1000 on 2014-09-04
Many thanks for the info.

I'll stick with the driver I'm using in that case.

---

