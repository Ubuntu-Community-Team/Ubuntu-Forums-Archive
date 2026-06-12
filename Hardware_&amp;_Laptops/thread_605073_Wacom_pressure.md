---
title: "Wacom pressure"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by petepan on 2007-11-06
Hi!

I have a working Wacom with pressure sensitivity and all.. byt i need to know... where are all the 1024 levels of different pressure? i can only find 4 in gimp and that sux big time tbh! If that is al that is available to the Linux community than someone should get working on new drivers or something..

well. just need to know.

/petter

---

### Post by henke_a on 2007-11-09
Hi.
You could try to add the option "PressCurve" to your /etc/X11/xorg.conf  to change the pressure curve.
Something like this:
```
Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "USB"  "on"
    Option         "TwinView"    "horizontal"
    Option         "ScreenNo" "0"
    Option         "PressCurve" "50,0,100,50"
EndSection
```
Those values works great for me with my Intuos 2 tablet.
For more options type "**man wacom**" in the terminal.
If you don't have an entry similar to this your tablet probably isn't properly configured.

---

