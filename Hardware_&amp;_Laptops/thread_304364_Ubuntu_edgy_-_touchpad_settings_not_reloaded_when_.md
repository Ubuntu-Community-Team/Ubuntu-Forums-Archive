---
title: "Ubuntu edgy - touchpad settings not reloaded when resuming from suspend/hibernate"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by dawn on 2006-11-21
HI everyone,

I own a Toshiba A110 laptop and i have a small, annoying issue: my touchpad settings are not loaded after resuming from suspend/hibernate.
The touchpad simply acts like a plain touchpad, no scrolling, no zones, etc.
If i'm restarting the X server, then some settings are loaded, but not those from xorg.conf. I get horizontal scrolling, which is disabled in my config.
If i'm running qsynaptics, then after closing it all my settings are loaded and the touchpad is working the way i like.

Any ideas?
Thx for help.

Btw, my touchpad is an ALPS;
My /etc/X11/xorg.conf looks like:
...
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option 		"LeftEdge" 		"130"
	Option 		"RightEdge" 		"840"
	Option "TopEdge" 		"130"
	Option "BottomEdge" 		"640"
	Option "FingerLow" 		"7"
	Option "FingerHigh" 		"8"
	Option "MaxTapMove" 		"110"
	Option "EmulateMidButtonTime" 	"75"
	Option "VertScrollDelta" 	"20"
	Option "MinSpeed" 		"0.25"
	Option "MaxSpeed" 		"0.50"
	Option "AccelFactor" 		"0.030"
	Option "EdgeMotionMinSpeed" 	"200"
	Option "EdgeMotionMaxSpeed" 	"200"
	Option "UpDownScrolling" 	"1"
	Option "CircularScrolling" 	"1"
	Option "CircScrollDelta" 	"0.1"
	Option "CircScrollTrigger" 	"2"
	Option "SHMConfig" 		"on"
Option "CircularPad"		"0"
Option "ClickTime" 		"100"
Option "CoastingSpeed"		"0"
Option "EdgeMotionMaxZ"		"160"
Option "EdgeMotionMinZ"		"30"
Option "EdgeMotionUseAlways"	"0"
Option "FastTaps"		"0"
Option "GuestMouseOff"		"0"
Option "HScrollEmuOff"		"1"
Option "HorizEdgeScroll"	"1"
Option "HorizScrollDelta"	"10"
Option "HorizTwoFingerScroll"	"0"
Option "LBCornerButton"		"0"
Option "LTCornerButton"		"0"
Option "LeftRightRepeat"	"1"
Option "LeftRightScrolling"	"1"
Option "LockedDrags"		"0"
Option "MaxDoubleTapTime"	"180"
Option "MaxTapTime"		"271"
Option "PalmDetect"		"1"
Option "PalmMinWidth"		"10"
Option "PalmMinZ"		"200"
Option "PressureMotionMaxFactor" "1"
Option "PressureMotionMaxZ"	"160"
Option "PressureMotionMinFactor" "1"
Option "PressureMotionMinZ"	"30"
Option "RBCornerButton"		"3"
Option "RTCornerButton"		"2"
Option "ScrollButtonRepeat"	"100"
Option "ScrollingMode"		"1"
Option "SingleTapTimeout"	"180"
Option "SynDaemonOff"		"0"
Option "SynDaemonTiming"	"0"
Option "TapButton1"		"1"
Option "TapButton2"		"2"
Option "TapButton3"		"3"
Option "TappingOff"		"0"
Option "TouchpadOff"		"0"
Option "UpDownRepeat"		"1"
Option "VScrollEmuOff"		"0"
Option "VertEdgeScroll"		"1"
Option "VertScrollDelta"	"20"
Option "VertTwoFingerScroll"	"0"
Option "VertTwoFingerScroll"	"0"

EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad" "AlwaysCore"
EndSection

---

### Post by atonaldenim on 2007-01-06
hey dawn-
I have the same problem on my Sony laptop - I lose touchpad scrolling after suspend/resume. I did a little searching and found an [explanation of the problem]("https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/59867") and a potential solution:> 
After suspend/hibernate the device file that points to the touchpad (event*) changes its name (event1 -> event3 or something like it).

I had to add rules to "udev" that makes it create a link called /dev/input/touchpad that points to the "right" device file.

[Pedro Martínez Juliá]("https://launchpad.net/~pedromj")  at 2006-10-23 14:46:39 UTC


I'm not too familiar with writing udev rules, but maybe someone else here can give us some advice...

---

### Post by eitan_a on 2007-01-06
Confirmed on a Sony Vaio laptop, Ubu 6.10.

Bug was not present in 6.06.

---

### Post by leadweight on 2007-03-22
I have this problem as well on a Sony SZ and not a clue as to how to write a udev link.  My solution for now is ctrl-alt-f1 followed by ctrl-allt-f7.

---

### Post by bastubis on 2007-04-18
I have the same problem with edgy and alps touchpad on Dell Inspiron 500M -- it only happened recently though, was fine up until a week ago -- possibly caused by an upgrade. I've been restarting X which fixes it -- reluctant to start rewriting udev without understanding what the (sudden) problem is?

---

### Post by leadweight on 2007-04-19
It still a problem for me with the release of Feisty.  There are a lot more entries on the launchpad bug report.  All I can see is they rate it as a low priority bug.  Perhaps the person responsible for fixing it has a laptop that is not plagued with this problem, and can't diagnose it.  Its a bit much to enter your password, keyring password and then restart X every time you put a notebook to sleep and go to wake it up.

It may not be for you, but for me this is a show stopper.  It is also not a good way to start, because if something basic like this does not work, what about the rest of the system?

---

### Post by bastubis on 2007-04-22
Just upgraded to Feisty (clean install) -- resume from suspend is now so hopeless I've had to turn it off. Restarting X doesn't work, the touchpad comes back (sorta) but the whole desktop is flaky until I reboot. If I hibernate instead, the screen remains off and I still have to reboot. 

Other than that, Feisty seems really great -- so far anyway. I'm pleased enough with it to just cope with not being able to suspend (though it *is* pretty annoying).

---

### Post by bepcyc on 2007-04-22
Hi, everybody

I had the same problem after installing Feisty Fawn on my laptop (Sony VAIO SZ)
And I've found an easy workaround for this bug [here]("https://bugs.launchpad.net/ubuntu/+source/xorg-driver-synaptics/+bug/18605/comments/8").

You need to uncomment the line

**DOUBLE_CONSOLE_SWITCH=true**

in file /etc/default/acpi-support

after doing that my touchpad does work perfect with suspend/hibernate ;)))

Hope it helps to you

---

