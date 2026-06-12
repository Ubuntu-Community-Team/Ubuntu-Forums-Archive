---
title: "Elantech Touchpad doesn't work on New ASUS TP500L Laptop"
date: 2014-08-26
forum: Hardware
---

### Post by digitaleagle on 2014-08-26
I just bought my wife a brand new ASUS TP500LA-AB52T laptop for work.  I installed Ubuntu 14.04 on it.  The wireless didn't work initially, but I have that working.  Now, I am fighting with the touchpad.

It is a ETPS/2 Elantech Touchpad.

Here's the output of xinput:
```
&#9121; Virtual core pointer id=2 [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)]
&#9116; &#8627; USBest Technology SiS HID Touch Controller id=10 [slave pointer (2)]
&#9116; &#8627; ETPS/2 Elantech Touchpad id=16 [slave pointer (2)]
&#9116; &#8627; Cypress PS/2 to USB Adapter id=13 [slave pointer (2)]
&#9123; Virtual core keyboard id=3 [master keyboard (2)]
&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)]
&#8627; Power Button id=6 [slave keyboard (3)]
&#8627; Video Bus id=7 [slave keyboard (3)]
&#8627; Sleep Button id=8 [slave keyboard (3)]
&#8627; USB2.0 UVC HD Webcam id=9 [slave keyboard (3)]
&#8627; Asus WMI hotkeys id=14 [slave keyboard (3)]
&#8627; AT Translated Set 2 keyboard id=15 [slave keyboard (3)]
&#8627; Belkin Corporation Flip CC id=11 [slave keyboard (3)]
&#8627; Cypress PS/2 to USB Adapter id=12 [slave keyboard (3)]
```

I tried to install the driver from [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+index?comments=all").  Here are the commands that I used:

```
cd ~/Downloads
sudo dkms ldtarball psmouse-elantech-x551c.tar.gz
sudo dkms install -m psmouse -v elantech-x551c</p>
sudo rmmod psmouse
sudo modprobe psmouse
```

It seemed to install fine, but it didn't seem to make any difference.

When the laptop boots, I get no mouse pointer and the touchpad doesn't seem to do anything.  The laptop has a touch screen, and that seems to work for the most part.  I can run the following two commands and turn the touchpad into a regular mouse:
```
modprobe -r psmouse
modprobe psmouse proto=imps
```

After that, I get the mouse pointer, and it seems to work fine.  The multitouch scrolling doesn't work though.  It's basically acting as just a regular mouse without any of the touchpad features.  I also have to run those two commands every time it boots.  I could probably get it so that that option is set automatically upon boot, but I would rather get the touchpad working regularly.

Does anyone have any suggestions?

---

### Post by varunendra on 2014-08-27
Does it work if you reload the 'psmouse' driver without the 'imps' option? That is -
```
modprobe -r psmouse
modprobe psmouse
```

The need for above parameter is an old problem with some specific models, I don't know if it was fixed or not. You may look up for bug reports and see if a proper fix was found/released.

---

### Post by digitaleagle on 2014-08-27
> Does it work if you reload the 'psmouse' driver without the 'imps' option


@varun, thanks for the thought.  That doesn't help.  It resets it back to using the Elantech driver, but my cursor goes away, and the touchpad quits working altogether.


```
lphillips@sunflower:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
lphillips@sunflower:~$ sudo modprobe -r psmouse
lphillips@sunflower:~$ sudo modprobe psmouse
lphillips@sunflower:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
lphillips@sunflower:~$ sudo modprobe -r psmouse
lphillips@sunflower:~$ sudo modprobe psmouse proto=imps
lphillips@sunflower:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```


I've tried combing through some of the bug reports relating to Elantech touchpads, and I have yet to find anything that works.  I saw one that talked about upgrading the kernel, so I'll keep combing through the bug reports and maybe see if I can figure out how to upgrade the kernel.

```
lphillips@sunflower:~$ uname -r
3.13.0-34-generic

```

---

### Post by varunendra on 2014-08-27
Have you tried the 'xinput float/reattach' trick? (as mentioned in post #4 of this thread : [http://ubuntuforums.org/showthread.php?t=2188781](http://ubuntuforums.org/showthread.php?t=2188781) )

What is the output of -
```
synclient
```
when you reload psmouse without proto=imps parameter?

---

### Post by digitaleagle on 2014-08-27
Here's the output of synclient...


```
lphillips@sunflower:~$ sudo modprobe -r psmouse
[sudo] password for lphillips: 
lphillips@sunflower:~$ sudo modprobe psmouse
lphillips@sunflower:~$ synclient
Parameter settings:
    LeftEdge                = 123
    RightEdge               = 2974
    TopEdge                 = 114
    BottomEdge              = 2005
    FingerLow               = 1
    FingerHigh              = 1
    MaxTapTime              = 180
    MaxTapMove              = 165
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    EmulateMidButtonTime    = 0
    EmulateTwoFingerMinZ    = 282
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 75
    HorizScrollDelta        = 75
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 1
    MinSpeed                = 1
    MaxSpeed                = 1.75
    AccelFactor             = 0.0533049
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
    RightButtonAreaLeft     = 1548
    RightButtonAreaRight    = 0
    RightButtonAreaTop      = 1737
    RightButtonAreaBottom   = 0
    MiddleButtonAreaLeft    = 0
    MiddleButtonAreaRight   = 0
    MiddleButtonAreaTop     = 0
    MiddleButtonAreaBottom  = 0

```


I just went back through my notes.  I did try this:

```
$ synclient -l | grep -i touchpad
TouchpadOff = 2

$ synclient TouchpadOff=0
lphillips@sunflower:~$ synclient -l | grep -i touchpad
TouchpadOff = 0


```

That seemed to enable the touchpad, but it didn't make a difference as far as it phyically working.  Along that line, I do have a Fn + F9 feature that is supposed to enable/disable the touchpad.  When I press it, I do get the notification popping up that the OS recognizes it.  It tells me if the touchpad is on or off.  Still it does make the touchpad actually work.

---

### Post by digitaleagle on 2014-08-27
I thought I had tried the other thing that you mentioned.  Just in case, I did it again.  It didn't make a difference.

```
lphillips@sunflower:~$ sudo modprobe -r psmouse
lphillips@sunflower:~$ sudo modprobe psmouse
lphillips@sunflower:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
lphillips@sunflower:~$ xinput float "PS/2 Elantech Touchpad"
unable to find device 'PS/2 Elantech Touchpad'
lphillips@sunflower:~$ xinput reattach "PS/2 Elantech Touchpad" "Virtual core pointer"
unable to find device 'PS/2 Elantech Touchpad'
lphillips@sunflower:~$ xinput float "ETPS/2 Elantech Touchpad"
lphillips@sunflower:~$ xinput reattach "ETPS/2 Elantech Touchpad" "Virtual core pointer"
lphillips@sunflower:~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```

---

### Post by digitaleagle on 2014-09-04
I am still fighting with this.  Based on comments in a bug thread, I decided to try the latest kernel.  It did not help, but just for reference, here's what I did:

Installed the kernel from the[ version 3.17.0-031700rc2 directory]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17-rc2-utopic/").

I installed it with:

```
sudo dpkg -i linux-headers-3.17.0-031700rc2-generic_3.17.0-031700rc2.201408251935_amd64.deb \
linux-image-3.17.0-031700rc2-generic_3.17.0-031700rc2.201408251935_amd64.deb  \
linux-headers-3.17.0-031700rc2_3.17.0-031700rc2.201408251935_all.deb

```
I could see it in the list with:

```
grep vmlinuz /boot/grub/grub.cfg
```

After rebooting, I could tell that I was on the updated kernel with:

```
uname -r
```

At that point, neither my touchscreen nor my touchpad worked.

---

### Post by daringseal on 2014-09-14
Just wondering if anyone found a solution to this issue. I installed Ubuntu on my TP500LA and finally got Wifi working, and touchpad is all I still need.

---

### Post by zvisha on 2014-09-23
I have same issue.
After installing and compiling driver I see following when I move finger over it:

 dmesg | grep -i touch
[ 9119.364806] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.389146] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.415591] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.441420] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.467035] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.731333] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.754198] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
....

I found that some patches were released for specific models:
[https://bugzilla.kernel.org/show_bug.cgi?id=48161](https://bugzilla.kernel.org/show_bug.cgi?id=48161)
but I guess no patch for this model yet.

---

### Post by varunendra on 2014-09-23
Please also post whatever you have tried so far. Have you already tried what is suggested in this thread above?

Along with that, you should also post the outputs of -
```
xinput
synclient
```
..from your systems.

For reference, here are these outputs from mine -
```
**$ xinput**
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; ASUS USB2.0 WebCam                      	id=9	[slave  keyboard (3)]

**$ synclient**
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
    PalmDetect              = 1
    PalmMinWidth            = 3
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
I can clearly see some difference, apparently critical ones, in the outputs from digitaleagle's post. Perhaps the missing properties can be set using "xinput set-prop <device>" command, but I'm not sure and I don't know exactly how. The current values of the properties (in a much detailed form than the output of "synclient") can be listed with "xinput list-props <device>" command.

For reference, this is from mine (working without problems) -
```
**$ xinput list-props "ETPS/2 Elantech Touchpad"**
Device 'ETPS/2 Elantech Touchpad':
	Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (254):	1
	Device Accel Constant Deceleration (255):	2.500000
	Device Accel Adaptive Deceleration (256):	1.000000
	Device Accel Velocity Scaling (257):	12.500000
	Synaptics Edges (258):	100, 2408, 71, 1249
	Synaptics Finger (259):	1, 1, 256
	Synaptics Tap Time (260):	180
	Synaptics Tap Move (261):	124
	Synaptics Tap Durations (262):	180, 180, 100
	Synaptics ClickPad (263):	0
	Synaptics Tap FastTap (264):	0
	Synaptics Middle Button Timeout (265):	75
	Synaptics Two-Finger Pressure (266):	282
	Synaptics Two-Finger Width (267):	7
	Synaptics Scrolling Distance (268):	56, 56
	Synaptics Edge Scrolling (269):	0, 0, 0
	Synaptics Two-Finger Scrolling (270):	1, 0
	Synaptics Move Speed (271):	1.000000, 1.750000, 0.070572, 40.000000
	Synaptics Edge Motion Pressure (272):	30, 160
	Synaptics Edge Motion Speed (273):	1, 226
	Synaptics Edge Motion Always (274):	0
	Synaptics Off (275):	0
	Synaptics Locked Drags (276):	0
	Synaptics Locked Drags Timeout (277):	5000
	Synaptics Tap Action (278):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (279):	1, 1, 0
	Synaptics Circular Scrolling (280):	0
	Synaptics Circular Scrolling Distance (281):	0.100000
	Synaptics Circular Scrolling Trigger (282):	0
	Synaptics Circular Pad (283):	0
	Synaptics Palm Detection (284):	1
	Synaptics Palm Dimensions (285):	3, 200
	Synaptics Coasting Speed (286):	20.000000, 50.000000
	Synaptics Pressure Motion (287):		... of unknown type CARDINAL

	Synaptics Pressure Motion Factor (288):	1.000000, 1.000000
	Synaptics Resolution Detect (289):	1
	Synaptics Grab Event Device (290):	1
	Synaptics Gestures (291):	1
	Synaptics Capabilities (292):	1, 0, 1, 1, 1, 1, 1
	Synaptics Pad Resolution (293):	1, 1
	Synaptics Area (294):	0, 0, 0, 0
	Synaptics Noise Cancellation (295):	14, 14
	Device Product ID (249):	2, 14
	Device Node (250):	"/dev/input/event7"
```

Oh, I also get those *"[COLOR="#0000CD"]....lost sync at byte 6[/COLOR]"* errors occasionally, during which my touchpad freezes, but usually it gets back on track automatically after a freeze of 2-3 seconds. It usually happens when my system is overloaded with applications (usually while switching between them) or some naughty device (like my usb 3G modem) is connecting/disconnecting, and I very rarely need to unload --> reload the psmouse module. Usually it is just the 2-3 seconds that fix it automatically. So I consider that normal on my laptop here.

**EDIT:**
I have set the "PalmDetect=1" and "PalmMinWidth=3" values manually for my convenience, so those are not default values. Similarly, the speed and acceleration may also be non-default values. But I believe everything else is at defaults.


--

---

### Post by area51pilot on 2014-11-21
Im running kernel v3.18-rc4 on 14.04x64 and have done everything listed above and can only get touchpad to work as a basic mouse by editing grub. I'd really like to see full touchpad usability. This along with Bluetooth not working are my 2 major issues with this ultra book.

---

### Post by area51pilot on 2014-11-22
Varun .. I have the same output as you have, but my trackpad wont work. Everything I look at points to it being working, but it doesnt.  Trackpad is enabled, drivers loaded but no mouse, click or scroll functionality unless I load on startup as a basic psmouse device.

Any ideas?

---

### Post by area51pilot on 2015-03-05
This problem still exists for me even after updating to the latest kernel 3.19.  Any ideas on a fix? Bluetooth also stays disabled on this ASUS.

---

### Post by danylion on 2015-03-17
Having this same issue trying to patiently wait for a fix

---

### Post by paolopoz on 2015-04-07
Same problem here. I am looking for a way to fix it, if I find something useful I will post it here.

---

### Post by jorgepaulo on 2015-04-27
The fix at [https://bugzilla.kernel.org/show_bug.cgi?id=84491]("https://bugzilla.kernel.org/show_bug.cgi?id=84491") worked for me on an ASUS Flipbook TP500LA.

It consists of issuing the following command as root:

```
echo 1 > /sys/devices/platform/i8042/serio4/reg_07
```

You will likely need to re-issue the command at every reboot / resume.

Good luck,
Jorge

---

### Post by aljosa2 on 2015-04-28
hi,
i still didn't tried the 4.1-rc1 kernel, but i've been informed by the developers that the new kernel finally solves elantech touchpad problem :)

---

### Post by Carlos_Ortigoza_De on 2015-05-11
> **aljosa2 said:**
> hi,
i still didn't tried the 4.1-rc1 kernel, but i've been informed by the developers that the new kernel finally solves elantech touchpad problem :)

Hello friend. I have a Asus Q302LA and I don't have multitouch either... What version of the kernel is going to solve this touchpad problem? (as developers told you).

Thank you in advance for your help :)

---

### Post by Pilot6 on 2015-05-11
> **Carlos_Ortigoza_De said:**
> Hello friend. I have a Asus Q302LA and I don't have multitouch either... What version of the kernel is going to solve this touchpad problem? (as developers told you).

Thank you in advance for your help :)
What is your touchpad? Is it Elantech too?

---

### Post by aljosa2 on 2015-05-12
> **Carlos_Ortigoza_De said:**
> Hello friend. I have a Asus Q302LA and I don't have multitouch either... What version of the kernel is going to solve this touchpad problem? (as developers told you).

Thank you in advance for your help :)

I still didn't tried the new 4.1-rc3 (release candidate) kernel, but as soon as I upgraded kernel to 4.0.2 (stable), the Elantech touchpad problem disappeared :) :) :)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

---

### Post by bje24 on 2015-05-20
Thanks aljosa2! I have the exact same laptop and had the same touchpad problem as the original poster. I was surviving by having it register as a basic mouse on startup, but the lack of advanced control and the constant accidental activation by my palms while typing was driving me crazy.
upgrading to kernel 4.0.2 using the guide below and then rebooting has completely fixed it, and thankfully not caused any other problems, at least as far as I've noticed.

[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

---

### Post by aljosa2 on 2015-05-21
hi bje24,
once you start to use mainline kernel, you need to follow [kernel development]("https://lkml.org/") and accustom yourself to manual upgrades. for example, the latest stable mainline version is already v4.0.4-wily:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

once you installed the new kernel, and you find that everything is ok with your machine, here's how to remove old kernel(s):

> sudo apt-get --purge remove linux-headers-4.0.2-040002 linux-image-4.0.2-040002
sudo update-grub
sudo reboot


---

### Post by mwray on 2015-06-25
THANKS! That worked for me on openSUSE 13.2, the new 15.04 worked out of the box, but I hate the "Unity" environ, and EVERYTHING broke when I tried to use other desktop environs in Ubunutu. (ASUS TP500L i7,Broadwell)

> **jorgepaulo said:**
> The fix at [https://bugzilla.kernel.org/show_bug.cgi?id=84491]("https://bugzilla.kernel.org/show_bug.cgi?id=84491") worked for me on an ASUS Flipbook TP500LA.

It consists of issuing the following command as root:

```
echo 1 > /sys/devices/platform/i8042/serio4/reg_07
```

You will likely need to re-issue the command at every reboot / resume.

Good luck,
Jorge

---

