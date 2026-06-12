---
title: "horizontal scrolling thinkpad t410, ubuntu 10.10"
date: 2010-12-06
forum: Hardware
---

### Post by hobbsc on 2010-12-06
I've got a ThinkPad T410 and I can't seem to get horizontal scrolling working on the touchpad with 10.10.  I seem to recall being able to use it in 10.04, but my memory may be faulty...

I've installed "pointing devices" and set it to allow horizontal scrolling there, tried the default 'mouse' app under system -> preferences, and i've used synclient to set HorizEdgeScroll=1.

The closest I've come to being able to get it functioning is by following this post: [ http://ubuntuforums.org/showpost.php?p=10071212&postcount=8]("http://ubuntuforums.org/showpost.php?p=10071212&postcount=8")

That got two finger scrolling working (both vertical and horizontal), but it was difficult to use.  It wasn't very smooth and didn't always seem to detect my attempt to scroll.

Here's my synclient -l output:


```
Parameter settings:
    LeftEdge                = 1781
    RightEdge               = 5579
    TopEdge                 = 1646
    BottomEdge              = 4582
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 245
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 111
    HorizScrollDelta        = 111
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00896057
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 446
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 1
    GuestMouseOff           = 0
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
    PalmMinZ                = 199
    CoastingSpeed           = 0
    PressureMotionMinZ      = 29
    PressureMotionMaxZ      = 159
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

Thanks!

---

