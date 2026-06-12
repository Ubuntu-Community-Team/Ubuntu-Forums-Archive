---
title: "Touchpad left click causes right click ~80% of the time"
date: 2015-12-21
forum: Hardware
---

### Post by luke62 on 2015-12-21
I had been using 14.04 for a while with no incident, but upgraded to 15.04 (and then 15.10) for various reasons. I formatted the partition and reinstalled 15.04 from scratch, then used the update manager to upgrade to 15.10. 

In both 15.04 and 15.10, my touchpad became nigh-unusable. When i left-click, more often than not it opens up the right click menu and does not register the left click, making navigation of the computer possible only for the most resolute and patient souls. With some google-fu, I determined what it is most likely not the triggered trackpad macros (bottom right corner copies, bottom left corner pastes, etc). No issues with a USB mouse.

output of xinput list-props:
```
Device 'ETPS/2 Elantech Touchpad':
	Device Enabled (146):	1
	Coordinate Transformation Matrix (148):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (268):	1
	Device Accel Constant Deceleration (269):	2.500000
	Device Accel Adaptive Deceleration (270):	1.000000
	Device Accel Velocity Scaling (271):	12.500000
	Synaptics Edges (292):	109, 2619, 60, 1056
	Synaptics Finger (293):	1, 1, 0
	Synaptics Tap Time (294):	180
	Synaptics Tap Move (295):	129
	Synaptics Tap Durations (296):	180, 100, 100
	Synaptics ClickPad (297):	0
	Synaptics Middle Button Timeout (298):	75
	Synaptics Two-Finger Pressure (299):	282
	Synaptics Two-Finger Width (300):	7
	Synaptics Scrolling Distance (301):	-58, -58
	Synaptics Edge Scrolling (302):	1, 1, 0
	Synaptics Two-Finger Scrolling (303):	0, 0
	Synaptics Move Speed (304):	1.000000, 1.750000, 0.067866, 0.000000
	Synaptics Off (305):	2
	Synaptics Locked Drags (306):	0
	Synaptics Locked Drags Timeout (307):	5000
	Synaptics Tap Action (308):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (309):	1, 1, 0
	Synaptics Circular Scrolling (310):	0
	Synaptics Circular Scrolling Distance (311):	0.100000
	Synaptics Circular Scrolling Trigger (312):	0
	Synaptics Circular Pad (313):	0
	Synaptics Palm Detection (314):	0
	Synaptics Palm Dimensions (315):	10, 200
	Synaptics Coasting Speed (316):	20.000000, 50.000000
	Synaptics Pressure Motion (317):	30, 160
	Synaptics Pressure Motion Factor (318):	1.000000, 1.000000
	Synaptics Resolution Detect (319):	1
	Synaptics Grab Event Device (320):	0
	Synaptics Gestures (321):	1
	Synaptics Capabilities (322):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (323):	31, 31
	Synaptics Area (324):	0, 0, 0, 0
	Synaptics Noise Cancellation (325):	14, 14
	Device Product ID (263):	2, 14
	Device Node (264):	"/dev/input/event7"

```

output of synclient -l:
```

Parameter settings:
    LeftEdge                = 109
    RightEdge               = 2619
    TopEdge                 = 60
    BottomEdge              = 1056
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 129
    MaxDoubleTapTime        = 100
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -58
    HorizScrollDelta        = -58
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 1
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0678656
    TouchpadOff             = 2
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
    GrabEventDevice         = 0
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    HorizHysteresis         = 14
    VertHysteresis          = 14
    ClickPad                = 0

```

System Info:
Aspire V3-551 : AMD A8-4500M APU with Radeon(tm) HD Graphics

its possible that it's a mechanical issue (some malformed plastic/debris) but unlikely i think, as this happened immediately after re-installation. i vaguely remember having to do something similar with 14.04, but not enough to say what i did, or be sure that I even did anything.

thanks for your time.

---

