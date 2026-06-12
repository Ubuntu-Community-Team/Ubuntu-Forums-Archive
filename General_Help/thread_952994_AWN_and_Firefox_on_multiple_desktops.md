---
title: "AWN and Firefox on multiple desktops"
date: 2008-10-19
forum: General Help
---

### Post by sbussy89 on 2008-10-19
Using AWN... there's a firefox launcher, and when I click on it it doesn't add another firefox icon to the dock, it just takes the arrow away from underneath it and the launcher then represents the window until i close it.  because of this i can't use the launcher to open another window, i need to use file > new window.  the real problem with this is if im working on a desktop and want a firefox window, i need to flip back to a desktop that has a firefox window and click file > new window and then drag it to the new desktop, as clicking on the launcher just takes me back to the desktop with my original firefox window.  any other application adds a new icon to the end of the bar, this is the only app i have this problem with... any solutions?

---

### Post by sbussy89 on 2008-10-19
i was wrong about firefox being the only app it does this with... it seems to do it for everything but open office... is there some setting i can change so that no matter what it always adds a new icon for a new window?

---

### Post by mattman on 2008-10-19
If you have a middle mouse button or scroll wheel you can select the firefox icon with it and it will open a new window on the workspace you are currently using.

---

### Post by sbussy89 on 2008-10-19
thanks for the reply, but unfortunately i am using a touchpad with no middle button... is there somewhere i can change that to another button?  thank you

---

### Post by mattman on 2008-10-19
According to the wiki the only way to open multiple instances is by middle clicking. [http://wiki.awn-project.org/FAQ#How_can_I_launch_more_than_one_instance_of_an_application_that_I_have_a_launcher_for.3F]("http://wiki.awn-project.org/FAQ#How_can_I_launch_more_than_one_instance_of_an_application_that_I_have_a_launcher_for.3F")

---

### Post by loomsen on 2008-10-19
> **sbussy89 said:**
> thanks for the reply, but unfortunately i am using a touchpad with no middle button... is there somewhere i can change that to another button?  thank you

You may configure your touchpad whichever way you like.

Scrolling anywhere when using two fingers, specifying the delta when a scroll begins, how hard you gotta tap for it to be a klick, what else it should be, anything - all in the magic file on your PC.

/etc/X11/xorg.conf

Section Input, Synaptic and go :)
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"		"True"
	Option		"Device"				"/dev/psaux"
	Option		"Protocol"			"auto-dev"
	Option		"HorizTwoFigerScroll"	"True"
	Option		"VertTwoFingerScroll"	"True"
EndSection

```

Thats what mine looks like, tho I only added thw TwoFingerScroll Options, cause I'm using a mouse most of the time. But it could as well look like this:

```

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option  "LeftEdge"              "120"
    Option  "RightEdge"             "830"
    Option  "TopEdge"               "120"
    Option  "BottomEdge"            "650"
    Option  "FingerLow"             "14"
    Option  "FingerHigh"            "15"
    Option  "MaxTapTime"            "0"
    Option  "MaxTapMove"            "0"
    Option  "MaxDoubleTapTime"      "0"
    Option  "ClickTime"  "0"
    Option  "EmulateMidButtonTime"  "75"
    Option  "VertScrollDelta"       "10"
    Option  "HorizScrollDelta"      "0"
    Option  "MinSpeed"              "0.45"
    Option  "MaxSpeed"              "0.75"
    Option  "AccelFactor"           "0.020"
    Option  "EdgeMotionMinZ"    "30"
    Option  "EdgeMotionMaxZ"    "160"
    Option  "EdgeMotionMinSpeed"    "200"
    Option  "EdgeMotionMaxSpeed"    "200"
    Option  "EdgeMotionUseAlways"    "0"
    Option  "UpDownScrolling"       "1"
    Option "TouchpadOff" "0"
    Option "GuestMouseOff" "0"
    Option "LockedDrags" "0"
    Option "RTCornerButton" "2"
    Option "RBCornerButton" "3"
    Option "LTCornerButton" "0"
    Option "LBCornerButton" "0"
    Option "TapButton1" "0"
    Option "TapButton2" "0"
    Option "TapButton3" "0"
    Option  "CircularScrolling"     "0"
    Option  "CircScrollDelta"       "0.1"
    Option  "CircScrollTrigger"     "2"
    Option  "CircularPad"     "0"
    Option  "SHMConfig"  "true"
EndSection

```

Have fun :)

---

