---
title: "two-finger right-click on clickpad works erratically"
date: 2014-11-21
forum: Hardware
---

### Post by leptogenesis2 on 2014-11-21
I just got an Acer Aspire v15 nitro, and am having an issue with its clickpad.  It's the kind where the touchpad has no buttons beneath it, but rather functions as one large button.  left-clicking is done with a single finger and works fine; scrolling by dragging two fingers works fine as well.  However, the standard gesture for right-click--i.e. a click with two fingers--has a very bizarre issue.  Once in about 10 tries it works correctly.  Sometimes it does nothing.  Sometimes it registers as a left click.  Often, it registers as a right click, but the right-click menu disappears almost immediately.  Using the mouse & touchpad test, it seems that sometimes the laptop sees a right-click immediately followed by a left-click.  Another interesting observation is that right-click is much less likely to work in nautilus than in firefox.  I'm using Ubuntu 14.10.  Any ideas?  Here is my synclient:

```

    LeftEdge                = 49
    RightEdge               = 1187
    TopEdge                 = 48
    BottomEdge              = 850
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 67
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -30
    HorizScrollDelta        = -30
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.130976
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
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 7
    VertHysteresis          = 7
    ClickPad                = 0

```

---

### Post by mkim3 on 2015-03-11
> **leptogenesis2 said:**
> I just got an Acer Aspire v15 nitro, and am having an issue with its clickpad.  It's the kind where the touchpad has no buttons beneath it, but rather functions as one large button.  left-clicking is done with a single finger and works fine; scrolling by dragging two fingers works fine as well.  However, the standard gesture for right-click--i.e. a click with two fingers--has a very bizarre issue.  Once in about 10 tries it works correctly.  Sometimes it does nothing.  Sometimes it registers as a left click.  Often, it registers as a right click, but the right-click menu disappears almost immediately.  Using the mouse & touchpad test, it seems that sometimes the laptop sees a right-click immediately followed by a left-click.  Another interesting observation is that right-click is much less likely to work in nautilus than in firefox.  I'm using Ubuntu 14.10.  Any ideas?  Here is my synclient:

```

    LeftEdge                = 49
    RightEdge               = 1187
    TopEdge                 = 48
    BottomEdge              = 850
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 67
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -30
    HorizScrollDelta        = -30
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.130976
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
    ClickFinger2            = 3
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 7
    VertHysteresis          = 7
    ClickPad                = 0

```

I also have a Acer V15 Nitro running 14.10. I realize this post was from a few months ago, but since its one of the top searches for the Nitro trackpad, I thought I'd point out that the fix for this is 

synclient Clickpad=1.

---

