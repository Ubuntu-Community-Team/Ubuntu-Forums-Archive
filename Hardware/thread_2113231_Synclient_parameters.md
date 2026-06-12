---
title: "Synclient parameters?"
date: 2013-02-06
forum: Hardware
---

### Post by Archie Moses on 2013-02-06
Trying to turn off touch to click in the lower right corner of my touchpad.  Buttons are integrated into the pad, entire thing clicks on either side.  When I right click pressing down, on release tap to click selects the first option from the context menu.  Trying to turn off tap to right-click, but leave the button active if that makes sense?  So the button has to be pressed down, every other action is left click.

Can't find an explanation for params so don't know what to change.  Playing around with these settings with reckless abandon, can't find it.

Synclient shows:

```
synclient
Parameter settings:

    LeftEdge                = 1766
    RightEdge               = 5384
    TopEdge                 = 1637
    BottomEdge              = 4451
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 234
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 106
    HorizScrollDelta        = 106
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0375375
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 426
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 2
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
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
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 8
    VertHysteresis          = 8
    ClickPad                = 1
    RightButtonAreaLeft     = 3575
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4091
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

---

### Post by mexicanseaf00d on 2013-02-07
Try synclient RBCornerButton=0

Although it says button, it is the corner-click

RT = right top corner
LT = left top
LB = left bottom


the "3" value in the original setting means mouse button 3 (which is right mouse button)

here are some more options, [https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Synclient](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Synclient)

---

