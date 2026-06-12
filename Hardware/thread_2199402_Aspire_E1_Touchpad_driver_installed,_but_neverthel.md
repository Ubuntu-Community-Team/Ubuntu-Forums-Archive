---
title: "Aspire E1: Touchpad driver installed, but nevertheless unusable"
date: 2014-01-13
forum: Hardware
---

### Post by luckystarnova on 2014-01-13
I have an Aspire E1-522-5659 laptop, somewhat new and somewhat cheap.  Tried out a variety of linux os' and liked ubuntu, because ubuntu worked *almost* 100% by just installing it.

The touchpad is practically useless.  It knows the touchpad is there and has drivers installed for it, but when you actually touch the touchpad it moves the mouse randomly accross the screen, maybe.

This I find odd because older linux versions have no problem whatsoever with the touchpad (but can't find the wireless devices which is more important).

Anyways, I'm somewhat new.  Here's what xinput gave me in the terminal:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard 
```

Any insight as to what would be wrong here would be welcome, always having to use the usb mouse is kinda annoying :P

---

### Post by varunendra on 2014-01-14
Welcome to the forums luckystarnova !

You didn't tell us which version of Ubuntu. Please also show us the outputs of -
```
uname -mr
lsb_release -d
synclient
xinput list-props "ETPS/2 Elantech Touchpad"
```

I use the same touchpad on my Asus X54C running on Ubuntu 12.04 (kernel 3.2.0-36), and it works nicely except being too sensitive to touch (pages jump when double-finger tapping to emulate a right-click). Perfectly usable apart from that frequent annoyance.

---

### Post by luckystarnova on 2014-01-14
Here, and thanks! 

uname -mr
```
3.8.0-35-generic x86_64
```
lsb_release -d
```
Description:    Ubuntu 12.04.4 LTS
```
synclient
```
Parameter settings:
    LeftEdge                = 118
    RightEdge               = 2842
    TopEdge                 = 79
    BottomEdge              = 1401
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 145
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 66
    HorizScrollDelta        = 66
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 3.99381
    MaxSpeed                = 1
    AccelFactor             = 0
    TrackstickSpeed         = 1.58347e-43
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 264
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
    HorizHysteresis         = 16
    VertHysteresis          = 16
    ClickPad                = 0
```
xinput list-props "ETPS/2 Elantech Touchpad"
```
Device 'ETPS/2 Elantech Touchpad':
    Device Enabled (144):    1
    Coordinate Transformation Matrix (146):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    1
    Device Accel Constant Deceleration (266):    2.500000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    12.500000
    Synaptics Edges (269):    118, 2842, 79, 1401
    Synaptics Finger (270):    1, 1, 256
    Synaptics Tap Time (271):    180
    Synaptics Tap Move (272):    145
    Synaptics Tap Durations (273):    180, 180, 100
    Synaptics ClickPad (274):    0
    Synaptics Tap FastTap (275):    0
    Synaptics Middle Button Timeout (276):    75
    Synaptics Two-Finger Pressure (277):    282
    Synaptics Two-Finger Width (278):    7
    Synaptics Scrolling Distance (279):    66, 66
    Synaptics Edge Scrolling (280):    1, 0, 0
    Synaptics Two-Finger Scrolling (281):    0, 0
    Synaptics Move Speed (282):    3.993808, 1.000000, 0.000000, 0.000000
    Synaptics Edge Motion Pressure (283):    30, 160
    Synaptics Edge Motion Speed (284):    1, 264
    Synaptics Edge Motion Always (285):    0
    Synaptics Off (286):    0
    Synaptics Locked Drags (287):    0
    Synaptics Locked Drags Timeout (288):    5000
    Synaptics Tap Action (289):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (290):    1, 1, 0
    Synaptics Circular Scrolling (291):    0
    Synaptics Circular Scrolling Distance (292):    0.100000
    Synaptics Circular Scrolling Trigger (293):    0
    Synaptics Circular Pad (294):    0
    Synaptics Palm Detection (295):    0
    Synaptics Palm Dimensions (296):    10, 200
    Synaptics Coasting Speed (297):    20.000000, 50.000000
    Synaptics Pressure Motion (298):        ... of unknown type CARDINAL

    Synaptics Pressure Motion Factor (299):    1.000000, 1.000000
    Synaptics Resolution Detect (300):    1
    Synaptics Grab Event Device (301):    1
    Synaptics Gestures (302):    1
    Synaptics Capabilities (303):    1, 0, 1, 1, 1, 1, 1
    Synaptics Pad Resolution (304):    1, 1
    Synaptics Area (305):    0, 0, 0, 0
    Synaptics Noise Cancellation (306):    16, 16
    Device Product ID (260):    2, 14
    Device Node (261):    "/dev/input/event6"

```

---

### Post by varunendra on 2014-01-14
> **luckystarnova said:**
> 
synclient
```

[B]    MinSpeed                = [COLOR="#FF0000"]3.99381[/COLOR]
    MaxSpeed                = [COLOR="#FF0000"]1[/COLOR][/B]
    AccelFactor             = 0
    TrackstickSpeed         = 1.58347e-43
```

Is it just me or the speed settings are actually crazy? Here are the above settings from mine (I've adjusted them a bit to suit my preference, but can't think of a sane setting where MinSpeed can be higher than MaxSpeed :P) -
```
    [B]MinSpeed                = 1
    MaxSpeed                = 1.75[/B]
    AccelFactor             = 0.0705716
    TrackstickSpeed         = 40
```

Full output -
```
$ synclient
Parameter settings:
    LeftEdge                = 100
    RightEdge               = 2408
    TopEdge                 = 71
    BottomEdge              = 1249
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 124
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 56
    HorizScrollDelta        = 56
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0705716
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 226
    EdgeMotionUseAlways     = 0
    TouchpadOff             = 2
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
    HorizHysteresis         = 14
    VertHysteresis          = 14
    ClickPad                = 0
```

Accordingly, please try adjusting the speed to match mine -
```
synclient MinSpeed=1
synclient MaxSpeed=1.75
synclient AccelFactor=0.07
synclient TrackstickSpeed=40
```
If this brings the pointer under control, you may adjust the values to suit your preferences.

The manual adjustment will be lost at next boot. I'm not yet sure what is the correct method to make them persistent across reboots, but let's just test the above settings for now, and if it helps, I hope we can find a way to make it permanent.

---

### Post by luckystarnova on 2014-01-14
Changed the speed settings, now it is more likely to do something when I touch the touchpad.  Still doesn't move predictably, smoothly, or in any other usable way.
```
synclient
Parameter settings:
    LeftEdge                = 118
    RightEdge               = 2842
    TopEdge                 = 79
    BottomEdge              = 1401
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 145
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 66
    HorizScrollDelta        = 66
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0604412
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 264
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
    HorizHysteresis         = 16
    VertHysteresis          = 16
    ClickPad                = 0

```

---

### Post by varunendra on 2014-01-15
I'm not very familiar with what all the variables mean or what can be reasonable values to them. So can't say if a small difference in any of them can make a big difference in behaviour. As such, can you try manually setting all the values same as mine? Cumbersome, but at least it will make sure if the settings alone can make it usable or not. If not, I'm probably out of ideas already, but you may try a few tweaks with the driver or changing the version of Xorg packages altogether.

---

