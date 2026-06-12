---
title: "Elantech Touchpad Issues"
date: 2013-07-20
forum: Hardware
---

### Post by Commander_Bob on 2013-07-20
I have an Aspire S7 that is running Ubuntu 13.04. Most things are working fine but the touchpad is driving me crazy.

There are three major issues I have with it right now.

The first is the cursor would move much faster vertically than horizontally. I actually fixed this by adding 
	Option "VertResolution" "7"
	Option "HorizResolution" "5"
to 50-synaptics.config (in /usr/share/X11/xorg.conf.d)

The second issue is really bizarre and the most annoying. The vertical sensitivity seems to be non-uniform. If I move my finger at a constant speed up the pad, the cursor will move slowly, speed up for about 1cm, slow down again for about 1cm, and continue doing this for the entire area. This doesn't happen horizontally. This makes it incredibly frustrating to click small buttons because the cursor won't be moving then all of a sudden it jumps over the button.

The last issue, which may be a hardware limitation or caused from above, is that the touchpad seems too insensitive. If I move my finger a little the cursor won't move. It takes a good amount of motion to get it to move and it will often move to far then.

The output from xinput list is
```
$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ELAN Touchscreen                        	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```
```
$ xinput list-props 'ETPS/2 Elantech Touchpad'
Device 'ETPS/2 Elantech Touchpad':
	Device Enabled (133):	1
	Coordinate Transformation Matrix (135):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (261):	1
	Device Accel Constant Deceleration (262):	2.500000
	Device Accel Adaptive Deceleration (263):	1.000000
	Device Accel Velocity Scaling (264):	12.500000
	Synaptics Edges (285):	130, 3126, 95, 1681
	Synaptics Finger (286):	1, 1, 256
	Synaptics Tap Time (287):	180
	Synaptics Tap Move (288):	163
	Synaptics Tap Durations (289):	180, 180, 100
	Synaptics ClickPad (290):	1
	Synaptics Tap FastTap (291):	0
	Synaptics Middle Button Timeout (292):	0
	Synaptics Two-Finger Pressure (293):	282
	Synaptics Two-Finger Width (294):	7
	Synaptics Scrolling Distance (295):	-74, -74
	Synaptics Edge Scrolling (296):	0, 0, 0
	Synaptics Two-Finger Scrolling (297):	1, 1
	Synaptics Move Speed (298):	1.000000, 1.750000, 0.050000, 40.000000
	Synaptics Edge Motion Pressure (299):	30, 160
	Synaptics Edge Motion Speed (300):	1, 296
	Synaptics Edge Motion Always (301):	0
	Synaptics Off (302):	0
	Synaptics Locked Drags (303):	0
	Synaptics Locked Drags Timeout (304):	5000
	Synaptics Tap Action (305):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (306):	1, 3, 0
	Synaptics Circular Scrolling (307):	0
	Synaptics Circular Scrolling Distance (308):	0.100000
	Synaptics Circular Scrolling Trigger (309):	0
	Synaptics Circular Pad (310):	0
	Synaptics Palm Detection (311):	0
	Synaptics Palm Dimensions (312):	10, 200
	Synaptics Coasting Speed (313):	20.000000, 50.000000
	Synaptics Pressure Motion (314):	30, 160
	Synaptics Pressure Motion Factor (315):	1.000000, 1.000000
	Synaptics Resolution Detect (316):	1
	Synaptics Grab Event Device (317):	1
	Synaptics Gestures (318):	1
	Synaptics Capabilities (319):	1, 0, 0, 1, 1, 1, 1
	Synaptics Pad Resolution (320):	600, 500
	Synaptics Area (321):	0, 0, 0, 0
	Synaptics Soft Button Areas (322):	1628, 0, 1456, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (323):	18, 18
	Device Product ID (250):	2, 14
	Device Node (251):	"/dev/input/event7"

```
```
synclient -l
Parameter settings:
    LeftEdge                = 130
    RightEdge               = 3126
    TopEdge                 = 95
    BottomEdge              = 1681
    FingerLow               = 1
    FingerHigh              = 1
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 163
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = -74
    HorizScrollDelta        = -74
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.05
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 296
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
    ClickFinger2            = 3
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
    HorizHysteresis         = 18
    VertHysteresis          = 18
    ClickPad                = 1
    RightButtonAreaLeft     = 1628
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1456
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```

This is driving me crazy and I've even considered loading Win8 back on my laptop to fix this. Any help is greatly appreciated.

---

### Post by Twilight in Zero on 2013-12-06
Bumping this because I am having the exact same issue with the very same touchpad on an Asus G46VW running Xubuntu 13.10.

---

### Post by ivano.visco on 2014-04-03
Same problem here on an Asus N53SV

---

### Post by chronos00 on 2014-06-25
Hello Commander Bob,

I have EXACTLY the same issue with my Acer Aspire S7 (391). Your description of the problem is BY FAR the most accurate I have found on internet. 

The only thing I don't completely agree is on horizontal jerkyness. I do agree that horizontaly, the touchpad behaves much beter than vertically, but I feel it still has some non-uniformity. This is the first time I have ever tested a touchpad this thoroghly, so perhaps this slightly jerky horizontal movement is present in most other touchpads and acceptable.

In any case, where you able to find a solution, work around, or mitigation for this problem?

Thank you!

---

