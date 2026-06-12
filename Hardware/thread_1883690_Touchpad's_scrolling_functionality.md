---
title: "Touchpad's scrolling functionality"
date: 2011-11-19
forum: Hardware
---

### Post by Lazzi on 2011-11-19
Hello!
I am using Ubuntu 11.10 on Acer Aspire 5738ZG. Mostly the OS works fine, but the scrolling on the touch pad mouse doesn't. Mouse moves, tapping works, everything except scrolling. I've checked from mouse settings that scrolling is enabled, it just doesn't work. It works on windows 7 but not on Ubuntu.

Is there something I can do to fix this issue?

---

### Post by emilywind on 2011-11-19
> **Lazzi said:**
> Hello!
I am using Ubuntu 11.10 on Acer Aspire 5738ZG. Mostly the OS works fine, but the scrolling on the touch pad mouse doesn't. Mouse moves, tapping works, everything except scrolling. I've checked from mouse settings that scrolling is enabled, it just doesn't work. It works on windows 7 but not on Ubuntu.

Is there something I can do to fix this issue?

Can you give the output of:

```
synclient -l
```

Also, are you looking to enable side or two finger scrolling?

---

### Post by Lazzi on 2011-11-19
Here's the out put of "synclient -l"

```
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
    HorizEdgeScroll         = 0
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
    TouchpadOff             = 0
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

```

And I'm trying to get the side scrolling working

---

### Post by Lazzi on 2011-11-20
Found solution from askubuntu.com.
[http://askubuntu.com/questions/63265/touchpad-scroll-not-working-on-acer-aspire-one/63292#63292](http://askubuntu.com/questions/63265/touchpad-scroll-not-working-on-acer-aspire-one/63292#63292)

---

