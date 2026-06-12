---
title: "compaq c700 xorg.conf help request"
date: 2008-07-27
forum: Hardware
---

### Post by stevieray1 on 2008-07-27
hello,

im running Ubuntu 8.04 on a compaq presario C700. Im having trouble figuring out how to run a dual screen (extended screen) with an LG 715Z.

My xorg.conf does not seem to detect anything so it looks like i am running all default values:

* * *
[...]
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection
* * *

lspci | grep VGA gives me

***

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

***

it runs as a twin screen ok if i clone the screen but really looks terrible. Any help greatly appreciated...

---

### Post by stevieray1 on 2008-07-29
what a pain in the a** - i spent a LONg time on this and i think i finally figured it out (although there is some weird redraw stuff but its passable for now)

To get dual heads working (extended display) you cannot apparently use xinerama with the intel driver anymore. Take all the crap out of your xorg.conf file ([https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/212231](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/212231)) and make sure that on your default screen you have a Virtual entry big enough to hold both your screen sizes (i.e. Virtual 2048 1024).

reboot and then run xrandr:

xrandr --output VGA --right-of LVDS


That worked for me. 

Some one needs to tell this guy to update his stuff as this is what everyone points to for ubuntu dual head installs: ([http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)) 

cheers- - hope this saved someone some time i spent a cool 8 hours on this one...but at least i didnt have to throw out ubuntu but it was close ;-)

i figured this out by reading this post and the two posts it points to:
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/212231](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/212231)

---

