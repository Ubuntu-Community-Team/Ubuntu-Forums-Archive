---
title: "[SOLVED] Alps touchpad in Ubuntu 7.04"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2007-06-18
Feels like I will have a post with this issue on every Ubuntu version.

How do I turn off my ALPS touchpad in Ubuntu 7.04?

Is ALPS forgotten by the linux community?

---

### Post by ppd on 2007-06-18
Just put SHMConfig "true" in your xorg.conf and you'll be able to switch on/off the pad dynamically

---

### Post by Jaxilian on 2007-06-19
> **ppd said:**
> Just put SHMConfig "true" in your xorg.conf and you'll be able to switch on/off the pad dynamically

Where in the file shall I put it?

---

### Post by tact on 2007-06-19
in your /etc/X11/xorg.conf you will find a section for touchpad (dont worry it says synaptic, mine does and i have an ALPS touchpad too).

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

FIRST - back up your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.my.bak
```

Then edit using:
```
sudo gedit /etc/X11/xorg.conf
```

and make it look like this:
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option    	"MinSpeed"        	"0.8"
	Option    	"MaxSpeed"        	"0.8"
	Option		"SHMConfig"		"on"
EndSection

If you didnt have the min and max speed lines - you you can adjust the acceleration of your touchpad pointer also.

With the SHMconfig line in your xorg.conf you can now use the programs synclient and/or syndaemon to control your touchpad.

A clever thing to do is not to totally turn off your touchpad but to have syndaemon just disable it while typing and re-enabling it say 1 or 2 seconds after keyboard has been idle.  This is REALLY effective in stopping those annoying "moments" when you inadvertently brush the touchpad when typing and wipe out chunks of text accidently.

A good tutorial is here:
[http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing](http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing)

It talks about putting syndaemon in a script to enable it automatically all the time.  ubuntu users can simply create an entry in "sessions" with the appropriate parameters.

CLick   System>Preferences>Sessions and under the startup tab create a new startup program entry for syndaemon.

---

### Post by Jaxilian on 2007-06-19
Thanks man.

It works very good :popcorn:

---

### Post by Jaxilian on 2007-06-19
Just curious, What is the opposite command to the following one that disables the touchpad?
```

$synclient  TouchpadOff=1

```

---

### Post by Jaxilian on 2007-06-19
ah crap.....the command: 
```

syndeamon -t 1.0 -d

```

didn't work at all. I tried without the 1.0 too....same result. 

any ideas?

---

### Post by tact on 2007-06-20
Errrm I think syndaemon -t does not take a parameter.  

try 
syndaemon -t  -d

or
syndaemon -i 2 -d


and for synclient ..
TouchpadOff (Integer)
    Switch off the touchpad. Valid values are:
    0 	Touchpad is enabled
    1 	Touchpad is switched off
    2 	Only tapping and scrolling is switched off

---

### Post by Jaxilian on 2007-06-21
3 words....does not work


tried it all. 

synclient TouchpadOff=2 

does not turn off tapping.

syndaemon -t -d 

does not work either

---

### Post by tact on 2007-06-21
What is the output of 
```
synclient -l
```

---

### Post by Jaxilian on 2007-06-22
> **tact said:**
> What is the output of 
```
synclient -l
```

```

~$ synclient -l
Parameter settings:
    LeftEdge             = 102
    RightEdge            = 921
    TopEdge              = 76
    BottomEdge           = 691
    FingerLow            = 25
    FingerHigh           = 30
    MaxTapTime           = 180
    MaxTapMove           = 220
    MaxDoubleTapTime     = 180
    SingleTapTimeout     = 180
    ClickTime            = 100
    FastTaps             = 0
    EmulateMidButtonTime = 75
    VertScrollDelta      = 15
    HorizScrollDelta     = 0
    VertEdgeScroll       = 1
    HorizEdgeScroll      = 1
    VertTwoFingerScroll  = 0
    HorizTwoFingerScroll = 0
    MinSpeed             = 0.325945
    MaxSpeed             = 0.782269
    AccelFactor          = 0.0065189
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 76
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    LeftRightScrolling   = 1
    UpDownRepeat         = 1
    LeftRightRepeat      = 1
    ScrollButtonRepeat   = 100
    TouchpadOff          = 2
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0
    CircularPad          = 0
    PalmDetect           = 1
    PalmMinWidth         = 10
    PalmMinZ             = 200
    CoastingSpeed        = 0
    PressureMotionMinZ   = 30
    PressureMotionMaxZ   = 160
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1

```

I can't get the tapping off. It's the most annooying feature on a laptop. synclient parameters doesn't do anything when I type them.

---

### Post by kerry_s on 2007-06-22
sudo gedit /etc/X11/xorg.conf

Option		"TouchpadOff"		"1"


my settings
i use> syndaemon -d <in session startup it disables the touchpad when i'm typing.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"TouchpadOff"		"0"
# 0 Touchpad is enabled 
# 1 Touchpad is switched off 
# 2 Only tapping and scrolling is switched off

	Option		"AccelFactor"		"0.050"
	Option		"MaxTapTime"		"160"
	Option		"MaxTapMove"		"400"
	Option		"SHMConfig"		"on"
	Option		"RBCornerButton"	"2"
	Option		"LockedDrags"		"true"
EndSection

```

---

