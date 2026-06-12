---
title: "Problem with Wacom tablet on 8.10"
date: 2008-11-23
forum: Hardware
---

### Post by michaelGR on 2008-11-23
Hello All,
I have an old Wacom Intuos 2 tablet with a serial connection. It used to work fine on 8.04 and below.
When 8.10 came out I did a clean install and lost my previous xorg.conf (stupid, I know).
I've just gotten around to configuring it to get my tablet working again. I found out though, that now I can't get to the rightmost side of my screen using the tablet (the mouse works normally). When I get the stylus to the rightmost side of the tablet, the cursor is still 135 pixels (I checked with Gimp) away from the right edge of the screen. 

here is the relevant xorg.conf segment:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"
  Option        "Type"          "stylus"
  Option	"TVResolution"	"1280x1024,1024x768"
  Option	"Twinview"	"horizontal"
  Option	"ScreenNo"	"0"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"
  Option        "Type"          "eraser"
  Option	"TVResolution"	"1280x1024,1024x768"
  Option	"Twinview"	"horizontal"
  Option	"ScreenNo"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"
  Option        "Type"          "cursor"
  Option	"TVResolution"	"1280x1024,1024x768"
  Option	"Twinview"	"horizontal"
  Option	"ScreenNo"	"0"
EndSection

```

Other relevant data:
I have an Nvidia 7600GT card, an 1280x104 LCD monitor and a TV set arranged in a twinview setup. I'm using the default wacom driver that came with 8.10.
Thanks in advance for any help with this.

---

