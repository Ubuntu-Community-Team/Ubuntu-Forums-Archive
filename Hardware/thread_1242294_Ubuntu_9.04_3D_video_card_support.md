---
title: "Ubuntu 9.04 3D video card support"
date: 2009-08-17
forum: Hardware
---

### Post by tom.swartz07 on 2009-08-17
Hi all,

I have a rather simple question.

I have been using Ubuntu for several months now, and am thoroughly enjoying every minute of it. Just recently I was poking around with Blender, which I used to have on my Vista installation. For some reason of another, the window for blender is INCREDIBLY choppy and leaves artifacts all over the screen. Upon further investigation, I searched my X11 xorg.conf file and found that for some strange reason, there is no driver for my ATI card listed. It simply says:

 	Code:
 	Section "Device"
    Identifier    "Radeon X1200"
    Driver        "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Radeon X1200"
EndSection 
I googled the problem and found that many early builds of Jaunty, 9.04 did not have any support for the ATI cards such as mine. After some digging in the Ubuntu documentation, I uncovered that you should configure the file such as I have here, but, alas- I still do not have support for my card!

My question is; how do I configure xorg to use my card, and ultimately, another screen??
Ultimately, My goal is to regain use of the s-video port on the back of my computer to attach a secondary monitor. Until I figure out how to add the drivers for the card, no dice.

Any help would be greatly appreciated!
Thanks a ton!

---

