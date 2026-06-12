---
title: "external display resolution problem on ibm r50e laptop"
date: 2009-07-15
forum: Hardware
---

### Post by enes guler on 2009-07-15
i have a fresh ubuntu user and just installed 9.04. everything is fine except my external lcd display. for the last 2 hours i have been searching for a solution but no luck at all...

ubuntu recognized that the external display is NEC 17" LCD monitor. also i see there is the 1280*1024 option in display settings. but when select it and click apply, screen goes mad and stuck on the top left 1/4 of monitor. i can get rid of this either restarting or using xrandr (without seeing anything).

another point: i have disabled the laptop display and no help. actually, there is no difference its on or off.  all i need is getting 1280*1024 on external display.

here is the xorg.conf content: 

> Section "Device"
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




thanks.

---

### Post by GoldenSun on 2009-07-15
just something simple here.
try turning off and turn back on the external display.  Sometimes they just screw up, or atleast my cheap one does.  

Also make sure you have most up-to-date driver for gpu.  If you have compiz on, dl a compiz switch to turn it off and see if that works.

---

### Post by enes guler on 2009-07-15
thanks for the reply. here is answers:

> turning off and turn back on the external display.  Sometimes they just screw up, or atleast my cheap one does.  

it didnt work for me at all :)


> Also make sure you have most up-to-date driver for gpu. 

how do i do this? i have executed a terminal command (while looking for a solution) to update intel video things but i get "its up to date".


> If you have compiz on, dl a compiz switch to turn it off and see if that works.

i do not have any idea on this. its a naked installation. 

after installation, i only installed apache&php&mysql. and they are ntohing to with display.

---

### Post by enes guler on 2009-07-17
i see that there is no hope...

---

