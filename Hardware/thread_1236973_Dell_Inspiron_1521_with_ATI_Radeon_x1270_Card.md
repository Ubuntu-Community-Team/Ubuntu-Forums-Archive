---
title: "Dell Inspiron 1521 with ATI Radeon x1270 Card"
date: 2009-08-10
forum: Hardware
---

### Post by tom.swartz07 on 2009-08-10
Hi all,

I have a rather simple question.

I have been using Ubuntu for several months now, and am thoroughly enjoying every minute of it. Just recently I was poking around with Blender, which I used to have on my Vista installation. For some reason of another, the window for blender is INCREDIBLY choppy and leaves artifacts all over the screen. I also found that I could not use the s-video out port on my system. Upon further investigation, I searched my X11 xorg.conf file and found that for some strange reason, there is no driver for my ATI card listed. It simply says:

 	Code:
 	Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection 
I googled the problem and found that many early builds of Jaunty, 9.04 did not have any support for the ATI cards such as mine. 

My question is; does the final version of 9.04 have support for my ATI Mobility Radeon X1270 card? If so, how do I configure xorg to use it?
Ultimately, My goal is to regain use of the s-video port on the back of my computer to attach a secondary monitor. Until I figure out how to add the drivers for the card, no dice.

Any help would be greatly appreciated!
Thanks a ton!

---

### Post by esalnoj on 2009-08-10
I'm running same graphics card. Is your system up to date?

It appears you are missing your resolution settings in /etc/X11/xorg.conf

I have not installed the open source or propietary driver yet.

---

