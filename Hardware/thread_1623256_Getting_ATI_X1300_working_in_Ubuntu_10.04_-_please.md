---
title: "Getting ATI X1300 working in Ubuntu 10.04 - please help!!"
date: 2010-11-16
forum: Hardware
---

### Post by Rev2010 on 2010-11-16
For the life of me I can't get the X1300 ATI chipset in a Lenovo T60 working in Ubuntu 10.04. I'm setting this up for a coworker and have tried so many different suggestions I've found via Google but nothing works. As a result, any program that relies on 3D graphics won't even fully launch (ie. Google Earth, Stellarium, etc). Everything else launches fine though.

Does anyone have any rock solid info on getting this older, non-supported, chipset working in Ubuntu 10.04?


Rev.

---

### Post by Fafler on 2010-11-16
I have a T60p, it's pretty much the same machine, but has a FireGL M56GL graphics chip instead. It's like the Radeon with more features and uses the same driver. I have tried everything. Alternative drivers, disabling kernel modesetting etc. and the best results i've got is 10.04 with the drivers from [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) is around 20 fps with the Doom III timedemo. It should be able to do 4 times that, when i compare to similar systems running Windows. Unfortunately xorg-edgers isn't compatible with 10.10. Now i'm stuck with 10.10, 7 fps in the timedemo and weird errors with the taskbar and notifications appearing on top of the OpenGL content in fullscreen.

---

### Post by Rev2010 on 2010-11-17
Thanks man, that made things much better! Still don't see a driver listed in the hardware panel but I guess that's cause it's not a proprietary driver? Doesn't matter though cause now the programs are all working.


Rev.

---

