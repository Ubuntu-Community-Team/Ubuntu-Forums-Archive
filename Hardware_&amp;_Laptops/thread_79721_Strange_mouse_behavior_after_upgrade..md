---
title: "Strange mouse behavior after upgrade."
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by K2712 on 2005-10-20
Just upgraded to breezy and everything is great so far with the following exception:  I was simply surfing the internet when my laptop mouse froze(both the touchpad and the button).  I could still navigate using the keyboard but that is obviously not desired.  When I plugged in a USB mouse, I could control the cursor again, but only with the USB mouse.  I've searched the forums and seen others with similar problems, but no solutions that helped mine.  Here is the applicable section of my xorg.conf:

Section "InputDevice"
           Identifier         "Configured Mouse"
           Driver             "mouse"
           Option            "CorePointer"
           Option            "Device"                       "/dev/input/mice"
           Option            "Protocol"                     "ImPS/2"
           Option            "Emulate3Buttons"          "true"
           Option            "ZAxisMapping"              "4 5"
EndSection

Section "InputDevice"
           Identifier        "Synaptics Touchpad"
           Driver            "synaptics"
           Option           "SendCoreEvents"           "true"
           Option           "Device"                        "/dev/psaux"
           Option           "Protocol"                      "auto-dev"
           Option           "HorizScrollDelta"            "0"
EndSection

Any help would be appreciated.

---

