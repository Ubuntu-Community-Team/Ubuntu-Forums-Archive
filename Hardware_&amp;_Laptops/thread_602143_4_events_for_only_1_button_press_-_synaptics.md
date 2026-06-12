---
title: "4 events for only 1 button press - synaptics"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by Joaquim on 2007-11-03
I have a LG A1 Express Dual. It comes with a synaptics touchpad.
Whenever I push the left button (the real button, not a tap in the touchpad) it generates two events :confused:

It's as if i had pressed button 4, and then pressed button 1

Here's the "xev" tool output:

```
ButtonPress event, serial 27, synthetic NO, window 0x2800001,
    root 0x5c, subw 0x0, time 145682450, (79,68), root:(892,92),
    state 0x0, button 4, same_screen YES

ButtonPress event, serial 27, synthetic NO, window 0x2800001,
    root 0x5c, subw 0x0, time 145682527, (79,68), root:(892,92),
    state 0x800, button 1, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x2800001,
    root 0x5c, subw 0x0, time 145682599, (79,68), root:(892,92),
    state 0x900, button 1, same_screen YES

ButtonRelease event, serial 27, synthetic NO, window 0x2800001,
    root 0x5c, subw 0x0, time 145682599, (79,68), root:(892,92),
    state 0x800, button 4, same_screen YES
```
 
The same happens to right button except this time, it generates button 3 and 5 events respectively.

Is anyone having the same problem?

The settings for the driver are listed with "synclient -l":
 
<code>
 Parameter settings:
    LeftEdge             = 1872
    RightEdge            = 5072
    TopEdge              = 1712
    BottomEdge           = 4144
    FingerLow            = 20
    FingerHigh           = 25
    MaxTapTime           = 180
    MaxTapMove           = 220
    MaxDoubleTapTime     = 180
    SingleTapTimeout     = 180
    ClickTime            = 100
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 60
    HorizScrollDelta     = 80
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 1
    VertTwoFingerScroll  = 0
    HorizTwoFingerScroll = 0
    MinSpeed             = 0.0822368
    MaxSpeed             = 0.197368
    AccelFactor          = 0.00164474
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 304
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 0
    GuestMouseOff        = 0
    LockedDrags          = 1
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 1
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 3
    CircularPad          = 0
    PalmDetect           = 1
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0
    PressureMotionMinZ   = 30
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
</code>

By the way, it works fine on XP :lolflag:

---

