---
title: "Impossible to disable trackpad tapping"
date: 2008-08-22
forum: Hardware
---

### Post by lucis on 2008-08-22
I'm having a ton of trouble with my touchpad on Intrepid. I would like to disable once and for all the irritating tapping feature but can't seem to achieve that.

Gsynaptics / synclient won't work because they both report SHMConfig isn't enabled, which it is. Here's the relevant portion of my xorg.conf:


 Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
        Option          "SHMConfig"             "on"
        Option          "SHMConfig"             "true"
        Option          "TapButton"              "0"
EndSection

But anything I put in this section seems to not have any effect. :confused:

---

