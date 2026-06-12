---
title: "Multitouch support for Laptop Touchpad"
date: 2014-05-04
forum: Hardware
---

### Post by randomdude2 on 2014-05-04
Hello Everyone,     I am using Ubuntu 14.04 on my laptop and want to use the multi touch capabilities of my touchpad.  It is an SynPS/2 Synaptics Touchpad and the three finger tap works fine. I have read that the multi touch gestures should be enabled by default but this doesn't seem to be the case for me.  Checking how many fingers my touchpad supports revealed that only 2 are supported right now, however I am able to use up to 4 in Windows 8.  Is there a way to install a new driver, do I need to change some files to enable the three finger swipes?     Any help is greatly appreciated.

---

### Post by randomdude2 on 2014-05-05
So it turns out that my touchpad is not supported currently on a kernel level [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

---

### Post by el_garicimo on 2014-05-10
Messing around with the synclient settings that have to do with palm detection, I can't seem to get it to affect anything either. Any chance you can expound upon how one checks what type of touchpad they have, and then how they can check if it's supported on a kernal level?

I have a Dell XPS 12 9Q33 (haswell chip), with one of those new fangled "clickpads", which is basically just one big button.

---

### Post by el_garicimo on 2014-05-10
Messing around with the synclient settings that have to do with palm detection, I can't seem to get it to affect anything either. Any chance you can expound upon how one checks what type of touchpad they have, and then how they can check if it's supported on a kernal level?

I have a Dell XPS 12 9Q33 (haswell chip), with one of those new fangled "clickpads", which is basically just one big button.

EDIT:
ok, so I "read the F**in manual" a bit by reading more closely the link you provided-- after following the instructions in the [https://wiki.ubuntu.com/DebuggingTouchpadDetection#In_case_your_multitouch_features_does_not_work](https://wiki.ubuntu.com/DebuggingTouchpadDetection#In_case_your_multitouch_features_does_not_work)  , typing

```
$xinput list
```

to get my touchpad version/ device id, I have a SynPS/2 Synaptics TouchPad (same as you!) , device id 11.

then entering

```
$xinput --list-props 11
```

I get the following synaptics capabilities line, telling me what my touchpad can and can't do:

```
Synaptics Capabilities (286):	1, 0, 0, 1, 1, 1, 1
```

According to the man page in synaptics, 

"Synaptics Capabilities              This read-only property expresses the physical capability of the
              touchpad, most notably whether the  touchpad  hardware  supports
              multi-finger tapping and scrolling.


              8  bit (BOOL), 7 values (read-only), has left button, has middle
              button, has right  button,  two-finger  detection,  three-finger
              detection, pressure detection, and finger/palm width detection. "

So that means that my touchpad doesn't have a middle or right button (which makes sense, because it's clickpad), but it should be able to do everything else--two-finger detection, three-finger detection, pressure detection, and **finger/palm width detection; **this would make it appear that the kernal does support all of these features then.

Randomdude2 , what do your synaptics capabilities look like?

---

### Post by el_garicimo on 2014-05-10
for anyone else having palm detection issues quick work around--change the value of your AreaRightEdge variable in synaptics to be a little less then the Right Edge-- my Right Edge was 5382, so setting my AreaRightEdge to 5300 made it so that the very right most part of my clickpad (about a finger's width worth) is deactivate in terms of actuallymoving the pointer. If i click there though, it's still a right click, which is nice.

By default, your AreaRightEdge is probably 0, which means it extends to infinity in that direction (uses the entire area of the clickpad). My clickpad is super big though, so I don't really mind the one finger width's reduction in width, and it solves my problem! :)

---

### Post by luis.nando on 2014-06-03
Is it fair to mark this topic as solved? As far as I understood, the issue of not having the multitouch remained, don't it? Well, I am facing the same issue with my touchpad, here are some specs:

xinput --list
```
 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 Camera                           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

xinput --list-props 12
```
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (135):	1
	Coordinate Transformation Matrix (137):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (260):	1
	Device Accel Constant Deceleration (261):	2.500000
	Device Accel Adaptive Deceleration (262):	1.000000
	Device Accel Velocity Scaling (263):	12.500000
	Synaptics Edges (264):	1763, 5347, 1639, 4483
	Synaptics Finger (265):	25, 30, 0
	Synaptics Tap Time (266):	180
	Synaptics Tap Move (267):	233
	Synaptics Tap Durations (268):	180, 180, 100
	Synaptics ClickPad (269):	1
	Synaptics Middle Button Timeout (270):	0
	Synaptics Two-Finger Pressure (271):	282
	Synaptics Two-Finger Width (272):	7
	Synaptics Scrolling Distance (273):	106, 106
	Synaptics Edge Scrolling (274):	0, 0, 0
	Synaptics Two-Finger Scrolling (275):	1, 1
	Synaptics Move Speed (276):	1.000000, 1.750000, 0.037608, 0.000000
	Synaptics Off (277):	0
	Synaptics Locked Drags (278):	0
	Synaptics Locked Drags Timeout (279):	5000
	Synaptics Tap Action (280):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (281):	1, 3, 0
	Synaptics Circular Scrolling (282):	0
	Synaptics Circular Scrolling Distance (283):	0.100000
	Synaptics Circular Scrolling Trigger (284):	0
	Synaptics Circular Pad (285):	0
	Synaptics Palm Detection (286):	0
	Synaptics Palm Dimensions (287):	10, 200
	Synaptics Coasting Speed (288):	20.000000, 50.000000
	Synaptics Pressure Motion (289):	30, 160
	Synaptics Pressure Motion Factor (290):	1.000000, 1.000000
	Synaptics Resolution Detect (291):	1
	Synaptics Grab Event Device (292):	1
	Synaptics Gestures (293):	1
	Synaptics Capabilities (294):	1, 0, 0, 1, 1, 1, 1
	Synaptics Pad Resolution (295):	59, 37
	Synaptics Area (296):	0, 0, 0, 0
	Synaptics Soft Button Areas (297):	3555, 0, 4118, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (298):	8, 8
	Device Product ID (254):	2, 7
	Device Node (255):	"/dev/input/event3"

```

The fact is that the multitouch support worked out of the box on windows 7, but after Ubuntu it is a no-go. Also, I have other two machines with a Synaptics touchpad that perfectly work with touchegg...

If anyone actually reached a solution for the problem, please share!

Regards

---

### Post by Suhas_Cherukuri on 2014-11-10
This is a guide to getting multitouch gestures to work in Linux [http://blog.mpiannucci.com/view/multitouchgesture](http://blog.mpiannucci.com/view/multitouchgesture)

It involves removing the current synclient driver and replacing it with one that supports gestures.

Hope it helps.

---

