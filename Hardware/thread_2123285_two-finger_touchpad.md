---
title: "two-finger touchpad"
date: 2013-03-07
forum: Hardware
---

### Post by layers on 2013-03-07
I have an ALPS touchpad, and I remember that two-finger scroll used to work. But now, it is greyed out in the settings menu and I have to scroll with the edge of the touchpad (hor and vert works). However, I want to have more control without using a mouse - to enable two finger tap, window navigation, etc. I remember doing it years ago, but with 12.04 I can't seem to find properly explained information on enabling the two-finger stuff. Does anyone have an idea where I can start from?```
ibo@ibo-VPCF130FD:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (064e:2100)                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
ibo@ibo-VPCF130FD:~$ synclient -l
Parameter settings:
    LeftEdge                = 300
    RightEdge               = 1700
    TopEdge                 = 210
    BottomEdge              = 1190
    FingerLow               = 12
    FingerHigh              = 15
    FingerPress             = 128
    MaxTapTime              = 180
    MaxTapMove              = 107
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 48
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 48
    HorizScrollDelta        = 48
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0819
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 15
    EdgeMotionMaxZ          = 80
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 195
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
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 1
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.100007
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 100
    CoastingSpeed           = 20
    CoastingFriction        = 50
    PressureMotionMinZ      = 15
    PressureMotionMaxZ      = 80
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    ResolutionDetect        = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 12
    VertHysteresis          = 12
    ClickPad                = 0
ibo@ibo-VPCF130FD:~$
```

---

### Post by tgalati4 on 2013-03-07
I'm running 12.10 and you have a choice between edge scrolling or two-finger.  The one not selected is greyed-out.  Are you sure that you can't select two-finger scrolling?

---

### Post by layers on 2013-03-07
[ATTACH=CONFIG]239883[/ATTACH]

---

### Post by tgalati4 on 2013-03-08
Mine looks the same, but I can select the greyed-out option.  So, I assume that you can't select the greyed-out option?  

I didn't think that the Alps Glidepoint was capable of 2-finger scroll.  You need something call Alps Multipoint or Ultrapoint or some marketing-poo name.  They really should have named it Alps *Chalkboard* or *Sandpaper*.  More reflective of its performance.

---

