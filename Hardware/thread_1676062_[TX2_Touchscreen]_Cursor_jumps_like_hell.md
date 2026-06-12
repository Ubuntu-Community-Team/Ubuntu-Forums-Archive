---
title: "[TX2 Touchscreen] Cursor jumps like hell"
date: 2011-01-26
forum: Hardware
---

### Post by eNoVa on 2011-01-26
Hello guys,
after i got my HP TX2 - 1150eg repair service(they changed Motherboard because my TX2 didn't boot anymore) back, my Cursor makes me go wild!

But the curious thing is, it does only happen on some Applications like Internet Browser(in FF more than in chrome and gets heavier if the Cursor is over a Flash-app), screensaver and the "Loginscreen which appears after inactivity".
In all other cases my Touchsreeen works correctly, so it isn't a hardware issue.

The second thing i've recognized is, i "lost" about a fingertip of screen of the Left Side of the Touchscreen. It is touchable but the cursor does not "reach" the clicked point(stylus and other pointer do).

And the last strange thing i've noticed is, if i trigger a click with my stylus, it does not release anymore and in some of this cases the keyboard stops working simultaneously (sometimes control+alt+backspace still works and fixes the state).

So i wonder if someone could help, give me a hint how to fix this problem.

thanking in advance

eNoVa

ps: im using a Fresh installed Ubuntu 10.10 and Windows is banished from my Hard disk.

pps: does anybody know how to check the Touchscreen Firmware on Linux is it possible to install one without Windows?

Edit: Magick-Rotation does not Rotate after rotating the screen, but worked before...

---

### Post by Ayuthia on 2011-01-28
> **eNoVa said:**
> Hello guys,
after i got my HP TX2 - 1150eg repair service(they changed Motherboard because my TX2 didn't boot anymore) back, my Cursor makes me go wild!

But the curious thing is, it does only happen on some Applications like Internet Browser(in FF more than in chrome and gets heavier if the Cursor is over a Flash-app), screensaver and the "Loginscreen which appears after inactivity".
In all other cases my Touchsreeen works correctly, so it isn't a hardware issue.

The second thing i've recognized is, i "lost" about a fingertip of screen of the Left Side of the Touchscreen. It is touchable but the cursor does not "reach" the clicked point(stylus and other pointer do).

And the last strange thing i've noticed is, if i trigger a click with my stylus, it does not release anymore and in some of this cases the keyboard stops working simultaneously (sometimes control+alt+backspace still works and fixes the state).

So i wonder if someone could help, give me a hint how to fix this problem.

thanking in advance

eNoVa

ps: im using a Fresh installed Ubuntu 10.10 and Windows is banished from my Hard disk.

pps: does anybody know how to check the Touchscreen Firmware on Linux is it possible to install one without Windows?

Edit: Magick-Rotation does not Rotate after rotating the screen, but worked before...

Do you know what the touchscreen hardware is for it?  Is it the N-trig?  If so, you should be able to get the firmware version from dmesg.  Just look for some variation of N-trig (n-trig, ntrig, N-Trig, etc.) and it should show the firmware version.

The touch portion could just be an issue with the calibration.  You might want to provide the xinput --list information and then we can look at the properties of the touch and stylus to see if it is set up correctly.

As far as I know, the firmware installation can only be done in Windows.  At least that is for the N-trig versions.

As for Magick-Rotation, which version are you using?  It might be a matter of the hp-wmi driver needing to be loaded.  You can check to see if it is loaded:
```

lsmod|grep wmi

```

---

### Post by eNoVa on 2011-01-29
Thanks for responding,
Firmwareversion of my N-Trig device is 4.6.5.8.5,
hp_wmi is not loaded; modprobe hp_wmi seem not to change hp_wmi state.


Below my XInput output :

```

Device 'N-Trig Touchscreen':
	Device Enabled (148):	1
	Coordinate Transformation Matrix (150):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (269):	0
	Device Accel Constant Deceleration (270):	1.000000
	Device Accel Adaptive Deceleration (271):	1.000000
	Device Accel Velocity Scaling (272):	10.000000
	Evdev Reopen Attempts (267):	10
	Evdev Axis Inversion (298):	0, 0
	Evdev Axis Calibration (299):	<no items>
	Evdev Axes Swap (300):	0
	Axis Labels (301):	"Abs X" (273), "Abs Y" (274), "None" (0), "None" (0)
	Button Labels (302):	"Button 0" (311), "Button Unknown" (297), "Button Unknown" (297), "Button Wheel Up" (154), "Button Wheel Down" (155)
	Evdev Middle Button Emulation (303):	2
	Evdev Middle Button Timeout (304):	50
	Evdev Wheel Emulation (305):	0
	Evdev Wheel Emulation Axes (306):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (307):	10
	Evdev Wheel Emulation Timeout (308):	200
	Evdev Wheel Emulation Button (309):	4
	Evdev Drag Lock Buttons (310):	0

```

```

'N-Trig MultiTouch':
	Device Enabled (148):	1
	Coordinate Transformation Matrix (150):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (269):	0
	Device Accel Constant Deceleration (270):	1.000000
	Device Accel Adaptive Deceleration (271):	1.000000
	Device Accel Velocity Scaling (272):	10.000000
	Evdev Reopen Attempts (267):	10
	Evdev Axis Inversion (298):	0, 0
	Evdev Axis Calibration (299):	<no items>
	Evdev Axes Swap (300):	0
	Axis Labels (301):	"Abs X" (273), "Abs Y" (274), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Button Labels (302):	"Button Unknown" (297), "Button Unknown" (297), "Button Unknown" (297), "Button Wheel Up" (154), "Button Wheel Down" (155)
	Evdev Middle Button Emulation (303):	2
	Evdev Middle Button Timeout (304):	50
	Evdev Wheel Emulation (305):	0
	Evdev Wheel Emulation Axes (306):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (307):	10
	Evdev Wheel Emulation Timeout (308):	200
	Evdev Wheel Emulation Button (309):	4
	Evdev Drag Lock Buttons (310):	0

```

```

Device 'N-Trig Pen stylus':
	Device Enabled (148):	1
	Coordinate Transformation Matrix (150):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (269):	0
	Device Accel Constant Deceleration (270):	1.000000
	Device Accel Adaptive Deceleration (271):	1.000000
	Device Accel Velocity Scaling (272):	10.000000
	Wacom Tablet Area (278):	0, 0, 9600, 7200
	Wacom Rotation (279):	0
	Wacom Pressurecurve (280):	0, 0, 100, 100
	Wacom Serial IDs (281):	1, 0, 2, 0
	Wacom TwinView Resolution (282):	0, 0, 0, 0
	Wacom Display Options (283):	-1, 0, 1
	Wacom Screen Area (284):	0, 0, 1280, 800
	Wacom Proximity Threshold (285):	42
	Wacom Capacity (286):	-1
	Wacom Pressure Threshold (287):	27
	Wacom Sample and Suppress (288):	2, 4
	Wacom Enable Touch (289):	0
	Wacom Hover Click (290):	1
	Wacom Enable Touch Gesture (291):	0
	Wacom Touch Gesture Parameters (292):	50, 20, 250
	Wacom Tool Type (293):	"STYLUS" (295)
	Wacom Button Actions (294):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)


```

Thanks in Advance
eNoVa

---

### Post by Ayuthia on 2011-01-29
You might try this [link]("https://wiki.ubuntu.com/Multitouch/Calibration/Ntrig") to see if it fixes the touch.

As for hp_wmi, since it is not loading automatically you will want to add it to /etc/modules:
```

cat hp_wmi|sudo tee -a /etc/modules

```
This is needed so that magick-rotation will be able to read the swivel events.

Which version of magick-rotation do you have?  The reason I ask is because the current version (1.2) needs to have checkmagick32/64 compiled or else it does not work.

---

### Post by eNoVa on 2011-01-31
I got the latest version(**1.3**) of Magick-rotation installed.
I think hp_wmi cant be loaded because its not on my system, despite
it is listened in lsmod.

Unfortunally, your links did not affect the calibration of my Touchscreen...

But could it be that the errors can be fixed with xorg.conf?
Yesterday, i was setting up a second Display (dualview) and i noticed, if i dont use fgrlx, my cursor does not jump.
Im mazed? Is there an explanation out there?

greez

---

### Post by Ayuthia on 2011-02-05
> **eNoVa said:**
> I got the latest version(**1.3**) of Magick-rotation installed.
I think hp_wmi cant be loaded because its not on my system, despite
it is listened in lsmod.

Unfortunally, your links did not affect the calibration of my Touchscreen...

But could it be that the errors can be fixed with xorg.conf?
Yesterday, i was setting up a second Display (dualview) and i noticed, if i dont use fgrlx, my cursor does not jump.
Im mazed? Is there an explanation out there?

greez

It sounds like the symbolic link that points to the swivel event is not there.  Can you post the results of:
```

ls -l /dev/input

```

As for the calibration, it sounds like we will need to adjust the Evdev Axis Calibration value.  Right now I am not able to look up how to configure this, but if I remember correctly it is something like:
```

xinput --set-prop "N-Trig MultiTouch" "Evdev Axis Calibration" 0 0 1280 800

```
but I am not 100% sure.  The information might be in the man pages (man evdev).

As for the fglrx, I have not seen this but I have not tried fglrx with an external monitor either.

---

### Post by Huss on 2011-02-07
Hi eNoVa, Ayuthia and other touchscreen users,

I am having a similar issue. For me, the touch screen works well for a while and then starts to get erratic. Erratic behavior includes random clicks in the upper left hand side of the screen and, in web browsers, it is like the middle button has been pressed and scrolling follows mouse movement. 

I am using ubuntu 10.10, with the windows 7 n-trig firmware. Also using GINN, but behavior is still erratic if GINN turned off.

Any workarounds would be appreciated.

P.S. Also, is anyone interested in having the feature where a keyboard/handwriting option appears on a textbox click? Is there something that can be borrowed from android on this? Share your thoughts on the following thread: [http://ubuntuforums.org/showthread.php?p=10307789#post10307789](http://ubuntuforums.org/showthread.php?p=10307789#post10307789)

---

### Post by Ayuthia on 2011-02-07
> **Huss said:**
> Hi eNoVa, Ayuthia and other touchscreen users,

I am having a similar issue. For me, the touch screen works well for a while and then starts to get erratic. Erratic behavior includes random clicks in the upper left hand side of the screen and, in web browsers, it is like the middle button has been pressed and scrolling follows mouse movement. 


You will find this behavior known as "ghost touches" if you search around.  It seems to happen in Windows and in Linux and seems to be tied into the firmware.  I have found that the 2.239 version from HP has been the most stable for me.  I am also using the open source radeon driver instead of fglrx.

Are you using the fglrx driver or the radeon version?  Also which firmware version are you using?  If you are not sure, you can find it in dmesg (dmesg|grep -i ntrig).  Can you also let us know which BIOS version you are using?  I have not seen any of the ghost touches with this firmware but of course, each laptop is different.

---

### Post by Favux on 2011-02-07
Hi Huss,

I'm wondering if your digitizer hasn't picked up noise that needs to be "degaussed".  Linked in the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1") and on the [Ubuntu multitouch wiki]("https://wiki.ubuntu.com/Multitouch/Calibration/Ntrig").

---

### Post by Huss on 2011-02-08
Thanks for the quick replies,

I am using the latest 64bit firmware for my TouchSmartTX2, installed through Windows 7. Version # 2.239. It seems as though I am using the Radeon driver. fglrx-modaliase is installed though. I will try changing drivers and see how I go. I will look at the degassing option if the driver doesn't do the job.

Thanks again

---

### Post by Huss on 2011-02-08
After installing fglrx from Synaptic the touch screen is working much better, no ghost clicks. I must have missed a step with changing the drivers over, because now my system is acting as though there is no graphics acceleration. ATI control centre does not open, stating missing drivers. Visual effects can't be enabled. Also, the boot up and shut down screens are now a little rougher and the system doesn't shut down - just hangs on a black screen.

Is it a conflicting driver issue? I couldn't find a radeon driver to remove...

---

### Post by Favux on 2011-02-08
I'm not sure what that's indicating.  The proprietary driver isn't installed correctly?  Froms Synaptics?  Don't you still get the ATI "flgrx" from Hardware Drivers.

Anyway you may several ATI OSS drivers installed by default.  Their names would be something like:
xserver-xorg-video-ati
xserver-xorg-video-radeon
xserver-xorg-video-radeonhd

---

### Post by Huss on 2011-02-08
I will try and remove the old radeon drivers later today. Thanks

---

### Post by Huss on 2011-02-10
Removing the old drivers didn't do the job. Any other ideas?

---

### Post by Ayuthia on 2011-02-10
Is the fglrx driver loading (in lsmod)?  If so, have you tried:
```

sudo aticonfig --initial

```

You might also check to see what is showing up in /var/log/Xorg.0.log.  It should provide some clue about what is happening.

---

### Post by Huss on 2011-02-10
Thanks Ayuthia,

That did the job. 

```
uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0
```

Hopefully all will go well from here!

---

