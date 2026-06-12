---
title: "Direct Rendering problems with Intel Graphics Card"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by kev717 on 2009-04-24
Today I decided to do a fresh install of Ubuntu 9.04.  I am using an intel I810 graphics card, and running GLX Gears on the live CD showed that I was getting around 200 frames per second.  After installing, I was still getting 200 frames per second, however whenever I tried to run any openGL application, it would be blurry or would simply freeze the system.  Adding 
```
Option "DRI" "off"
``` 
to my Xorg configuration file seems to have fixed the freezing problem, but now I'm only getting 64 frames per second, and I can't even run an openGL application with that, it's just too slow.  Is there any way that I can enable the direct rendering and not have my computer freeze every time I open a fullscreen 3D application (like sauerbraten)?

---

### Post by kev717 on 2009-04-25
*bump*

---

### Post by kev717 on 2009-04-25
*bump*

Looking through my log files, I notice that moments before the system freezes, there is an error message:
```
*ERROR* unknown parameter 6
```
Just in case that helps... could this maybe be a bug in the intel display package?

*edit*
Related to [bug 353049]("https://lists.ubuntu.com/archives/universe-bugs/2009-April/069936.html") maybe?

---

### Post by jerrylamos on 2009-04-25
Well, depending on how adventurous you are.

Jaunty comes with linux image 2.6.28-11

There is a later image available 2.6.30-rc3

which gets back toward Intrepid performance with my two intel machines.

I downloaded it from:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

I wind up with grub boot options for rc3 followed by the boot option for 2.6.28-11 so I can run either one.

Cheers, Jerry

---

