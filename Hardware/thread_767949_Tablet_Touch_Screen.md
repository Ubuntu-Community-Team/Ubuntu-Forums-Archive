---
title: "Tablet Touch Screen"
date: 2008-04-26
forum: Hardware
---

### Post by wwbdd on 2008-04-26
I just installed ubuntu 8.04 on my lenovo x61 tablet, and I have almost everything working.  I have the touchscreen version of this machine, so it should respond to either the pen input or the finger touch, but as of right now, it only responds to the pen.  What do I need to do to remedy this?

xorg.conf
```

Section "InputDevice"
    Identifier  "stylus"
    Driver      "wacom"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "stylus"
    Option      "PressCurve"    "50,0,100,50"
    Option      "Threshold" "60"
    Option      "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
    Identifier  "eraser"
    Driver      "wacom"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "eraser"
    Option      "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
    Identifier  "cursor"
    Driver      "wacom"
    Option      "Device"    "/dev/input/wacom"
    Option      "Type"      "cursor"
    Option      "Mode"      "relative"
    Option      "ForceDevice"   "ISDV4"
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "Default Screen"
    InputDevice "Synaptics Touchpad"
    InputDevice "stylus"
    InputDevice "eraser"
    InputDevice "cursor"
EndSection

```

---

### Post by schmolch on 2008-04-26
There is nothing you can do, the Touchscreen is not supported.

---

### Post by NiklasV on 2008-04-26
ThinkWiki appears to have a solution, but the guide is written for Fedora 8 and links to rpms, it also links to source though so you may be able to compile.
[http://www.thinkwiki.org/wiki/Installing_Fedora_8_(Werewolf)_on_an_X61_Tablet#Getting_multitouch_support_with_you_X61_tablet](http://www.thinkwiki.org/wiki/Installing_Fedora_8_(Werewolf)_on_an_X61_Tablet#Getting_multitouch_support_with_you_X61_tablet)

---

