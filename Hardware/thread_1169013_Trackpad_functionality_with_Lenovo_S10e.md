---
title: "Trackpad functionality with Lenovo S10e"
date: 2009-05-24
forum: Hardware
---

### Post by valmar on 2009-05-24
Dear All,

 I just installed Jaunty on a Lenovo S10e. The S10e has a Synaptics trackpad. However, out of the box I only get tap-to-click and vertical scroll bar, without any way to tap-to-right-click. Is this normal, or the trackpad should have more functionality? I heard that several people seem to be enabling multitouch using fdi files in hal, but this does not work for me, even if I follow their tutorial. What would be interesting form me is the tap-to-right-click: it is the only thing for which I still use the physical button. Anyone knows how to activate it somehow? Multitouch would be perfect (with two-finger scroll), but tap-to-right-click would be excellent also.

Thank you for your help

           Valerio

---

### Post by valmar on 2009-05-24
Dear All! Just an update. I installed gsynpatic and edited the hal fdi files to set shmconfig to on. 

If I now type: symclient -l I get:

Parameter settings:
    LeftEdge                = 1632
    RightEdge               = 5312
    TopEdge                 = 1575
    BottomEdge              = 4281
    FingerLow               = 24
    FingerHigh              = 29
    FingerPress             = 255
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 280
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 0.2
    MaxSpeed                = 0.5
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
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 2
    TapButton3              = 3
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 1
    CircularScrolling       = 0
    CircScrollDelta         = 0.01
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

As you can see, the two finger scrolling seems to be set to one, but it does not work. Anyone is experiencing the same?

                    Valerio

---

### Post by mgrindel on 2009-07-16
Hi,
This is the same behavior I have on my S10e
However two finger scroll does work in XP with the Google Code software.
So there is not a hardware restriction....
Did you ever manage to get yours working??
Mark

---

