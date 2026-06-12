---
title: "Synaptic setting to ignore double touches?"
date: 2010-02-24
forum: Hardware
---

### Post by tomcat2007 on 2010-02-24
Is there a synaptic parameter that can be used to ignore secondary touching?  When I accidentally touch the touchpad in two places at once, the pointer goes nuts, can select enormous amounts of text and delete it, and perform other such mayhem.  I've turned the sensitivity thresholds (FingerHigh & FingerLow) up as high as feasible, so adjusting those numbers are less an option now than before.

Hardware: Lenovo Y550 (4186) with a SynPS/2 Synaptics TouchPad.
OS: Ubuntu Karmic

Thanks!

---

### Post by tomcat2007 on 2010-02-24
Something else I have noticed while troubleshooting the issue, when my finger touches above the touchpad while using another finger on the touchpad, the problem happens.  I maxed out the TopEdge parameter at 4236 (same as BottomEdge) and would have expected the touchpad to completely ignore input, but it didn't change anything.

Why does touching ABOVE the touchpad at the same time touching the inside the touchpad boundary cause the pointer to jump like crazy when moving only one finger above the touchpad not move the pointer?  This is quite an infuriating problem.

Here is a dump of the settings

tomcat@tomcat2:~$ synclient -l

Parameter settings:
    LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 4236
    BottomEdge              = 4236
    FingerLow               = 34
    FingerHigh              = 39
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.00995223
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 29
    EdgeMotionMaxZ          = 159
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
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
    RTCornerButton          = 0
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
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
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

---

### Post by TheSe7enthSin on 2010-07-18
bump. Anyone know the answer to this?

---

