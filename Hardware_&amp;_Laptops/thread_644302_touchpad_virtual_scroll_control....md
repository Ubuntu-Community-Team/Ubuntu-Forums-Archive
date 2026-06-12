---
title: "touchpad virtual scroll control..."
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by buccaneere on 2007-12-18
I found these parameters for touchpad settings:

   Option "LeftEdge" "1900"
   Option "RightEdge" "5400"
   Option "TopEdge" "1400"
   Option "BottomEdge" "4500"
   Option "FingerLow" "25"
   Option "FingerHigh" "30"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "220"
   Option "VertScrollDelta" "100"
   Option "MinSpeed" "0.02"
   Option "MaxSpeed" "0.18"
   Option "AccelFactor" "0.0010"

[COLOR="Red"]I want to reduce the size of the vertical scroll region on the right side of the touchpad. [/COLOR]

Do I just reduce the number for vertical scroll delta?
Any idea what the range is?
Does it start at 100? Finish at 100?

Thanks...

---

### Post by buccaneere on 2007-12-19
> **buccaneere said:**
> I found these parameters for touchpad settings:

   Option "LeftEdge" "1900"
   Option "RightEdge" "5400"
   Option "TopEdge" "1400"
   Option "BottomEdge" "4500"
   Option "FingerLow" "25"
   Option "FingerHigh" "30"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "220"
   Option "VertScrollDelta" "100"
   Option "MinSpeed" "0.02"
   Option "MaxSpeed" "0.18"
   Option "AccelFactor" "0.0010"

I want to reduce the size of the vertical scroll region on the right side of the touchpad. 

Do I just reduce the number for vertical scroll delta?
Any idea what the range is?
Does it start at 100? Finish at 100?

Thanks...

bumpinthisuntodatop

---

### Post by buccaneere on 2008-01-06
> **buccaneere said:**
> I found these parameters for touchpad settings:

   Option "LeftEdge" "1900"
   Option "RightEdge" "5400"
   Option "TopEdge" "1400"
   Option "BottomEdge" "4500"
   Option "FingerLow" "25"
   Option "FingerHigh" "30"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "220"
   Option "VertScrollDelta" "100"
   Option "MinSpeed" "0.02"
   Option "MaxSpeed" "0.18"
   Option "AccelFactor" "0.0010"

[COLOR="Red"]I want to reduce the size of the vertical scroll region on the right side of the touchpad. [/COLOR]

Do I just reduce the number for vertical scroll delta?
Any idea what the range is?
Does it start at 100? Finish at 100?

Thanks...

bumpin' again here.......

---

### Post by JCrowly on 2008-01-08
hey I was having the same problem. I saw your post and that gave me somewhere to start anyways. I got mine working properly now. Here's what I did.

Open a terminal and type:
```
sudo gedit /etc/X11/xorg.conf
```

You're looking for an input device with an identifier relating to a touchpad. Mine was "Synaptics Touchpad".

Add or Change the entry listed as **Option "RightEdge" "<####>"**
The higher your **<####>** is, the more narrow your verticle scroll edge will be.
For me, anything from **5900** to **5950** was satisfactory.

Save the changes you made to xorg.conf, log out and log back in. Your scrolling area should be more realistic now. Play around with the RightEdge number if it still needs adjusting.

Enjoy.

---

### Post by JCrowly on 2008-01-08
I mean to put either:

Option "RightEdge" "5900"

*- or -*

Option "RightEdge" "5950"

If you go much higher than that, you'll lose your verticle scrolling altogether. If you go much lower, more of your touchpad will be used for scrolling, less for controlling your mouse. The "LeftEdge" will remain at default, unless you state otherwise. If the LeftEdge and RightEdge were very close together though, I would imagine that the touchpad would be more sensitive.

---

### Post by buccaneere on 2008-01-09
> **JCrowly said:**
> I mean to put either:

Option "RightEdge" "5900"

*- or -*

Option "RightEdge" "5950"

If you go much higher than that, you'll lose your verticle scrolling altogether. If you go much lower, more of your touchpad will be used for scrolling, less for controlling your mouse. The "LeftEdge" will remain at default, unless you state otherwise. If the LeftEdge and RightEdge were very close together though, I would imagine that the touchpad would be more sensitive.

Hi crowly...

That's exactly where I needed to get to - I did it once for disable tap function.

Here's what I got now on 3 different machines:
the one I want to change...
[HTML]Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
EndSection[/HTML]

This is a second laptop:
[HTML]
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "MaxTapTime"            "0"
EndSection[/HTML]

---

### Post by Yellowdog428 on 2008-01-09
looks like we are in the same boat.

I to need to change the scroll on the right of my touchpad.  its about 1/2 inch larger than I would like on my laptop.  My xorg.conf file looks like yours and cant seem to find anything about where the change should take place.....

Thanks in advance to anyone that can help!
Cheers

---

### Post by buccaneere on 2008-01-09
> **Yellowdog428 said:**
> looks like we are in the same boat.

I to need to change the scroll on the right of my touchpad.  its about 1/2 inch larger than I would like on my laptop.  My xorg.conf file looks like yours and cant seem to find anything about where the change should take place.....

Thanks in advance to anyone that can help!
Cheers

Hi Yell...

I just got into the files that crowly referred me to, which is where I was able to dis-able tapping some time back.

But the 'values' section of the file, where I found the values I posted in my first post, are not in that file.

???:confused:

---

### Post by Yellowdog428 on 2008-01-09
Yep heres mine

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option 		"SHMConfig" 		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by buccaneere on 2008-01-09
I can't find those values in my box anywhere - I think I was havin' figmentatious hallucinations...

So I found this on 2 sites :
[HTML]Section "InputDevice"
	Identifier	"Synaptics"
	Driver	"synaptics"
	Option	"Protocol" "event"
	Option	"Device" "/dev/input/event1"
	Option	"LeftEdge" "1900"
	Option	"RightEdge" "5400"
	Option	"TopEdge" "1900"
	Option	"BottomEdge" "4000"
	Option	"FingerLow" "25"
	Option	"FingerHigh" "30"
	Option	"MaxTapTime" "180"
	Option	"MaxTapMove" "220"
	Option	"VertScrollDelta" "100"
	Option	"MinSpeed" "0.02"
	Option	"MaxSpeed" "0.10"
	Option	"AccelFactor" "0.0010"
	Option	"SHMConfig" "on"
EndSection[/HTML]

I'm gonna' cut n paste, so if you don't hear from me for a couple of days, watch for bright light, wind, and smoke. Then run...

---

### Post by buccaneere on 2008-01-09
Don't Do It!!!

Big mistake!!!
I got booted up with a live CD. You know how to re-create the file from a Live CD boot?

---

### Post by Yellowdog428 on 2008-01-10
> **buccaneere said:**
> Don't Do It!!!

Big mistake!!!
I got booted up with a live CD. You know how to re-create the file from a Live CD boot?

Sorry man hope you got it working.

If not you can edit the same file from your Live CD.

```
sudo gedit /LOCATION ON THE DRIVE WHERE YOUR xorg.conf file is
```

Then edit to

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "SHMConfig"             "on"
        Option          "MaxTapTime"            "0"
EndSection
```

and save the file.

Let me know how it goes.
Cheers

---

### Post by KingArthur10 on 2008-01-21
How do people find out their max right edge?  My laptop is registering a double-wide scroll area under linux and I'd like to lessen it.  I guess I could just dink around with numbers for a while, but if there is a way to find out what your edges are, that would be greatly appreciated.

---

### Post by KingArthur10 on 2008-01-24
I found a good edge for my Gateway C-140xl.  "5820" works great!

---

