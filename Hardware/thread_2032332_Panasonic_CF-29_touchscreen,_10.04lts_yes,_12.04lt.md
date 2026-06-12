---
title: "Panasonic CF-29 touchscreen, 10.04lts yes, 12.04lts no"
date: 2012-07-23
forum: Hardware
---

### Post by nrKist on 2012-07-23
Hi all,
I have several partitions on my Panasonic CF-29 laptop and installed the new Xubuntu 12.04lts beside my existing Xubuntu 10.04lts. 

With 10.04 there was no support out of the box and I had to add 
evtouch, plus some settings in /etc/X11/xorg.conf, then all was well. All has been well with 10.04 ever since. 

With 12.04 there is touchscreen activity out of the box, but the calibration is way off. I see that evtouch is not part of the 12.04 repositories and there is no xorg.conf in 12.04. It _appears_ that evdev is handling this input now and evtest shows me touchscreen activity on event7. 

If evdev is indeed now handling my touchscreen input can anyone tell me how to calibrate devices in evdev? If it's not, can anyone tell me what is and how to calibrate that?

I'm trying to get on top of this as support for 10.04lts ceases in April of 2013 and I'm a touchscreen addict. It's amazing how many times I catch myself reaching for the screen when borrowing my wife's laptop. 


If it's relevant this is a Panasonic Toughbook CF-29 Mark IV with a LBPS/2 Fujitsu Lifebook TouchScreen.

Thank!

---

### Post by nrKist on 2012-07-24
Anyone?

---

### Post by Favux on 2012-07-26
Hi nrKist,

You are correct and evtouch has been deprecated and replaced by evdev.

Calibration we can do.  First what is the output of the following command in a terminal?
```
xinput list
```

---

### Post by nrKist on 2012-07-27
Thank you for dropping by. I appreciate the help. Here is the output. 

```
keith3@keith3-CF-29L4LGZBM:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Touchpad                           	id=10	[slave  pointer  (2)]
&#9116;   &#8627; LBPS/2 Fujitsu Lifebook TouchScreen     	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; Panasonic Laptop Support                	id=12	[slave  keyboard (3)]

```

Keith

---

### Post by Favux on 2012-07-27
Hi Keith,

Now we want to look at the list-props for the touchscreen:
```
xinput list-props "LBPS/2 Fujitsu Lifebook TouchScreen"
```
Or if the ID number hasn't changed (reboot or hotplug):
```
xinput list-props 11
```
I expect that will show us it is on the evdev driver.  Then we want to look at the Xorg.0.log in /var/log.  It is big so right click on it and Compress and attach to your next post.  Hopefully that will show us the touchscreen is being set up by evdev's touchscreen snippet.  Then using the info. we've collected we write a custom xorg.conf.d .conf file where we tell evdev what the coordinates are.  If it isn't able to determine them on its own.

---

### Post by nrKist on 2012-07-27
Here is the output of 'xinput list-props "LBPS/2 Fujitsu Lifebook TouchScreen"' 

'xinput list-props 11' gives the same result though I have rebooted.

```
keith3@keith3-CF-29L4LGZBM:~$ xinput list-props "LBPS/2 Fujitsu Lifebook TouchScreen"
Device 'LBPS/2 Fujitsu Lifebook TouchScreen':
	Device Enabled (154):	1
	Coordinate Transformation Matrix (156):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (275):	0
	Device Accel Constant Deceleration (276):	1.000000
	Device Accel Adaptive Deceleration (277):	1.000000
	Device Accel Velocity Scaling (278):	10.000000
	Device Product ID (271):	2, 9
	Device Node (272):	"/dev/input/event7"
	Evdev Axis Inversion (279):	0, 0
	Evdev Axis Calibration (280):	<no items>
	Evdev Axes Swap (281):	0
	Axis Labels (282):	"Abs X" (296), "Abs Y" (297)
	Button Labels (283):	"Button Unknown" (274), "Button Unknown" (274), "Button Unknown" (274), "Button Wheel Up" (160), "Button Wheel Down" (161)
	Evdev Middle Button Emulation (284):	0
	Evdev Middle Button Timeout (285):	50
	Evdev Third Button Emulation (286):	0
	Evdev Third Button Emulation Timeout (287):	1000
	Evdev Third Button Emulation Button (288):	3
	Evdev Third Button Emulation Threshold (289):	20
	Evdev Wheel Emulation (290):	0
	Evdev Wheel Emulation Axes (291):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (292):	10
	Evdev Wheel Emulation Timeout (293):	200
	Evdev Wheel Emulation Button (294):	4
	Evdev Drag Lock Buttons (295):	0

```




While I have attached a compressed Xorg.0.log, this appears to be the only segment that refers to the touchscreen.

```
[    16.242] (II) config/udev: Adding input device LBPS/2 Fujitsu Lifebook TouchScreen (/dev/input/event7)
[    16.242] (**) LBPS/2 Fujitsu Lifebook TouchScreen: Applying InputClass "evdev touchscreen catchall"
[    16.242] (II) Using input driver 'evdev' for 'LBPS/2 Fujitsu Lifebook TouchScreen'
[    16.242] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.242] (**) LBPS/2 Fujitsu Lifebook TouchScreen: always reports core events
[    16.242] (**) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: Device: "/dev/input/event7"
[    16.242] (--) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: Vendor 0x2 Product 0x9
[    16.243] (--) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: Found absolute axes
[    16.243] (--) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: Found x and y absolute axes
[    16.243] (--) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: Found absolute touchscreen
[    16.243] (II) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: Configuring as touchscreen
[    16.243] (**) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: YAxisMapping: buttons 4 and 5
[    16.243] (**) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.243] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    16.243] (II) XINPUT: Adding extended input device "LBPS/2 Fujitsu Lifebook TouchScreen" (type: TOUCHSCREEN, id 11)
[    16.243] (II) evdev: LBPS/2 Fujitsu Lifebook TouchScreen: initialized for absolute axes.
[    16.243] (**) LBPS/2 Fujitsu Lifebook TouchScreen: (accel) keeping acceleration scheme 1
[    16.243] (**) LBPS/2 Fujitsu Lifebook TouchScreen: (accel) acceleration profile 0
[    16.243] (**) LBPS/2 Fujitsu Lifebook TouchScreen: (accel) acceleration factor: 2.000
[    16.243] (**) LBPS/2 Fujitsu Lifebook TouchScreen: (accel) acceleration threshold: 4
[    16.243] (II) config/udev: Adding input device LBPS/2 Fujitsu Lifebook TouchScreen (/dev/input/mouse1)

```

---

### Post by Favux on 2012-07-27
I'm guessing LBPS/2 = Lifebook PS/2 TouchScreen.  Do you know?

Also the kernel serio driver was alread there for you, correct?  You didn't have to add it did you?
> [    16.243] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"

It all seems good.  On evdev and the Xorg.0.log shows:
> [    16.242] (II) config/udev: Adding input device LBPS/2 Fujitsu Lifebook TouchScreen (/dev/input/event7)
[    16.242] (**) LBPS/2 Fujitsu Lifebook TouchScreen: Applying InputClass "evdev touchscreen catchall"
[    16.242] (II) Using input driver 'evdev' for 'LBPS/2 Fujitsu Lifebook TouchScreen'
Showing the 10-evdev.conf snippet MatchIsTouchscreen is matching.  And axes are Absolute.

So from:  [http://www.kubuntuforums.net/showthread.php?49066-touchscreen-problems-%28-panasonic-CF-29-%29](http://www.kubuntuforums.net/showthread.php?49066-touchscreen-problems-%28-panasonic-CF-29-%29)  I got some coordinates.  You could use xinput_calibrator.

You may need to create the xorg.conf.d directory in /etc/X11.  Then create your custom .conf file in it:
```
gksudo gedit /etc/X11/xorg.conf.d/52-fujitsu-touchscreen.conf
```
And for the contents use this snippet:
```
Section "InputClass"
        Identifier "Fujitsu touchscreen options"
        MatchIsTouchscreen = "on"
        MatchProduct "LBPS/2 Fujitsu Lifebook TouchScreen"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "240 3900 220 3800"
EndSection
```
And restart with crossed fingers.

---

### Post by nrKist on 2012-07-28
I'll start with the most important part of the reply. It is now properly calibrated! Thank you!


I don't know for certain but I, like you, do think LBPS/2 stands for Lifebook PS/2.

You were correct that I did not have to add the kernel serio driver. Also correct that I had to create the xorg.conf.d directory. 

I created the 52-fujitsu-touchscreen.conf file and rebooted. The screen went blank just after the booting splash screen and remained that way until I forced a shutdown. Booted into 10.04, renamed 52-fujitsu-touchscreen.conf, rebooted. 

Then went with your other suggestion of installing and running xinput_calibrator. Followed its directions, rebooted, my touchscreen is now dead on. 

So again, thanks!
Keith

---

### Post by Favux on 2012-07-28
Hi Keith,

Great.  :)

Could you please post the .conf file you created with the xinput_calibrator coordinates?  That will help others.  Sounds like the ones I found didn't work too well.

---

### Post by nrKist on 2012-07-28
Certainly. After running xinput_calibrator from a terminal it told me to create /etc/X11/xorg.conf.d/99-calibration.conf and paste the following into it.

```
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "LBPS/2 Fujitsu Lifebook TouchScreen"
        Option  "Calibration"   "302 4002 275 3879"
EndSection

```

---

