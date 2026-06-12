---
title: "Configure Touchpad edge scrolling to use left side?"
date: 2013-01-28
forum: Hardware
---

### Post by dmouck on 2013-01-28
Hello all,

I am using Ubuntu 12.10 x64 on a Dell Latitude E6410. Everything is working quite well, but I would like to configure the touchpad's edge scrolling (vertical) to use the left side instead of the right. I am left-handed, and it would be much more convenient for me to use the left side.

I have looked at the man pages for xinput and frankly am lost. I do not know which variable to set, and what to set it to.

xinput --list outputs the following:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_3M             	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]

```

So I know that id 13 is the one I want to look at.

xinput --list 13 outputs this:

```
AlpsPS/2 ALPS DualPoint TouchPad        	id=13	[slave  pointer  (2)]
	Reporting 8 classes:
		Class originated from: 13. Type: XIButtonClass
		Buttons supported: 12
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None None None
		Button state:
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: 0.000000 - 2000.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: 0.000000 - 1400.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Scroll
		  Range: 0.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 13. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Scroll
		  Range: 0.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 48.000000
		  flags: 0x0
		Class originated from: 13. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: 48.000000
		  flags: 0x0
		Class originated from: 13. Type: XITouchClass
		Touch mode: dependent
		Max number of touches: 2
```

Finally, xinput --list-props 13 outputs this:

```
Device 'AlpsPS/2 ALPS DualPoint TouchPad':
	Device Enabled (143):	1
	Coordinate Transformation Matrix (145):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (263):	1
	Device Accel Constant Deceleration (264):	2.500000
	Device Accel Adaptive Deceleration (265):	1.000000
	Device Accel Velocity Scaling (266):	12.500000
	Synaptics Edges (286):	300, 1700, 210, 1190
	Synaptics Finger (287):	12, 15, 128
	Synaptics Tap Time (288):	180
	Synaptics Tap Move (289):	107
	Synaptics Tap Durations (290):	180, 180, 100
	Synaptics ClickPad (291):	0
	Synaptics Tap FastTap (292):	0
	Synaptics Middle Button Timeout (293):	75
	Synaptics Two-Finger Pressure (294):	141
	Synaptics Two-Finger Width (295):	7
	Synaptics Scrolling Distance (296):	48, 48
	Synaptics Edge Scrolling (297):	1, 0, 0
	Synaptics Two-Finger Scrolling (298):	0, 0
	Synaptics Move Speed (299):	1.000000, 1.750000, 0.081934, 40.000000
	Synaptics Edge Motion Pressure (300):	15, 80
	Synaptics Edge Motion Speed (301):	1, 195
	Synaptics Edge Motion Always (302):	0
	Synaptics Off (303):	2
	Synaptics Locked Drags (304):	0
	Synaptics Locked Drags Timeout (305):	5000
	Synaptics Tap Action (306):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (307):	1, 1, 0
	Synaptics Circular Scrolling (308):	0
	Synaptics Circular Scrolling Distance (309):	0.100000
	Synaptics Circular Scrolling Trigger (310):	0
	Synaptics Circular Pad (311):	0
	Synaptics Palm Detection (312):	0
	Synaptics Palm Dimensions (313):	10, 100
	Synaptics Coasting Speed (314):	20.000000, 50.000000
	Synaptics Pressure Motion (315):	15, 80
	Synaptics Pressure Motion Factor (316):	1.000000, 1.000000
	Synaptics Resolution Detect (317):	1
	Synaptics Grab Event Device (318):	1
	Synaptics Gestures (319):	1
	Synaptics Capabilities (320):	1, 1, 1, 1, 1, 1, 0
	Synaptics Pad Resolution (321):	1, 1
	Synaptics Area (322):	0, 0, 0, 0
	Synaptics Noise Cancellation (323):	12, 12
	Device Product ID (259):	2, 8
	Device Node (260):	"/dev/input/event13"
```

Thanks in advance to anyone who can offer assistance!

Cheers,
dmouck

---

### Post by dmouck on 2013-01-29
Any thoughts?

---

### Post by tgalati4 on 2013-01-29
You have done your homework.  Unfortunately, I don't see any parameters that can be changed to allow left-edge scrolling.  It's possible that it is hardcoded in the the module.  What module is loaded for the DualPoint?

```
lsmod
```  If you can find the source code for that module, you could modify it and then recompile it and load it.  It's possible that it is hardcoded for the right side.  I have an Alps Glidepoint (single touch only) and I couldn't find any switches to change it either.  Fortunately, I'm right handed, otherwise I wouldn't be able to sleep tonight thinking about how to change it.

You could try setting the coordiate transform matrix to -1 from 1 and see what happens.  My guess is that it will simply turn everything upside down.  Which will give you left side scrolling, but everything will be backwards.

---

