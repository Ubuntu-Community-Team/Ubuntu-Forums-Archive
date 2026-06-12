---
title: "Sony VAIO VGN-NS11M experience and problem solving"
date: 2008-11-14
forum: Hardware
---

### Post by chrispolderman on 2008-11-14
Hello there!

Just to post some experiences on the Sony VAIO VGN-NS11M. This laptop contains an T5800 processor, 3 MB of memory, 250G of HDD space and an Intel 4500MHD graphics processor.

This is a report on the only issue I encountered with the graphics card.

Installation went smoothly and gave me the "omg it works in one go!" sensation. Everything is detected automatically: webcam, wireless card, the works.

The graphics card supports all the gimmicks offered by compiz and works wonderful, EXCEPT for one thing:

Now and again the laptop seems to think there is a VGA screen attached to the system. This can be seen when using the [FONT="Fixedsys"]xrandr[/FONT] command. It will report a "VGA" output present (connected) in addition to the LVDS output.

<EDIT: Before you use this workaround, see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/147073](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/147073) which is (I think) similar.>

I do not know why this happens. To remedy this, I have created a script called "resetvga.sh" and placed this inside the /usr/bin directory. The /etc/X11/Xsession.d contains a snipped which calls this script. The content of the resetvga.sh script is:

[FONT="Fixedsys"]
#!/bin/sh
xrandr --output VGA --off
xrandr --output LVDS --mode 1280x800
[/FONT]

(ofcourse, the script should have "executable" flags!)

The content of the /etc/X11/Xsession.d/10ResetVGA snippet is:

[FONT="Fixedsys"]/usr/bin/resetvga.sh
[/FONT]

This caused the login script to still display in the wrong resolution, but as soon as you login: shazamm! no broken resolutions any more. This solution is not a permanent solution but until Xorg fixes this issue all is fine now.

The rest "just works" out of the box!

Just my response for anyone thinking about buying this laptop, and a solution for the ones having the 4500MHD chipset!

Chris

---

### Post by gwydionwaters on 2009-10-06
nice, thanks for the info. i am thinking of buying a vgn-ns110e/s which has the same video card. not sure about the wireless, i think it is atheros. i read it works i believe.

---

