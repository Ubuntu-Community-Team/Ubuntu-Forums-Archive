---
title: "Old Toshiba Laptop resolution problem - trident"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by superzorro on 2007-10-22
Hello, I need some help, with a low resolution problem

I have an old Toshiba Satellite 2250xcds laptop. It has installed Xubuntu 7.04, however if I use the "trident" driver it shows up a fuzzy line in the bottom of the screen. This is fixed, if I use the "vesa" driver, however supposedly it gives me a 800x600 resolution, but when I compare it with the installed Windows, using the same background, and different pics I can see that it's really running in 600x480, the images are grainy. I've also change the depth, but it doesn't change much, only using 15 as default depth, gives better results but then, the colors aren't good.

Anyone can give some hints on this?

The screen part of my xorg.conf is:

> 
Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-40
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems Cyber 9525"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "800x600"
EndSubSection
EndSection


Hope someone can give me some advice.

---

### Post by overdrank on 2007-10-23
H and maybe this thread will help 
[http://ubuntuforums.org/showthread.php?t=572588&highlight=Trident+Microsystems+Cyber+9525&page=2](http://ubuntuforums.org/showthread.php?t=572588&highlight=Trident+Microsystems+Cyber+9525&page=2)
Good luck! :KS

---

### Post by superzorro on 2007-10-31
Hello,

Well I tried, the steps on that thread, but still have the same problem, one unusual thing, is that when i tried to change my resolution with the "menu" there are only two options "Default" and 640x480 if I choose 640x480 the image is reduced, but if I choose the Default option the image fills the screen (normally) however the resolution is the same as the 640x480. 
Even if I edit the xorg file, it won't show u, the 800x600 as an option. And the only way to not see all the "pixels" is to use a depth of 15. However with this depth the colors look very ugly.

I need some help with this.

---

