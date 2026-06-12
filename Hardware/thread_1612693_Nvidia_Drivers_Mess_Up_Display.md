---
title: "Nvidia Drivers Mess Up Display"
date: 2010-11-03
forum: Hardware
---

### Post by Meaple on 2010-11-03
I know there have been many discussions about this topic but I CANNOT find the answer anywhere. I am running Ubuntu off a Toshiba Qosmio F20 laptop, it runs perfectly fine until I install the Nvidia drivers for it. The driver is GeForce Go 6600. The problem is when I install the driver,

1) When booting into normal mode, it returns an error, something like 'POWER_MODE: connection timed out'.

2) When I boot into recovery mode and load up into Ubuntu that way, it doesn't detect the BenQ FP731 external monitor.

I will say that I DO NOT have the built in monitor since it broke like a year ago so I took it off and I am only using the external monitor. I have tried to edit the xorg.conf file with no luck. Tried commands and no luck. I am starting to get frustrated so I am up for any solutions or ideas.

Here is the xorg.conf file backup, (I have uninstalled the drivers for now).

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
    Depth       24
    EndSubSection
EndSection
```

---

