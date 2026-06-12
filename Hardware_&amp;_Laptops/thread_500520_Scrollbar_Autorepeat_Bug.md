---
title: "Scrollbar Autorepeat Bug???"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by salmankhilji on 2007-07-14
If I single-click on the red area in the attached image just briefly, and let the left button go, the scrollbar will act as if I had held the left button down and will continue scrolling.  It happens intermittently---I'd say about 85% of my clicks act if they "got stuck".

I have a SONY laptop VGN-FS550 running Feisty.  I have tapping off on my touchpad.  I am running qsynaptics and here is the info from xorg.conf:

Section "InputDevice"
        Identifier      "Synaptics TouchPad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "VertScrollDelta"       "100"
        Option          "MinSpeed"              "0.30"
        Option          "MaxSpeed"              "0.70"
        Option          "AccelFactor"           "0.003"
        Option          "ClickTime"             "100"
        Option          "SHMConfig"             "on"
EndSection

---

