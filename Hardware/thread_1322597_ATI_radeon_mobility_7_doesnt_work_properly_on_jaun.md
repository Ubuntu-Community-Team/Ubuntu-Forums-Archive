---
title: "ATI radeon mobility 7 doesnt work properly on jaunty"
date: 2009-11-11
forum: Hardware
---

### Post by Nevermore on 2009-11-11
Hello
I installed the latest jaunty on my laptop, a panasonic cf73 with ati radeon mobility 7.
The screen shows a gritch in the upper right corner (looks like a notification window which is not been displayed) with is persistent and sometime covers the windows.
Compiz can't start and glxinfo shows no glx option available error and exits, glxgears is not starting as well.
It seems i have no acceleration but radeon module is loaded.
Any suggestion will be welcome (in old ubuntu i had to manually edit xorg.conf in order to add some parameters for compiz, now xorg.conf is gone and i cant do much).
Thanks

---

### Post by rich97 on 2009-11-11
ATI pulled support for the Radeon mobility drivers for some obscure reason.

The version of Mesa that comes with 9.04 does support the drivers, but not very well. Try upgrading Mesa or use Karmic. Works well for me! (Radeon 200m)

---

### Post by Nevermore on 2009-11-11
Sorry, im already using karmic!
and it doesnt work properly :(

---

### Post by Nevermore on 2009-11-11
solved by adding xorg unstable repository

---

### Post by spacecheck on 2009-11-12
x

---

### Post by spacecheck on 2009-11-12
> **Nevermore said:**
> Hello
I installed the latest jaunty on my laptop, a panasonic cf73 with ati radeon mobility 7.
The screen shows a gritch in the upper right corner (looks like a notification window which is not been displayed) with is persistent and sometime covers the windows.
Compiz can't start and glxinfo shows no glx option available error and exits, glxgears is not starting as well.
It seems i have no acceleration but radeon module is loaded.
Any suggestion will be welcome (in old ubuntu i had to manually edit xorg.conf in order to add some parameters for compiz, now xorg.conf is gone and i cant do much).
Thanks

Try this: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001/comments/13](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001/comments/13)
Adding that "EXA"entry solved the problem for me. I also raised my AGP aperture to equal the card memory, in the same section, with:
Option		"AGPSize"	"128"<b /> .
 You may also want to read these:
[https://bugs.launchpad.net/ubuntu/+bug/466066/comments/5](https://bugs.launchpad.net/ubuntu/+bug/466066/comments/5) 
[https://bugs.launchpad.net/ubuntu/+bug/466066/comments/6](https://bugs.launchpad.net/ubuntu/+bug/466066/comments/6)
 Good luck!
Ciao

---

### Post by Tony Ricena on 2009-11-12
> **Nevermore said:**
> solved by adding xorg unstable repository

did you find this under synaptic or something else?  I am having problems with my ATI Radeon 4650 HD and this might be what I need to solve some of my problems

---

