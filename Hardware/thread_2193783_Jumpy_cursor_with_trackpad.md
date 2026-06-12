---
title: "Jumpy cursor with trackpad"
date: 2013-12-14
forum: Hardware
---

### Post by axe2 on 2013-12-14
I have a new Dell XPS 12 running 13.10.  After installation, the trackpad was detected by the psmouse driver, and the tap gesture was much too sensitive.  In trying to fix this, I found a method to load the synaptic driver to get full gesture control over the trackpad.

All I want is for the track pad to move the cursor and let me use the buttons for clicking.  I don't need/want any gestures, and I'm okay even turning off the tap gesture to left click.  I have been able to get me almost there.  Tap is off, and all other gesture seem to be off, but I'm stuck with one annoyance.

First, the buttons on the XPS 12 are built into the trackpad, and motion is active over the buttons, meaning that you can move the cursor over the entire trackpad, including over the bottom button area.  I think that's key to the problem.

The symptoms show up most often when I try to drag a window (or drag a region on the screen).  If I move the cursor to the top of a window to select it, and then click the left button to start a move, it works correctly until and unless I lift the dragging (first selected) finger.  When I lift this finger it move the window down and to the left.

If I do the opposite (click left button, touch the touchpad with another finger and drag), it immediately warps the window up and to the left.

If I push the left button somewhere on the screen, and then put another finger on the touch pad, it select a region, and the upper left of that region seems to somewhat correspond to the position of the finger on the touchpad.

I'm thinking this is some gesture for quickly selecting a region, but I don't want it, and I haven't been able to figure out how to turn it off.

This is what my synclient list looks like:

```
xps12:~<103> synclient -l
Parameter settings:
    LeftEdge                = 1766
    RightEdge               = 5382
    TopEdge                 = 1639
    BottomEdge              = 4491
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 235
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 107
    HorizScrollDelta        = 107
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1.27946
    MaxSpeed                = 0.241611
    AccelFactor             = 0
    TouchpadOff             = 1
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    ClickFinger1            = 1
    ClickFinger2            = 0
    ClickFinger3            = 0
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
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
    HorizHysteresis         = 26
    VertHysteresis          = 26
    ClickPad                = 1
    RightButtonAreaLeft     = 3574
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 4125
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0
```

Any suggestions on what to try would be appreciated!

---

