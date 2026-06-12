---
title: "Dell D620 Touch Pad Help"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by MadModdr on 2007-07-01
I am running Ubuntu 7.04. I am trying to configure the touch pad to make the pointer acceleration a bit faster but when I goto System, Preferences, Mouse I can only change the settings for the trackpoint (this system has the trackpoint and a touch pad). How can I change the settings for the touchpad instead of the trackpoint?

---

### Post by linuxwizard on 2007-07-01
Is this what you are looking for

[https://help.ubuntu.com/community/Peripherals](https://help.ubuntu.com/community/Peripherals)

[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

---

### Post by MadModdr on 2007-07-01
I've actually installed and tried the Gsynaptics app. This app does allow for some customization of the settings for the touchpad but it does not allow me to change the speed of the pointer. The only setting I get that is even remotely close is touchpad sensitivity which doesn't seem to do much at all. I want to actually change pointer speed/acceleration.

---

### Post by erik_boi on 2007-07-05
This link --> [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620 ]("https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620") has a configuration that you can paste into your /etc/X11/xorg.conf and some other pointers for the d620. The notes say that it isn't needed for 7.04 but I have experienced otherwise, maybe I can't find the proper adjustments.

Here is the section
```
Section "InputDevice"
   Identifier   "Synaptics Touchpad"   # Don't change this from whatever value you have set already.
   Driver       "synaptics"
   Option       "SendCoreEvents"        "true"
   Option       "Device"                "/dev/psaux"
   Option       "Protocol"              "auto-dev"

   Option       "LeftEdge"              "130"
   Option       "RightEdge"             "840"
   Option       "TopEdge"               "130"
   Option       "BottomEdge"            "640"
   Option       "FingerLow"             "14"
   Option       "FingerHigh"            "15"
   Option       "MaxTapTime"            "180"
   Option       "MaxTapMove"            "110"
   Option       "ClickTime"             "0"
   Option       "MaxDoubleTapTime"      "100"
   Option       "EmulateMidButtonTime"  "75"
   Option       "VertScrollDelta"       "20"
   Option       "HorizScrollDelta"      "20"
   Option       "MinSpeed"              "0.60"
   Option       "MaxSpeed"              "1.10"
   Option       "AccelFactor"           "0.030"
   Option       "EdgeMotionMinSpeed"    "200"
   Option       "EdgeMotionMaxSpeed"    "200
   Option       "UpDownScrolling"       "1"
   Option       "CircularScrolling"     "1"
   Option       "CircScrollDelta"       "0.1"
   Option       "CircScrollTrigger"     "2"
   Option       "SHMConfig"             "true"
   Option       "Emulate3Buttons"       "on"
EndSection
```

---

