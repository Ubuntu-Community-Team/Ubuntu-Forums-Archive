---
title: "Enabling touchpad"
date: 2012-09-29
forum: Hardware
---

### Post by Mahler122 on 2012-09-29
For some reason after login, my touchpad stops responding. It's not a hardware problem because it works at the login screen.

Some googling revealed that I should be able to enable the touchpacd using the command xinput.

list of xinput devices:

```
$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Dynex Wired Optical Mouse               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; BisonCam, NB Pro                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```

List of properties of the touchpad:

```
$ xinput list-props 13
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (133):	0
	Coordinate Transformation Matrix (135):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (257):	1
	Device Accel Constant Deceleration (258):	2.500000
	Device Accel Adaptive Deceleration (259):	1.000000
	Device Accel Velocity Scaling (260):	12.500000
	Synaptics Edges (280):	1767, 5397, 1637, 4451
	Synaptics Finger (281):	25, 30, 0
	Synaptics Tap Time (282):	180
	Synaptics Tap Move (283):	234
	Synaptics Tap Durations (284):	180, 180, 100
	Synaptics ClickPad (285):	0
	Synaptics Middle Button Timeout (286):	75
	Synaptics Two-Finger Pressure (287):	282
	Synaptics Two-Finger Width (288):	7
	Synaptics Scrolling Distance (289):	106, 106
	Synaptics Edge Scrolling (290):	1, 0, 0
	Synaptics Two-Finger Scrolling (291):	0, 0
	Synaptics Move Speed (292):	1.000000, 1.750000, 0.037460, 0.000000
	Synaptics Off (293):	0
	Synaptics Locked Drags (294):	0
	Synaptics Locked Drags Timeout (295):	5000
	Synaptics Tap Action (296):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (297):	1, 1, 1
	Synaptics Circular Scrolling (298):	0
	Synaptics Circular Scrolling Distance (299):	0.100000
	Synaptics Circular Scrolling Trigger (300):	0
	Synaptics Palm Detection (301):	0
	Synaptics Palm Dimensions (302):	10, 200
	Synaptics Coasting Speed (303):	20.000000, 50.000000
	Synaptics Pressure Motion (304):	30, 160
	Synaptics Pressure Motion Factor (305):	1.000000, 1.000000
	Synaptics Grab Event Device (306):	1
	Synaptics Gestures (307):	1
	Synaptics Capabilities (308):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (309):	102, 66
	Synaptics Area (310):	0, 0, 0, 0
	Synaptics Noise Cancellation (311):	26, 26
	Device Product ID (250):	2, 7
	Device Node (251):	"/dev/input/event8"
```

I'm then led to believe that xinput set-prop can enable the touchpad. However, you can see that after running the command, the touchpad remains disabled.

```
$ xinput --set-prop 13 133 1
$ xinput list-props 13
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (133):	0
	Coordinate Transformation Matrix (135):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (257):	1
	Device Accel Constant Deceleration (258):	2.500000
	Device Accel Adaptive Deceleration (259):	1.000000
	Device Accel Velocity Scaling (260):	12.500000
	Synaptics Edges (280):	1767, 5397, 1637, 4451
	Synaptics Finger (281):	25, 30, 0
	Synaptics Tap Time (282):	180
	Synaptics Tap Move (283):	234
	Synaptics Tap Durations (284):	180, 180, 100
	Synaptics ClickPad (285):	0
	Synaptics Middle Button Timeout (286):	75
	Synaptics Two-Finger Pressure (287):	282
	Synaptics Two-Finger Width (288):	7
	Synaptics Scrolling Distance (289):	106, 106
	Synaptics Edge Scrolling (290):	1, 0, 0
	Synaptics Two-Finger Scrolling (291):	0, 0
	Synaptics Move Speed (292):	1.000000, 1.750000, 0.037460, 0.000000
	Synaptics Off (293):	0
	Synaptics Locked Drags (294):	0
	Synaptics Locked Drags Timeout (295):	5000
	Synaptics Tap Action (296):	0, 0, 0, 0, 0, 0, 0
	Synaptics Click Action (297):	1, 1, 1
	Synaptics Circular Scrolling (298):	0
	Synaptics Circular Scrolling Distance (299):	0.100000
	Synaptics Circular Scrolling Trigger (300):	0
	Synaptics Palm Detection (301):	0
	Synaptics Palm Dimensions (302):	10, 200
	Synaptics Coasting Speed (303):	20.000000, 50.000000
	Synaptics Pressure Motion (304):	30, 160
	Synaptics Pressure Motion Factor (305):	1.000000, 1.000000
	Synaptics Grab Event Device (306):	1
	Synaptics Gestures (307):	1
	Synaptics Capabilities (308):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (309):	102, 66
	Synaptics Area (310):	0, 0, 0, 0
	Synaptics Noise Cancellation (311):	26, 26
	Device Product ID (250):	2, 7
	Device Node (251):	"/dev/input/event8"
```

Is there a better way that this should be done?

---

### Post by itagomo on 2012-09-29
how bout this:
```
 xinput set-int-prop 13 "Device Enabled" 13 1
```

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

---

### Post by Mahler122 on 2012-09-29
No dice.

```
$ xinput set-int-prop 13 "Device Enabled" 13 1
Invalid format 13
```

reading the man page shows that the argument after "Device Enabled" can only be 8 16 or 32.

trying anything other than 8 gives:

```
$ xinput set-int-prop 13 "Device Enabled" 16 1
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Value in failed request:  0x85
  Serial number of failed request:  19
  Current serial number in output stream:  20
```

However, trying 8 doesn't enable the touchpad.

```
$ xinput set-int-prop 13 "Device Enabled" 8 1
$ xinput list-props 13 | grep Enabled
	Device Enabled (133):	0
```

---

### Post by Mahler122 on 2012-09-30
Oh another interesting piece of information,

Somehow the situation is that x thinks that the touchpad is disabled when actually it's hardware enabled, and when I touch the 'enable/disable touchpad' button on my laptop, I get the message from ubuntu that the touchpad is now enabled, however it's actually hardware disabled at that point so I can't use it then either...

Which is why I'm looking for a software method of enabling the touchpad.

---

### Post by Mahler122 on 2012-10-19
So, I discovered a solution to the problem. It's not the solution I wanted but I will still mark this thread as solved.

The problem was that if I disabled the touch pad while working, and then hibernated the computer, upon resuming from hibernation, the OS would remember that I had disabled the touchpad, however my hardware would revert to the touchpad being enabled. Thus if I pressed the button to disable, it would 'enable' in software. Thus preventing me from using the touchpad.

I attempted to switch the touchpad mode using only software methods which was the point of this post, but these methods failed it seems.

So if anyone can tell me why they think the software option above didn't work, I'd be quite grateful.

---

