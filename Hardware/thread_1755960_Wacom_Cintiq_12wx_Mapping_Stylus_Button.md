---
title: "Wacom Cintiq 12wx Mapping Stylus Button"
date: 2011-05-11
forum: Hardware
---

### Post by sysiphus80 on 2011-05-11
Hello! 

I can't use my stylus buttons of my cintiq 12wx since i've upgraded to 11.04. 

in 10.10 right and middle mouse button were mapped to the side buttons of my stylus. now  nothing is mapped to the side buttons and i can't manage to reconstruct it like it was in 10.10. 

already tried to play around with 

xsetwacom set "Wacom Cintiq 12WX stylus" Button

but without luck. any suggestions?

thanx for your help in advance

roland

---

### Post by sysiphus80 on 2011-05-11
just found out when i touch the tablet with the stylus and at the same time press the side button it works. 
but in 10.10 it was possible to use the side button of the stylus without directly touching the tablet with the stylus. 

any ideas?

---

### Post by Favux on 2011-05-11
Hi sysiphus80,

With the default Natty xf86-input-wacom-0.10.11 the Cintiq is conflated with a tablet PC, since they both have LCD's, so the driver is using the tablet PC default *TPCButton "on"* for your Cintiq.  Use this xsetwacom command:
```
xsetwacom set "device name" TabletPCButton "off"
```
using the device name for stylus you get from *xinput list* in a terminal.  That should give you the expected tablet hover mode.  Or add an Option to the usb snippet in the 50-wacomconf below the wacom driver line:
```
Option "TPCButton" "off"
```
It's been fixed in a later version of xf86-input-wacom 0.11.0.

---

### Post by sysiphus80 on 2011-05-13
Thank you, [Favux]("http://ubuntuforums.org/member.php?u=699990")! Works with the xsetwacom command :).

---

