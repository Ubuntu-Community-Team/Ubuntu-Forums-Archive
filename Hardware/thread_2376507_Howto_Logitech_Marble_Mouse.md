---
title: "Howto: Logitech Marble Mouse"
date: 2017-11-03
forum: Hardware
---

### Post by beerislife on 2017-11-03
I usually use the instructions here to get the scrollwheel working but with Kubuntu 17.10 they don't work:

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

 The solution I found was this:

sudo nano /usr/share/X11/xorg.conf.d/10-libinput.conf

and add:

Section "InputClass"
       Identifier      "Marble Mouse"
       MatchProduct    "Logitech USB Trackball"
       Driver          "libinput"
       Option          "ScrollMethod" "button"
       Option          "ScrollButton" "8"
	Option		"MiddleEmulation" "on"
EndSection

If that doesn't work, then try this:

sudo nano  /usr/share/X11/xorg.conf.d/10-evdev.conf

Add:

Section "InputClass"
       Identifier  "Marble Mouse"
       MatchProduct "Logitech USB Trackball"
       Option "EmulateWheel" "true"
       Option "EmulateWheelButton" "8"
       Option "XAxisMapping" "6 7"
       Option "Emulate3Buttons" "true"
EndSection

In either case, change 8 to 9 if you want to use the right button to  activate scroll on this line: Option "EmulateWheelButton" "8"

---

### Post by Richard-S on 2018-08-26
I added the following in Ubuntu 16.04, exactly the way beerislife suggested, and it worked like a charm. Perfect.

sudo nano  /usr/share/X11/xorg.conf.d/10-evdev.conf

Add:

Section "InputClass"
       Identifier  "Marble Mouse"
       MatchProduct "Logitech USB Trackball"
       Option "EmulateWheel" "true"
       Option "EmulateWheelButton" "8"
       Option "XAxisMapping" "6 7"
       Option "Emulate3Buttons" "true"
EndSection

Richard

---

