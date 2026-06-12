---
title: "Touchpad Scrolling"
date: 2009-02-17
forum: Hardware
---

### Post by shreyaspotnis on 2009-02-17
Hi,

I recently upgraded from Hardy to Intrepid. I had gsynaptics installed before and everything was working fine. After upgrading all the relevant sections in xorg.conf were commented out by update-manager saying that HAL is now used.

So I uncommented the touchpad section and added the SHMConfig option. After that I could adjust my touchpad sensitivity, speed and acceleration but horizontal and vertical scrolling stopped, even though I have enabled it in gsynaptics.

My xorg.conf file reads:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option  "MinSpeed"      "0.6"
        Option  "MaxSpeed"      "0.9"
        Option  "AccelFactor" "0.10"
        Option "SHMConfig" "true"

EndSection

```

and synclient -l gives
```
~$ synclient -l
Parameter settings:
    LeftEdge                = 40
    RightEdge               = 983
    TopEdge                 = 42
    BottomEdge              = 725
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 243
    MaxTapMove              = 220
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 1
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 257
    VertScrollDelta         = 105
    HorizScrollDelta        = 86
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.8
    MaxSpeed                = 1
    AccelFactor             = 0.1
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 102
    EdgeMotionUseAlways     = 1
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 2
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
    CircScrollTrigger       = 4
    CircularPad             = 0
    PalmDetect              = 1
    PalmMinWidth            = 10
    PalmMinZ                = 200
    CoastingSpeed           = 20
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1

```

Can somoene please help me out?

Thanks,
Shreyas.

---

### Post by shreyaspotnis on 2009-02-18
I just found out that TouchpadOff=2 means that scrolling if off! But doing synclient TouchpadOff=0 didn't help either :(
Someone please help me out.

---

### Post by littlelion58 on 2009-02-20
if you haven't already, try looking in preferences and mouse, under scrolling, is it checked or unchecked?

also try enabling shmconfig in the hal synaptics config file:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

read the comment for the syntax.

hope that helps

---

