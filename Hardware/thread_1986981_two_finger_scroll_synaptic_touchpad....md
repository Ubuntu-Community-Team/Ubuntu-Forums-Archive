---
title: "two finger scroll synaptic touchpad..."
date: 2012-05-25
forum: Hardware
---

### Post by robodoc2k on 2012-05-25
i have an Acer 5920g notebook
it has a synaptic touchpad and a lateral touch-sensitive multimedia bar that the system sees as a second touchpad
i have configured the last one to work (with xinput and xbindkey). that's ok.
I'm not able to make two fingers gesture works!
in preference/mouse and touchpad/touchpad tab i cannot select it
even if i activate TwoFingerScroll with synclient it doesn't work
**all the previous system in the forum seem not work**
any idea?

ubuntu precise x64

---

### Post by levomac on 2012-05-30
i have a dv6 hp pavilion ,and have the same problem,mine is also a synaptics touch pad,everything works except for the '2 finger scroll'.
In the system settings ,on the touch-pad options* the 2 finger scroll button is grayed out *and hence I can't select it.
I currently use the lateral edge scrolling for vertical scrolling.
To make the 2 finger scroll work I have to add the following lines to the etc/x11/xorg.conf file

Section "InputClass"
Identifier "Default touchpad buttons"
Driver "synaptics"
MatchIsTouchpad "on"
Option "LockedDrags" "1"
Option "VertTwoFingerScroll" "1"
Option "EmulateTwoFingerMinZ" "10"
Option "EmulateTwoFingerMinW" "5"
EndSection

------------------------------------------------------------------------------

#!/bin/sh
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=10
synclient VertEdgeScroll = 1
synclient HorizEdgeScroll = 1

and make this above script run at every boot by adding it to start up applications.

No other method works,if someone can make the default settings work then it would be great.

hope it helps

---

### Post by robodoc2k on 2012-05-31
I followed your instructions but it wasn't succesful.
if i get synclient it responds: 
LeftEdge                = 1752
    RightEdge               = 5192
    TopEdge                 = 1620
    BottomEdge              = 4236
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 10
    EmulateTwoFingerMinW    = 5
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0398089
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 2
    LockedDrags             = 1
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
    HorizHysteresis         = 25
    VertHysteresis          = 25
    ClickPad                = 0

so i can check that the commands are recived, but there is no effect. 
(two fingers doesn't works, in the mouse properties is still greied).

---

