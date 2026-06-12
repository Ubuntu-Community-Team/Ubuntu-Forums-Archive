---
title: "tap-to-click on touchpad"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by santo on 2005-12-08
I have a Dell Inspiron 9300 on which I want to completely disable the tap-to-click behaviour (because it's driving me nuts)
Following several posts in this forum and some other references I got everything working as expected initially, but the strange thing is that from time to time the tap-to-click behaviour is still enabled.

This is the touchpad configuration in my xorg.conf file:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        #Option         "Device"                "/dev/psaux"
        Option          "Device"                "/dev/input/event2"
        #Option         "Protocol"              "auto-dev"
        Option          "Protocol"              "event"
        Option          "HorizScrollDelta"      "0"

    #Option      "Device"                "/dev/input/mouse0"
    Option      "LeftEdge"              "120"
    Option      "RightEdge"             "830"
    Option      "TopEdge"               "120"
    Option      "BottomEdge"            "650"
    Option      "FingerLow"             "14"
    Option      "FingerHigh"            "15"
    #Option      "MaxTapTime"            "180"
    Option      "MaxTapTime"            "0"
    #Option      "MaxTapMove"            "110"
    Option      "MaxTapMove"            "0"
    Option      "EmulateMidButtonTime"  "75"
    #Option      "VertScrollDelta"       "20"
    Option      "VertScrollDelta"       "0"
    #Option      "HorizScrollDelta"      "20"
    Option      "MinSpeed"              "0.2"
    Option      "MaxSpeed"              "0.75"
    Option      "AccelFactor"           "0.20"
    Option      "EdgeMotionMinSpeed"    "15"
    Option      "EdgeMotionMaxSpeed"    "15"
    #Option      "UpDownScrolling"       "1"
    Option      "UpDownScrolling"       "0"
    #Option      "CircularScrolling"     "1"
    Option      "CircularScrolling"     "0"
    #Option      "CircScrollDelta"       "0.1"
    Option      "CircScrollDelta"       "0"
    #Option      "CircScrollTrigger"     "2"
    Option      "CircScrollTrigger"     "0"

        Option  "MaxDoubleTapTime"      "0"
        Option  "FastTaps"              "0"
        #Option "TapButton1"    "0"
        #Option "TapButton2"    "0"
        #Option "TapButton3"    "0"
EndSection

```

I'm always working with a mouse during the day, but in the evening I often pull out the mouse and take my laptop with me on the couch.
It's then that I often (but not always !) notice that the tap-to-click behaviour is enabled.

Any ideas what can be causing this behaviour ?

---

### Post by sebro1978 on 2005-12-12
I want to know that to. The touchpad is mutch to sensetive for me. :(

---

