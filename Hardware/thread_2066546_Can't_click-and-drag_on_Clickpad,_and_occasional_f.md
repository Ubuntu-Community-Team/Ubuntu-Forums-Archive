---
title: "Can't click-and-drag on Clickpad, and occasional freezes (Sentelic)"
date: 2012-10-04
forum: Hardware
---

### Post by darincb77 on 2012-10-04
I have a Sentelic clickpad (no pysical buttons, i.e. macbook style). It uses synclient. I have upgraded to kernel 3.5.4-030504-generic on Ubuntu 12.04. Side or two-finger scrolling works. What doesn't work is clicking with one finger and a motion action with another finger, like clicking a window and dragging as one would commonly do on a touchpad. Also the touchpad occasionally becomes unresponsive, which can last a couple minutes before it randomly starts functioning again. 

I have tried changing synclient ClickPad=1 and various other synclient settings to no avail. I paste my xinput and synclient output below. Any help or hints would be appreciated. Thanks!

```

darinb@vz:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Chicony USB Wireless HID Receiver       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Chicony USB Wireless HID Receiver       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; FSPPS/2 Sentelic FingerSensingPad       	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Chicony USB Wireless HID Receiver       	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
darinb@vz:~$ synclient
Parameter settings:
    LeftEdge                = 38
    RightEdge               = 929
    TopEdge                 = 38
    BottomEdge              = 673
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 52
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 24
    HorizScrollDelta        = 24
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.166667
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 96
    EdgeMotionUseAlways     = 0
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
    HorizHysteresis         = 6
    VertHysteresis          = 6
    ClickPad                = 1
    RightButtonAreaLeft     = 0
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 0
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

---

