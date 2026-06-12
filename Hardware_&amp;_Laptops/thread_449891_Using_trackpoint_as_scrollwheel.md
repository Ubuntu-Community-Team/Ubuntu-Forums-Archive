---
title: "Using trackpoint as scrollwheel"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by janlugt on 2007-05-20
I've got a both a touchpad and a trackpoint on my Dell Latitude D610. I'm used to using my touchpad for mouse-movement and using the trackpoint for scrolling (the windows driver had a setting for this). I've figured some things out, this is the resulting trackpoint section in my xorg.conf:
```
Section "InputDevice"
        Identifier      "TrackPoint"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Buttons"               "3"
        Option          "ButtonMapping"         "6 1 7"
        Option          "Emulate3Buttons"       "false"
        Option         "EmulateWheel"          "on"
        Option         "EmulateWheelButton"    "10"
        Option          "YAxisMapping"          "4 5"
EndSection
```

The buttons directly beneath the keyboard (the ones belonging to the trackpoint) are mapped as buttons 6 and 7, so I can use them as back/forward-buttons in firefox. I could also map one as a EmulateWheelButton, so the trackpoint acts as a scroll wheel when the mapped button is pressed.

What I want to achieve is permanent EmulateWheel, it should be on whether one of the buttons is pressed or not. The problem is that it has to be mapped to a button.

Is there a way to enable EmulateWheel without pressing a button? Or can I set a virtual button on my mouse (like button 10) to always be pressed (maybe by sending a ButtonPressed-event to the Xserver)?

---

