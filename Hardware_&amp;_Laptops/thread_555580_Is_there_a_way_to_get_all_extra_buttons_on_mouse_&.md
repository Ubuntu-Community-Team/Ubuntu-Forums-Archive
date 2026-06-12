---
title: "Is there a way to get all extra buttons on mouse &amp; keyboard working?"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by Uber Nooblett on 2007-09-20
Hey guys I have a mouse and keyboard with loads of buttons I'd really like to make use of (especially the volume buttons!) any way to do this please?

Specs

Product Name: Genius Ergo 525 - mouse
Device Type: Mouse
Dimensions (WxDxH): 7.9 cm x 12.7 cm x 4 cm
Weight: 140 g
Connectivity Technology: Wired - PS/2, USB
Movement Detection Technology: Laser
Buttons Qty: 8
Movement Resolution: 2000 dpi
Features: Scrolling wheel (4-way), switchable resolution

lots of the buttons on my keyboard work, but some don't:

Hot keys   36
Input device
Connectivity technology   Wired
Mouse included   N
Interface   USB, PS/2
Keyboard layout   QWERTY
Scroll wheel   Y
Technical details
Keyboard function keys   8
Colour
Colour of product   Black/Dark Blue


Many thanks in advance :)

currently my mouse reads:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

```

and keyboard reads:

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection
```

---

### Post by linuxwizard on 2007-09-20
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)


[https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

---

