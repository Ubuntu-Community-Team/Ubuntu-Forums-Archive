---
title: "Wacom Intuos4 is not working properly"
date: 2011-04-25
forum: Hardware
---

### Post by Rayleen on 2011-04-25
Hi, thanks for your attention. I have a Wacom Intuos4 and a few problems with it, and I'd want to know if someone can help me, I'm using Ubuntu 10.04 LTS (Lucid Lynx(, and I'm not the root.

When I first bought it I installed the drivers and all that I needed and it worked perfectly. GIMP had no problems detecting the pressure and all, but I have to use some concrete Windows programs due to school works so I usually run them with Wine. The pressure didn't work in any of the Windows programs so I told my father that he could try installing VirtualBox (he's the root) because I heard it could solve my problem, and plus our computer has enough capacity. He said it wasn't necessary and that he could solve it, that was when the problems begun.

He begun trying things and the result was that GIMP did not detect the pressure anymore, then he tried undoing it and the eraser tip stopped working independiently. He did more changes and the buttons stopped working almost completely (when I touch anyone of them, even the wheel the cursor runs to the upper left corner of the screen). And now when I touch the tablet with the pen to click, then I have to elevate it like 5cm or it won't recognize the pen again. It's exasperating.

The tablet works perfectly OK on the netbook, so the problem must be the computer. I need your help, please. My father touched so many things I don't even know where to begin with, and plus I do not have root powers so I can't do a lot of things. I tried looking over the internet but none of the things I tried worked. I don't even know where's the problem and I don't wanna ask my father for help 'cause he already messed it up too much, I don't want one of my most useful work tools to stop working :(

Thank you very much! And sorry for my english, I'm not a native speaker :oops:

---

### Post by Favux on 2011-04-25
Hi Rayleen,

Welcome to Ubuntu forums!

Your English is fine.  We may not be able to fix it, since you are not root.  But we may be able to find the problem.

I suspect from your description the tablet is no longer on the Wacom X driver.  Let's do some diagnostics.  Enter in a terminal:
```
xinput list
```
and post the output.

---

### Post by Rayleen on 2011-04-25
That was fast! Thank you =')

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6                       	id=8	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-04-25
Alright, now run this command and post the output:
```
xinput list-props "Wacom Intuos4 4x6"
```
If the tablet was on the Wacom X driver we should probably be seeing 3 input devices ending with stylus, eraser, and pad.

---

### Post by Rayleen on 2011-04-25
```
Device 'Wacom Intuos4 4x6':
	Device Enabled (121):	1
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (262):	1.000000
	Device Accel Velocity Scaling (263):	10.000000
	Evdev Reopen Attempts (238):	10
	Evdev Axis Inversion (264):	0, 0
	Evdev Axis Calibration (265):	<no items>
	Evdev Axes Swap (266):	0
	Axis Labels (267):	"Abs X" (249), "Abs Y" (250), "Abs Z" (251), "Abs Rotary Z" (252), "Abs Throttle" (253), "Abs Wheel" (254), "Abs Pressure" (255), "Abs Distance" (256), "Abs Tilt X" (257), "Abs Tilt Y" (258), "None" (0)
	Button Labels (268):	"Button Left" (122), "Button Middle" (123), "Button Right" (124), "Button Wheel Up" (125), "Button Wheel Down" (126), "Button Horiz Wheel Left" (127), "Button Horiz Wheel Right" (128), "Button Side" (247), "Button Extra" (248), "Button 5" (245), "Button 6" (246), "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239), "Button Unknown" (239)
	Evdev Middle Button Emulation (269):	2
	Evdev Middle Button Timeout (270):	50
	Evdev Wheel Emulation (271):	0
	Evdev Wheel Emulation Axes (272):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (273):	10
	Evdev Wheel Emulation Timeout (274):	200
	Evdev Wheel Emulation Button (275):	4
	Evdev Drag Lock Buttons (276):	0
```

---

### Post by Favux on 2011-04-25
As you can see the tablet is on the evdev X driver not the Wacom X driver.

So let's see if we can find out why.  Since you are in Lucid the wacom.conf file in xorg.conf.d to configure the tablet (place it on the wacom driver) should be called 10-wacom.conf and located at /usr/lib/X11/xorg.conf.d.  Check there to see if it is there.  If it is open it up in gedit (the text editor) and post the contents.

---

### Post by Rayleen on 2011-04-26
The file was there, yep. Here are the contents:

```
#Section "InputClass"
#	Identifier "Wacom class"
#	MatchProduct "Wacom|WACOM"
#	MatchDevicePath "/dev/input/event*"
#	Driver "wacom"
#EndSection
#
#Section "InputClass"
#	Identifier "Wacom serial class"
#	MatchProduct "Serial Wacom Tablet"
#	Driver "wacom"
#	Option "ForceDevice" "ISDV4"
#EndSection
#
## N-Trig Duosense Electromagnetic Digitizer
#Section "InputClass"
#	Identifier "Wacom N-Trig class"
#	MatchProduct "HID 1b96:0001"
#	MatchDevicePath "/dev/input/event*"
#	Driver "wacom"
#EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "stylus"
    Option "Device" "/dev/input/wacom"    # usb only?
    #Option "Device" "/dev/ttyS0"         # Serial only?
    Option "Type" "stylus"
    #Option "ForceDevice" "ISDV4"         # Tablet PC only
    Option "USB" "on"                     # usb only
    Option "PressCurve" "50,0,100,50"
    #Option "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "eraser"
    Option "Device" "/dev/input/wacom"    # usb only?
    Option "Type" "eraser"
    Option "USB" "on"                     # usb only
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "cursor"
    Option "Device" "/dev/input/wacom"    # usb only?
    Option "Type" "cursor"
    Option "USB" "on"                     # usb only
    #Option "Mode" "relative"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "pad"
    Option "Device" "/dev/input/wacom"    # usb only?
    Option "Type" "pad"
    Option "USB" "on"                     # usb only
    Option "ButtonsOnly" "on"
    Option "Button9"     "2"
    Option "Button10"    "3"
EndSection

#Section "ServerLayout"
#	Identifier  "Default Layout"
#	Screen      "Default Screen"
#	Option      "AIGLX"               "true"
#	InputDevice "Generic Keyboard"
#	InputDevice "Configured Mouse"
#	InputDevice "Wacom Tablet"        "SendCoreEvents"
#	InputDevice "Wacom Pen"           "SendCoreEvents"
#	InputDevice "Wacom Eraser"        "SendCoreEvents"
#	InputDevice "Wacom Mouse"         "SendCoreEvents"
#	InputDevice "Synaptics Touchpad"
#EndSection
```

---

### Post by Favux on 2011-04-26
Alright, we've found the problem.

While the xorg.conf.d and .conf files can be considered extensions of the xorg.conf the syntax is different.  Your problem is the usb snippet has been disabled and the xorg.conf like snippets/sections substituted for it will not work.  Luckily it hasn't broken X.

Since you only need the usb snippet you can just do this:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

#Section "InputClass"
#	Identifier "Wacom serial class"
#	MatchProduct "Serial Wacom Tablet"
#	Driver "wacom"
#	Option "ForceDevice" "ISDV4"
#EndSection
#
## N-Trig Duosense Electromagnetic Digitizer
#Section "InputClass"
#	Identifier "Wacom N-Trig class"
#	MatchProduct "HID 1b96:0001"
#	MatchDevicePath "/dev/input/event*"
#	Driver "wacom"
#EndSection
```
Removing all of the other xorg.conf like sections.  Use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
to edit the file.  So root has to do the editing.

Now to add the PressCurve Option what you do is add it to the usb snippet below the wacom driver line like so:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "PressCurve" "50,0,100,50"
EndSection
```
I know nothing about Wine but I'm reasonably sure I have seen folks describing pressure in PhotoShop on Wine in several threads.   So my guess is you are missing a setting to enable it.  Or else like in Gimp and Inkscape the application has something like extended input device settings you need to configure correctly.

I also think I've seen a similar deal with VirtualBox i.e. you have to change a setting to enable pressure.

---

