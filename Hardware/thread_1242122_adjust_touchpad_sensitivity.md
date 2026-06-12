---
title: "adjust touchpad sensitivity"
date: 2009-08-16
forum: Hardware
---

### Post by yellowzelo on 2009-08-16
Hi,

I need to increase the sensitivity of my touchpad. Here is my current xorg.conf:

```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```I already tried to insert these lines to xorg.conf, but no change:

```
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/psaux"
    Option        "Protocol" "auto-dev"
    Option        "MinSpeed" "0.1"
    Option        "MaxSpeed" "0.3"
    Option        "AccelFactor" "0.017"
    Option "MaxTapTime" "0"
EndSection

```I have a laptop Compal jhl90 and I am running Kubuntu 8.10.

Thanks for help!

---

### Post by RedSingularity on 2009-08-16
Did you adjust the mouse settings located in System>Preferences>Mouse.  Acceleration plays a big part in the sensitivity as well.

---

### Post by yellowzelo on 2009-08-17
Yes, but I have a USB mouse too and I want to have a different sensitivity/acceleration setting for my touchpad and my mouse - changing settings located in System>Preferences>Mouse changes it for both - USB mouse and touchpad

Changing sensitivity settings everytime I plug or unplug USB mouse is not a good solution
And I also want do disable touchpad when typing on keyboard and thats not possible through KDE settings.

---

### Post by yellowzelo on 2009-08-17
Nobody can help me?

---

