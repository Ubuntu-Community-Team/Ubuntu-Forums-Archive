---
title: "touch pad click"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by mixandgo on 2006-07-27
hello, I am having some problems with my touchpad (AlpsPS/2 ALPS Glidepoint).

synclient -l :
> 
Parameter settings:
    LeftEdge             = 120
    RightEdge            = 910
    TopEdge              = 120
    BottomEdge           = 650
    FingerLow            = 10
    FingerHigh           = 15
    MaxTapTime           = 0
    MaxTapMove           = 0
    MaxDoubleTapTime     = 0
    ClickTime            = 0
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 10
    HorizScrollDelta     = 0
    MinSpeed             = 0.45
    MaxSpeed             = 0.95
    AccelFactor          = 0.015
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 40
    EdgeMotionMaxSpeed   = 40
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 1
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 2
    CircularPad          = 0
    PalmDetect           = 1
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0


Sometimes to do one click like press a shortcut on the menu, I have to click twice, the first click pushes the shortcut (button) down, and the second releases it.

uname -a :
> Linux laptop 2.6.15-26-amd64-generic #1 SMP PREEMPT Mon Jul 17 19:50:04 UTC 2006 x86_64 GNU/Linux


Regards,
Cezar

---

### Post by hizaguchi on 2006-07-27
Yeah, the synaptics driver is a little buggy with 64 bit Dapper.
[http://www.ubuntuforums.org/showthread.php?t=222063](http://www.ubuntuforums.org/showthread.php?t=222063)

---

