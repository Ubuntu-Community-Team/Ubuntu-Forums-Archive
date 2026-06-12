---
title: "Touchpad two-finger tap and scroll"
date: 2013-02-03
forum: Hardware
---

### Post by Slowhand47 on 2013-02-03
Hello,

since I'm running Lubuntu 12.10 on a Samsung N145 netbook, I'm having a problem using two-finger tap and scroll on the touchpad. Both gestures work, but often the two-finger tap (which I'm using as the middle mouse button) causes a two-finger scroll. This is extremely annoying when browsing web pages and using the two-finger tap to open a link in a new tap. The browser often randomly scrolls away from the link instead of opening it.

Before Lubuntu 12.10 I was using Ubuntu 11.10, and I still have Mint 9 LXDE on a second partition. Both do not show this behaviour.

I guess I can somehow fine-tune this with synclient. I already found out that I have to create an xorg.conf file to make my synclient settings persistent (I did not find a GUI tool for touchpad configuration in the system settings). Can someone point me to the right option or combination of options to make the touchpad's two-finger tap more reliable?

Here are my current settings:

```

xxx@crossfire:~$ synclient -l
Parameter settings:
    LeftEdge                = 32
    RightEdge               = 787
    TopEdge                 = 21
    BottomEdge              = 384
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 40
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 18
    HorizScrollDelta        = 18
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.219058
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 73
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 0
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
    HorizHysteresis         = 4
    VertHysteresis          = 4
    ClickPad                = 0

```


Jan

---

