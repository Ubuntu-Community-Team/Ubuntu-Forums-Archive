---
title: "touchpad on acer stop working"
date: 2009-04-23
forum: Hardware
---

### Post by koco on 2009-04-23
Hi there, i'm pretty new in linux and i have instaled ubuntu lates bistro on acer aspire 7730 and touchpad plus numkeys was working (it's 17" so got num as on desktop keybord) but after while it stops working.
got [FONT=Courier New, monospace][SIZE=2]**xorg.conf empty try all think's like [https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig) and so on and wont work at all shmconfig look's as off.added this lines to xorg.conf**[/SIZE][/FONT][INDENT] 
Section “InputDevice”
 Identifier      “Synaptics Touchpad”
 Driver          “synaptics”
 Option          “SendCoreEvents”        “true”
 Option          “Device”                “/dev/psaux”
 Option          “Protocol”              “auto-dev”
 Option          “HorizScrollDelta”      “0&#8243;
 EndSection
 [/INDENT]and add one more option to the bottom above “EndSection”
  
Option          “SHMConfig”             “on”
and restarted xserver and still nothing
last thing:[INDENT] 
Section “InputDevice”
 Identifier      “Synaptics Touchpad”
 Driver          “synaptics”
 Option          “SendCoreEvents”        “true”
 Option          “Device”                “/dev/psaux”
 Option          “Protocol”              “auto-dev”
 Option          “HorizScrollDelta”      “0&#8243;
 EndSection
 [/INDENT]and add one more option to the bottom above “EndSection”
  
Option          “SHMConfig”             “on”
 please if there is way how to set it up again i'll be happy
thank's lot for ubuntu

---

