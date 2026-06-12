---
title: "Edge Scrolling on Toshiba Satellite R845-S80"
date: 2011-08-22
forum: Hardware
---

### Post by townimbecile on 2011-08-22
I'm having trouble figuring out how to enable edge scrolling on a Toshiba Satellite R845-S80. I have installed synaptics 1.3.99 on ubuntu 11.04.

My synclient settings are:
```

$ synclient -l
Parameter settings:
    LeftEdge                = 153
    RightEdge               = 870
    TopEdge                 = 115
    BottomEdge              = 652
    FingerLow               = 12
    FingerHigh              = 14
    FingerPress             = 127
    MaxTapTime              = 180
    MaxTapMove              = 56
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 139
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 25
    HorizScrollDelta        = 25
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.156495
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 14
    EdgeMotionMaxZ          = 79
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 102
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 1
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 99
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 14
    PressureMotionMaxZ      = 79
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

```

---

### Post by scienceguydan on 2011-12-22
I am having the same problem(no vertical or horizontal scroll on the the touchpad) on my Toshiba Satellite R845-S80 with Ubuntu 11.10 64-bit. I attached a picture of what I see when I open Mouse and TouchPad settings. Also below is the result of running synclient

Parameter settings:
    LeftEdge                = 153
    RightEdge               = 870
    TopEdge                 = 115
    BottomEdge              = 652
    FingerLow               = 12
    FingerHigh              = 14
    FingerPress             = 127
    MaxTapTime              = 180
    MaxTapMove              = 56
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 139
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 25
    HorizScrollDelta        = 25
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.156495
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 14
    EdgeMotionMaxZ          = 79
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 102
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 1
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 99
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 14
    PressureMotionMaxZ      = 79
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0

Please let me know if I can provide you with more information to help better diagnose the problem. Thank You for the help.

---

### Post by marcwhitaker on 2012-01-20
Hey, does this model Ubuntu well on other respects?

---

