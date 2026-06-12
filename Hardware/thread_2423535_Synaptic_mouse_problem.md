---
title: "Synaptic mouse problem"
date: 2019-07-25
forum: Hardware
---

### Post by gismo93 on 2019-07-25
It's not a huge problem but it's starting to annoy me. So the mouse  works fine for the most part, but when i'm moving my cursor around it  tends to drag and highlight stuff even though I'm not double tapping it.  I tried to mess around with synclient in the terminal by changing  FingerLow and FingerHigh to lower values but the problem persists.

synclient output

```
Parameter settings:
    LeftEdge                = 1596
    RightEdge               = 5344
    TopEdge                 = 1292
    BottomEdge              = 4560
    FingerLow               = 25
    FingerHigh              = 30
    MaxTapTime              = 180
    MaxTapMove              = 254
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -115
    HorizScrollDelta        = -115
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0346021
    TouchpadOff             = 2
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 0
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
    HorizHysteresis         = 28
    VertHysteresis          = 28
    ClickPad                = 0

```
xinput output
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; HP TrueVision HD Camera: HP Tru         	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                     	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]

```
xinput list-props 10 output
```

Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (143):	1
	Coordinate Transformation Matrix (145):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (273):	1
	Device Accel Constant Deceleration (274):	2.500000
	Device Accel Adaptive Deceleration (275):	1.000000
	Device Accel Velocity Scaling (276):	12.500000
	Synaptics Edges (277):	1596, 5344, 1292, 4560
	Synaptics Finger (278):	25, 30, 0
	Synaptics Tap Time (279):	180
	Synaptics Tap Move (280):	254
	Synaptics Tap Durations (281):	180, 180, 100
	Synaptics ClickPad (282):	0
	Synaptics Middle Button Timeout (283):	75
	Synaptics Two-Finger Pressure (284):	282
	Synaptics Two-Finger Width (285):	7
	Synaptics Scrolling Distance (286):	-115, -115
	Synaptics Edge Scrolling (287):	0, 0, 0
	Synaptics Two-Finger Scrolling (288):	0, 0
	Synaptics Move Speed (289):	1.000000, 1.750000, 0.034602, 0.000000
	Synaptics Off (290):	2
	Synaptics Locked Drags (291):	0
	Synaptics Locked Drags Timeout (292):	5000
	Synaptics Tap Action (293):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (294):	1, 0, 0
	Synaptics Circular Scrolling (295):	0
	Synaptics Circular Scrolling Distance (296):	0.100000
	Synaptics Circular Scrolling Trigger (297):	0
	Synaptics Circular Pad (298):	0
	Synaptics Palm Detection (299):	0
	Synaptics Palm Dimensions (300):	10, 200
	Synaptics Coasting Speed (301):	20.000000, 50.000000
	Synaptics Pressure Motion (302):	30, 160
	Synaptics Pressure Motion Factor (303):	1.000000, 1.000000
	Synaptics Resolution Detect (304):	1
	Synaptics Grab Event Device (305):	0
	Synaptics Gestures (306):	1
	Synaptics Capabilities (307):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (308):	84, 39
	Synaptics Area (309):	0, 0, 0, 0
	Synaptics Noise Cancellation (310):	28, 28
	Device Product ID (269):	2, 7
	Device Node (268):	"/dev/input/event4"

```
any help would be greatly appreciated! :)

---

### Post by Autodave on 2019-07-25
First of all, I would ignore the response that is above (if it is even still there).

Can you give us some info on your system please?  Have you tried attaching an external mouse to see if that works OK?

---

### Post by coffeecat on 2019-07-25
@gismo93, I've edited your post to add BBCode code tags in order to restore the columnar formatting. If you post terminal output as plain text in the body of a post, you lose formatting and the output becomes near unreadable. Please enclose all terminal output between BBCode code tags. There is a link to a howto for code tags in my sig if you need it.

---

### Post by cruzer001 on 2019-07-25
As far as I know synaptics should not be an option unless added by the user.  If added then libinput should be removed or else there will be interaction between the two.

---

### Post by gismo93 on 2019-07-25
Ah okay. Well when I change some of the synaptic settings I can definitely notice a different responsiveness in the touchpad but I don't think I'm changing the right settings for what I want. This problem was there before I changed any settings relating to the mouse so I don't think it's an issue with synclient and libinput interacting. How would I go about removing libinput to test if that's the issue? Thanks.

---

