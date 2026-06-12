---
title: "Synaptics Touchpad two finger scrolling greyed out"
date: 2012-08-06
forum: Hardware
---

### Post by SlasherIT on 2012-08-06
Hello,

I'm using Ubuntu 12.04 on a HP laptop: [http://h10025.www1.hp.com/ewfrf/wc/product?product=4043738&lc=en&cc=emea_middle_east&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_emea_middle_east/4043738/loc:0&cc=emea_middle_east](http://h10025.www1.hp.com/ewfrf/wc/product?product=4043738&lc=en&cc=emea_middle_east&dlc=en&lang=en&tmp_track_link=ot_we/prodlink/en_emea_middle_east/4043738/loc:0&cc=emea_middle_east)

The problem is that two finger scrolling is greyed out, and I can't select it. Two finger scrolling works in Windows and I think on a previous version of Ubuntu, 10.10 I think? Also, edge scrolling works fine.

Help would be appreciated, thanks.

---

### Post by SlasherIT on 2012-08-09
Bump.

---

### Post by SlasherIT on 2012-08-13
Anyone?

---

### Post by SlasherIT on 2012-08-15
Hello guys, please can you try to help me? Its almost been a week with no response :(.

---

### Post by cortman on 2012-08-15
What happens if you run

```
synclient VertTwoFingerScroll=1
```

in a terminal?

---

### Post by SlasherIT on 2012-08-15
Hi, thanks for responding.

Nothing really. I enter it into the terminal, and press enter. I get no response from the terminal after that.

> naimchahine@Slasher:~$ synclient VertTwoFingerScroll=1
naimchahine@Slasher:~$ 


I tried two finger scrolling in Chrome, but alas, no change at all :(.

---

### Post by cortman on 2012-08-16
> **SlasherIT said:**
> Hi, thanks for responding.

Nothing really. I enter it into the terminal, and press enter. I get no response from the terminal after that.



I tried two finger scrolling in Chrome, but alas, no change at all :(.

Type just "synclient" in the terminal; look over the options there. Also run

```
sudo apt-get install xserver-xorg-input-synaptics
```

To make sure the driver is installed.

---

### Post by SlasherIT on 2012-08-16
I checked in Synaptics, the driver is installed.

Synclient shows this:

> naimchahine@Slasher:~$ synclient
Parameter settings:
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
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0398089
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 401
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
    HorizHysteresis         = 25
    VertHysteresis          = 25
    ClickPad                = 0


---

### Post by cortman on 2012-08-16
> VertTwoFingerScroll = 0

The parameter is still set to 0. I think this is a case of not being able to enable multitouch. Install the dkms driver

```
sudo apt-get install dkms
```

Reboot, then go to System Settings and see if that fixes it. Alternately, try VertTwoFingerScroll again too.

---

### Post by SlasherIT on 2012-08-16
dkms is already installed.

---

### Post by cortman on 2012-08-16
> **SlasherIT said:**
> dkms is already installed.

[SIZE=1]oh.[/SIZE]

What's the output of

```
xinput list
```

---

### Post by SlasherIT on 2012-08-16
```
naimchahine@Slasher:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; MCE IR Keyboard/Mouse (ene_ir)          	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver      	id=15	[slave  keyboard (3)]

```

---

### Post by cortman on 2012-08-16
Ok, how about these in this order:

```
synclient VertTwoFingerScroll=1
xinput list-props 12 
```

and post output. Thanks!

---

### Post by SlasherIT on 2012-08-17
```
naimchahine@Slasher:~$ synclient VertTwoFingerScroll=1
naimchahine@Slasher:~$ xinput list-props 12
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (243):	1
	Device Accel Constant Deceleration (244):	2.500000
	Device Accel Adaptive Deceleration (245):	1.000000
	Device Accel Velocity Scaling (246):	12.500000
	Synaptics Edges (247):	1752, 5192, 1620, 4236
	Synaptics Finger (248):	25, 30, 256
	Synaptics Tap Time (249):	180
	Synaptics Tap Move (250):	221
	Synaptics Tap Durations (251):	180, 180, 100
	Synaptics ClickPad (252):	0
	Synaptics Tap FastTap (253):	0
	Synaptics Middle Button Timeout (254):	75
	Synaptics Two-Finger Pressure (255):	282
	Synaptics Two-Finger Width (256):	7
	Synaptics Scrolling Distance (257):	100, 100
	Synaptics Edge Scrolling (258):	1, 0, 0
	Synaptics Two-Finger Scrolling (259):	1, 0
	Synaptics Move Speed (260):	1.000000, 1.750000, 0.039809, 40.000000
	Synaptics Edge Motion Pressure (261):	30, 160
	Synaptics Edge Motion Speed (262):	1, 401
	Synaptics Edge Motion Always (263):	0
	Synaptics Off (264):	0
	Synaptics Locked Drags (265):	0
	Synaptics Locked Drags Timeout (266):	5000
	Synaptics Tap Action (267):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (268):	1, 1, 0
	Synaptics Circular Scrolling (269):	0
	Synaptics Circular Scrolling Distance (270):	0.100000
	Synaptics Circular Scrolling Trigger (271):	0
	Synaptics Circular Pad (272):	0
	Synaptics Palm Detection (273):	0
	Synaptics Palm Dimensions (274):	10, 200
	Synaptics Coasting Speed (275):	20.000000, 50.000000
	Synaptics Pressure Motion (276):		... of unknown type CARDINAL

	Synaptics Pressure Motion Factor (277):	1.000000, 1.000000
	Synaptics Resolution Detect (278):	1
	Synaptics Grab Event Device (279):	1
	Synaptics Gestures (280):	1
	Synaptics Capabilities (281):	1, 0, 1, 0, 0, 1, 1
	Synaptics Pad Resolution (282):	106, 58
	Synaptics Area (283):	0, 0, 0, 0
	Synaptics Noise Cancellation (284):	25, 25
	Device Product ID (238):	2, 7
	Device Node (239):	"/dev/input/event17"

```

No, thank you!

---

### Post by cortman on 2012-08-17
> **SlasherIT said:**
> ```
naimchahine@Slasher:~$ synclient VertTwoFingerScroll=1
naimchahine@Slasher:~$ xinput list-props 12
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (243):	1
	Device Accel Constant Deceleration (244):	2.500000
	Device Accel Adaptive Deceleration (245):	1.000000
	Device Accel Velocity Scaling (246):	12.500000
	Synaptics Edges (247):	1752, 5192, 1620, 4236
	Synaptics Finger (248):	25, 30, 256
	Synaptics Tap Time (249):	180
	Synaptics Tap Move (250):	221
	Synaptics Tap Durations (251):	180, 180, 100
	Synaptics ClickPad (252):	0
	Synaptics Tap FastTap (253):	0
	Synaptics Middle Button Timeout (254):	75
	Synaptics Two-Finger Pressure (255):	282
	Synaptics Two-Finger Width (256):	7
	Synaptics Scrolling Distance (257):	100, 100
	Synaptics Edge Scrolling (258):	1, 0, 0
	Synaptics Two-Finger Scrolling (259):	1, 0
	Synaptics Move Speed (260):	1.000000, 1.750000, 0.039809, 40.000000
	Synaptics Edge Motion Pressure (261):	30, 160
	Synaptics Edge Motion Speed (262):	1, 401
	Synaptics Edge Motion Always (263):	0
	Synaptics Off (264):	0
	Synaptics Locked Drags (265):	0
	Synaptics Locked Drags Timeout (266):	5000
	Synaptics Tap Action (267):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (268):	1, 1, 0
	Synaptics Circular Scrolling (269):	0
	Synaptics Circular Scrolling Distance (270):	0.100000
	Synaptics Circular Scrolling Trigger (271):	0
	Synaptics Circular Pad (272):	0
	Synaptics Palm Detection (273):	0
	Synaptics Palm Dimensions (274):	10, 200
	Synaptics Coasting Speed (275):	20.000000, 50.000000
	Synaptics Pressure Motion (276):		... of unknown type CARDINAL

	Synaptics Pressure Motion Factor (277):	1.000000, 1.000000
	Synaptics Resolution Detect (278):	1
	Synaptics Grab Event Device (279):	1
	Synaptics Gestures (280):	1
	Synaptics Capabilities (281):	1, 0, 1, 0, 0, 1, 1
	Synaptics Pad Resolution (282):	106, 58
	Synaptics Area (283):	0, 0, 0, 0
	Synaptics Noise Cancellation (284):	25, 25
	Device Product ID (238):	2, 7
	Device Node (239):	"/dev/input/event17"

```

No, thank you!

Grasping at straws here, but try the synclient VertTwoFinerScroll command with sudo.

---

### Post by SlasherIT on 2012-08-17
```
naimchahine@Slasher:~$ sudo synclient VertTwoFingerScroll=1
[sudo] password for naimchahine: 
naimchahine@Slasher:~$ 

```

Am I supposed to restart after doing this?

---

### Post by cortman on 2012-08-17
> **SlasherIT said:**
> ```
naimchahine@Slasher:~$ sudo synclient VertTwoFingerScroll=1
[sudo] password for naimchahine: 
naimchahine@Slasher:~$ 

```

Am I supposed to restart after doing this?

I don't think you should, in fact I think it should lose the setting upon reboot... but you can try.
Let me do a little more research here.

---

### Post by cortman on 2012-08-17
I think I'm at the end of my rope; I've scoured the internet looking for another instance of this happening and can't find it. I'll give you the link to this [wiki page]("https://help.ubuntu.com/community/SynapticsTouchpad/"), and hope you can get something sorted out! 99 times out of 100 these solutions would have already fixed it.
Sorry I wasn't more help...

---

### Post by SlasherIT on 2012-08-20
Unfortunately that wiki was of no help at all :(. So am I screwed? Thanks for trying to help me btw.

---

### Post by cortman on 2012-08-20
Everything holds out that VertTwoFingerScroll should work just fine; you have Synaptics touchpad; you have the correct driver; you have synclient. If it's still not working I'm not sure why it would be; perhaps someone with more knowledge could help.

---

### Post by SlasherIT on 2012-08-20
Alright then, thank you very much, hope someone comes to help me.

Is there anyway I can +1 rep you?

---

### Post by cortman on 2012-08-20
> **SlasherIT said:**
> Alright then, thank you very much, hope someone comes to help me.

Is there anyway I can +1 rep you?

Ah, thanks a lot for the offer! I don't think there's any way to do such on the forums though.
Good luck!

---

### Post by SlasherIT on 2012-08-20
Oh well then. Thanks for trying to help. Now to play the waiting game... Unless you know someone that can help me.

---

### Post by SlasherIT on 2012-09-14
Bump, hope someone can help me.

---

### Post by mieubrisse on 2012-12-06
I've been having this exact same problem. Anybody able to help with this? =/

---

### Post by ManiacMagee on 2012-12-09
Hi,

I have the same problem.  I believe the issue is related to the following bug report:
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-multitouch/+bug/308191/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xf86-input-multitouch/+bug/308191/+index?comments=all)

@SlasherIT
The output "Synaptics Capabilities (281): 1, 0, 1, 0, 0, 1, 1" indicates that your touchpad's multitouch capability isn't recognized.  The 4th and 5th positions are for 2 finger detection and 3 finger detection.  If you try to reinstall the driver or synaptics-dkms, do you get any error messages?  I get one that is mentioned a few times in the bug report:

"make KERNELRELEASE=3.2.0-34-generic -C /lib/modules/3.2.0-34-generic/build SUBDIRS=/var/lib/dkms/synaptics/1.1.1/build modules....(bad exit status: 2)
ERROR (dkms apport): binary package for synaptics: 1.1.1 not found
Error! Bad return status for module build on kernel: 3.2.0-34-generic (x86_64)
Consult /var/lib/dkms/synaptics/1.1.1/build/make.log for more information.
dpkg: error processing synaptics-dkms (--install):
 subprocess installed post-installation script returned error exit status 10"

@mieubrisse
Do you have the same output for "Synaptics Capabilities", and do you get a similar error message?

---

