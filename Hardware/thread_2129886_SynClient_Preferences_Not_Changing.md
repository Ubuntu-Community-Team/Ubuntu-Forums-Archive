---
title: "SynClient Preferences Not Changing"
date: 2013-03-27
forum: Hardware
---

### Post by audrummer15 on 2013-03-27
Using **Ubuntu 12.10**&#8203;
As stated above, I'm trying to change the palm sensitivity of my trackpad while typing. I'm issuing the following command to change the setting, and then verify that it has been changed(example): 
```

synclient PalmMinWidth=20
synclient -l
Parameter settings:
    LeftEdge                = 1763
    RightEdge               = 5343
    TopEdge                 = 1631
    BottomEdge              = 4375
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 230
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 104
    HorizScrollDelta        = 104
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0381461
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 419
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 0
    RBCornerButton          = 0
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 15
    PalmMinZ                = 255
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 0


```
As you can see, the setting is not changing. Despite a privilege error notification, I also tried issuing this command as super user, still to no avail. What gives?

---

### Post by Atomic-Fanboy on 2013-03-27
Open usr/share/X11/xorg.conf.d/50-synaptics.conf as root. (Be CAREFUL!)
At the end of the "Touchpad Catchall" entry (just before the EndSection), write:
Option "PalmMinWidth" "20" and then save the file.
This should ensure that PalmMinWidth is set to 20 every boot.

---

### Post by audrummer15 on 2013-03-27
> **Atomic-Fanboy said:**
> Open usr/share/X11/xorg.conf.d/50-synaptics.conf as root. (Be CAREFUL!)
At the end of the "Touchpad Catchall" entry (just before the EndSection), write:
Option "PalmMinWidth" "20" and then save the file.
This should ensure that PalmMinWidth is set to 20 every boot.

Thanks, I'll try that. However, I'm curious as to why changing the settings via terminal doesn't work like it seemingly should?

---

### Post by Atomic-Fanboy on 2013-03-28
I'm sorry... I have no idea. Did this work?

---

### Post by audrummer15 on 2013-03-30
> **Atomic-Fanboy said:**
> I'm sorry... I have no idea. Did this work?

No offence, your answer sounds viable. However, I'm more curious as to why I can not change the settings like everyone else seems to be able to. Thank you for the response though. If nothing else works, I'm sure I'll use your advice and it should work fine. Thanks again!

---

