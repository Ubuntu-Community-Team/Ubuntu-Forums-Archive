---
title: "Configuring USB mouse in fglrxconfig"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by Granji on 2005-09-10
Okay, I'm starting to get pissed, i've already run throught his once before, and it worked fine, but I upgraded to xfree86 4.3.0, and re ran the fglrxconfig program in an attempt to get a 3d accelerated program to work. Upon reboot, I found that my mouse was no longer being recognized by X server, and because of this it won't allow to boot with my proper keyboard/mouse/video etc settings. The problem I'm having though, is that I'm not sure where ubuntu is mounting my mouse, so using the proper /dev point is plaguing me. The error that i'm getting is " Unable initialize core devices "  When I replace the XF86Config-4 file with an older Xorg backup, I'm able to load things fine, but I lose my resolution, which is the main reason I installed the propietary ATI drivers to being with. Thanks for your time and your help.

---

### Post by Granji on 2005-09-10
Oh, wait, I got it, instead of looking for the USB mount point, I just used /dev/input/mice...the symbolic link for pointer devices...ahhh stupid me, thats what lack of sleep does to you :P, thanks to anyone who was gonna help.

---

