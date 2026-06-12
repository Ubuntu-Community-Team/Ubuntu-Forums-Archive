---
title: "xsetwacom does not show intuos5"
date: 2013-07-13
forum: Hardware
---

### Post by nwillis on 2013-07-13
I had my Intuos 5 working fine in 12.10; dist-upgraded a few weeks ago to 13.04, and now nada.  I'm still trying to figure out where the problem is.  It shows up in lsusb, but xsetwacom --list devices returns nothing.

xinput --list shows this:
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; 3Dconnexion SpaceNavigator              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Trackball Explorer®	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch L Pen               	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos5 touch L Finger            	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; PWC snapshot button                     	id=10	[slave  keyboard (3)]
    &#8627; Mitsumi Electric Goldtouch USB Keyboard 	id=13	[slave  keyboard (3)]

Since all the howto threads use xsetwacom to config things, I'm not sure how to proceed at this stage.  Help?

---

### Post by Favux on 2013-07-13
Hi nwillis,

The results of **xinput list** seem to indicate xf86-input-wacom (xorg-xserver-input-wacom) isn't installed, which makes no sense.  For example for the stylus device name you should see stylus appended:
```
Wacom Intuos5 touch L Pen stylus
```
And the same with other devices such as:
```
Wacom Intuos5 touch L Pen eraser

Wacom Intuos5 touch L Finger touch
```
Not sure what parent device pad would be appended to with the Intuos5.

What does:
```
xsetwacom -V
```
in a terminal return?

---

### Post by nwillis on 2013-07-13
Well, xserver-xorg-input-wacom is most definitely installed.  xsetwacom -V reports 
0.19.0

---

### Post by Favux on 2013-07-13
OK.  It shouldn't be the kernel driver because you're seeing the parent devices.  Let's check if it is auto-loading anyway.  You should see it (wacom) in **lsmod** or try:
```
lsmod | grep [Ww]acom
```

What Desktop are you using for Raring?  Unity?

---

### Post by nwillis on 2013-07-13
Yep, it's loading all right.
wacom                  57412  0 

And yeah, standard Unity; no other special bits (or, certainly not at the system plumbing layer)....

---

### Post by Favux on 2013-07-14
Still not making much sense.  Are you getting error messages in /var/log/Xorg.0.log?  Would have to be something about the Wacom X driver dropping the Intuos5.  May want to turn up the verbosity to 12, see **man wacom** rather than **man xsetwacom** for the debug parameters.  If you're hotplugging through a hub try directly into a usb port on the computer and make sure the cable is securely seated both ends.

Doubt it is an xsetwacom version conflict.  You didn't try to compile xf86-input-wacom did you?  If so make sure there is only one executable xsetwacom binary in /usr/bin of the right date and not another one in /usr/local/bin.

Does the Gnome Wacom configuration gui in System Settings correctly identify your Intuos5?  I'm not sure what checking the dconf settings for it in org.gnome.settings-daemon with dconf-editor gets us.

You could try reinstalling the xserver-xorg-input-wacom package and see if that gets you anything or maybe compile the 0.22.0 tar release.

---

### Post by nwillis on 2013-07-15
Not getting errors; get a lot of log messages, though -- e.g.:
[690354.829] (II) config/udev: Adding input device Wacom Intuos5 touch L Pen (/dev/input/event5)
[690354.830] (**) Wacom Intuos5 touch L Pen: Applying InputClass "evdev tablet catchall"
[690354.830] (II) Using input driver 'evdev' for 'Wacom Intuos5 touch L Pen'
[690354.830] (**) Wacom Intuos5 touch L Pen: always reports core events
[690354.830] (**) evdev: Wacom Intuos5 touch L Pen: Device: "/dev/input/event5"
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Vendor 0x56a Product 0x28
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Found 13 mouse buttons
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Found scroll wheel(s)
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Found relative axes
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Found absolute axes
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Found x and y absolute axes
[690354.830] (--) evdev: Wacom Intuos5 touch L Pen: Found absolute tablet.
[690354.830] (II) evdev: Wacom Intuos5 touch L Pen: Configuring as tablet
[690354.830] (II) evdev: Wacom Intuos5 touch L Pen: Adding scrollwheel support
[690354.830] (**) evdev: Wacom Intuos5 touch L Pen: YAxisMapping: buttons 4 and 5
[690354.830] (**) evdev: Wacom Intuos5 touch L Pen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[690354.830] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4/1-3.4.2/1-3.4.2:1.0/input/input16/event5"
[690354.830] (II) XINPUT: Adding extended input device "Wacom Intuos5 touch L Pen" (type: TABLET, id 8)

Obviously those are from evdev ... that doesn't seem right.  No, I haven't compiled xf86 packages locally, and no, the System Settings GUI does not see the Inutos5 -- in fact, that was the first sign I saw that things weren't working after the upgrade.  And I do agree that it doesn't make much sense....

Nate

---

### Post by Favux on 2013-07-15
You are correct and you shouldn't be seeing the 10-evdev.conf "evdev tablet catchall" snippet.  Unless you added a custom evdev .conf file to /etc/X11/xorg.conf.d that included it, over riding the wacom.conf.  Anyway the match to the evdev X driver explains why you're just seeing the parent devices because the Wacom X driver is what appends stylus, eraser, pad, and touch.  So that indicates either the 50-wacom.conf is missing from /usr/share/X11/xorg.conf.d or for some reason the usb tablet snippet that should provide a match isn't.  If the wacom.conf is there post its contents.

---

### Post by nwillis on 2013-07-15
It's there::

Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL|ISD-V4"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
        Driver "wacom"
EndSection

# Waltop tablets
Section "InputClass"
	Identifier "Waltop class"
	MatchProduct "WALTOP"
	MatchIsTablet "on"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

Are you saying that the evdev driver shouldn't grab the Wacom device to begin with?  Or that the wacom.conf file is supposed to match and take it back?  Because the order is clearly evedev-first, and I'm positive I haven't altered either file.

---

### Post by Favux on 2013-07-15
The wacom.conf should match and take it back because it is executed last.  And what's executed last controls.  In Xorg.0.log you should just see it saying something about matching to the wacom module i.e. Wacom X driver.  Shouldn't see any entries where the evdev driver is being applied.  There should be a line where the "evdev tablet catchall" is matched followed immediately by a line where the "Wacom class" snippet is matched.

Your 50-wacom.conf contents are basically the same as the current ones and you should be matching at least the keyword 'Wacom' in the usb snippet:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
That seems to leave your Wacom X driver install is broken, I guess.  But I would think you still should see the "Wacom class" match.  Did you try reinstalling it yet?

---

### Post by nwillis on 2013-07-15
Not yet; I wasn't keen on reinstalling without narrowing down the possible culprits a bit further.  It may be a few hours before I can tackle that -- work and all.

---

### Post by nwillis on 2013-07-15
Well, that didn't do much:
[877541.258] (II) config/udev: Adding input device Wacom Intuos5 touch L Pen (/dev/input/mouse1)
[877541.258] (II) No input driver specified, ignoring this device.
[877541.258] (II) This device may have been added with another device file.
[877541.259] (II) config/udev: Adding input device Wacom Intuos5 touch L Finger (/dev/input/mouse2)
[877541.260] (**) Wacom Intuos5 touch L Finger: Ignoring device from InputClass "touchpad ignore duplicates"
[877541.260] (II) config/udev: Adding input device Wacom Intuos5 touch L Pen (/dev/input/event5)
[877541.260] (**) Wacom Intuos5 touch L Pen: Applying InputClass "evdev tablet catchall"
[877541.260] (II) Using input driver 'evdev' for 'Wacom Intuos5 touch L Pen'
[877541.260] (**) Wacom Intuos5 touch L Pen: always reports core events
[877541.260] (**) evdev: Wacom Intuos5 touch L Pen: Device: "/dev/input/event5"
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Vendor 0x56a Product 0x28
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Found 13 mouse buttons
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Found scroll wheel(s)
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Found relative axes
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Found absolute axes
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Found x and y absolute axes
[877541.261] (--) evdev: Wacom Intuos5 touch L Pen: Found absolute tablet.
[877541.261] (II) evdev: Wacom Intuos5 touch L Pen: Configuring as tablet
[877541.261] (II) evdev: Wacom Intuos5 touch L Pen: Adding scrollwheel support
[877541.261] (**) evdev: Wacom Intuos5 touch L Pen: YAxisMapping: buttons 4 and 5
[877541.261] (**) evdev: Wacom Intuos5 touch L Pen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[877541.261] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4/1-3.4.2/1-3.4.2:1.0/input/input19/event5"
[877541.261] (II) XINPUT: Adding extended input device "Wacom Intuos5 touch L Pen" (type: TABLET, id 8)
[877541.261] (WW) evdev: Wacom Intuos5 touch L Pen: touchpads, tablets and touchscreens ignore relative axes.
[877541.261] (II) evdev: Wacom Intuos5 touch L Pen: initialized for absolute axes.
[877541.264] (**) Wacom Intuos5 touch L Pen: (accel) keeping acceleration scheme 1
[877541.264] (**) Wacom Intuos5 touch L Pen: (accel) acceleration profile 0
[877541.264] (**) Wacom Intuos5 touch L Pen: (accel) acceleration factor: 2.000
[877541.264] (**) Wacom Intuos5 touch L Pen: (accel) acceleration threshold: 4
[877541.268] (II) config/udev: Adding input device Wacom Intuos5 touch L Finger (/dev/input/event6)
[877541.268] (**) Wacom Intuos5 touch L Finger: Applying InputClass "evdev touchpad catchall"
[877541.269] (**) Wacom Intuos5 touch L Finger: Applying InputClass "touchpad catchall"
[877541.269] (**) Wacom Intuos5 touch L Finger: Applying InputClass "Default clickpad buttons"
[877541.269] (II) Using input driver 'synaptics' for 'Wacom Intuos5 touch L Finger'
[877541.269] (**) Wacom Intuos5 touch L Finger: always reports core events
[877541.269] (**) Option "Device" "/dev/input/event6"
[877541.298] (--) synaptics: Wacom Intuos5 touch L Finger: x-axis range 0 - 4096
[877541.298] (--) synaptics: Wacom Intuos5 touch L Finger: y-axis range 0 - 4096
[877541.298] (II) synaptics: Wacom Intuos5 touch L Finger: device does not report pressure, will use touch data.
[877541.298] (II) synaptics: Wacom Intuos5 touch L Finger: device does not report finger width.
[877541.298] (--) synaptics: Wacom Intuos5 touch L Finger: buttons: double triple
[877541.298] (--) synaptics: Wacom Intuos5 touch L Finger: Vendor 0x56a Product 0x28
[877541.298] (--) synaptics: Wacom Intuos5 touch L Finger: invalid pressure range.  defaulting to 0 - 255
[877541.299] (--) synaptics: Wacom Intuos5 touch L Finger: invalid finger width range.  defaulting to 0 - 15
[877541.299] (--) synaptics: Wacom Intuos5 touch L Finger: touchpad found
[877541.299] (**) Wacom Intuos5 touch L Finger: always reports core events
[877541.301] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.4/1-3.4.2/1-3.4.2:1.1/input/input20/event6"
[877541.301] (II) XINPUT: Adding extended input device "Wacom Intuos5 touch L Finger" (type: TOUCHPAD, id 9)
[877541.301] (**) synaptics: Wacom Intuos5 touch L Finger: (accel) MinSpeed is now constant deceleration 2.5
[877541.301] (**) synaptics: Wacom Intuos5 touch L Finger: MaxSpeed is now 1.75
[877541.301] (**) synaptics: Wacom Intuos5 touch L Finger: AccelFactor is now 0.035
[877541.305] (**) Wacom Intuos5 touch L Finger: (accel) keeping acceleration scheme 1
[877541.305] (**) Wacom Intuos5 touch L Finger: (accel) acceleration profile 1
[877541.305] (**) Wacom Intuos5 touch L Finger: (accel) acceleration factor: 2.000
[877541.305] (**) Wacom Intuos5 touch L Finger: (accel) acceleration threshold: 4
[877541.306] (--) synaptics: Wacom Intuos5 touch L Finger: touchpad found

Just out of curiosity, are you running 64-bit?  Because I know the total population of Intuos users running 13.04 must be pretty small; there's certainly the possibility that there's an undiscovered bug.  Is it possible there's a problem with one of the other .conf files, and that it isn't loading the higher-numbered ones?  Obvioulsy it's getting to 50-synaptics.conf; I just wonder.  Alphabetically, there's one in between -- 50-vmmouse.conf, which I presume was installed by VMware or something like that...  I guess if it wasn't loading/parsing the wacom conf file correctly, I'm not sure where it would throw the error....

---

### Post by Favux on 2013-07-15
Yes, I use 64-bit but I have an Intuos4 not 5.  For multitouch I have one of the new BambooPTs.  Several of the developers have Intuos5's so if there is a bug it is likely Ubuntu specific.  But I think Jason spends at least some time in Ubuntu, so I'd think he would catch a problem.

It still looks to me like a match isn't happening.  Let's try a custom .conf in /etc/X11/xorg.conf.d.  You may have to create the xorg.conf.d directory.  Use the usb snippet from earlier and call it say 52-wacom.conf.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
```
gksudo gedit /etc/X11/xorg.conf.d/52-wacom.conf
```

The parent devices in **xinput list** should be the device names the kernel is announcing so I don't understand why there isn't a match.  The only naming problem I remember was the bluetooth Intuos4, hence the temporary PTK-540WL in the match until it is fixed in the kernel.  But I don't follow the kernel stuff closely so maybe I missed something.  The Gnome configuration applet adds another layer of variables.  I'm wondering if that is somehow the problem.  Maybe there isn't a libwacom data file for your tablet or the match is wrong and somehow that's throwing a spanner in the works.  Maybe we should try turning it off.  Anyway lets get the PID from your **lsusb** output,  so post the wacom line.

---

### Post by nwillis on 2013-07-16
Just to be perfectly clear, you're suggesting putting the config in /etc/X11/* rather than in /usr/share/X11/* ?  And keeping the existing xorg.conf.d directory in /usr/share?

---

### Post by Favux on 2013-07-16
Right, /etc runs after /usr so a .conf file there controls and that's where user custom ones are suppose to go.  If you don't get a match then we can experiment a little with the matching line and see if we can come up with something that works.  Different keywords or maybe MatchVendor or some such.

---

### Post by Vinca on 2013-07-16
[http://ubuntuforums.org/showthread.php?t=2162808](http://ubuntuforums.org/showthread.php?t=2162808)

I probably have the same problem.  Just found this thread. What do you think? Which of these ideas should I try?

Bus 002 Device 006: ID 056a:00de Wacom Co., Ltd 

Thanks so much

vinca

---

