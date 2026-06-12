---
title: "Wacom Grapphire 4 - Dual monitor trouble."
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by galvheim on 2007-12-14
Hi to all of you,

I just installed my Wacom Grapphire 4 CTE-640 to my Gutsy Gibbon system without any problems. It seems very responsive and works nicely with gimp.

My only problem is that I work in a dual-monitor setup. That means that my tablet is stretched over two monitors making the aspect ratio feel unnatural. In other words its moving a lot faster in the x direction than in the y direction.

In windows it was possible to restrict the tablet to only working on one monitor when, but I have still not figured out how to do it in Ubuntu using some extra "Options" commands in the xconf file. 

I could not find anyone having brought up this issue before me, but still I think it's a very valid question to be answered. This has all to do with the now built-in feel in my hand for the pen-tool.

I strongly hope someone clever out there will give me a solution.

Thanx in advance!

- Gunnar.

---

### Post by sloggerkhan on 2007-12-14
You need to look up options for the pen tool to put in xorg config.
Offhand, if I recall correctly, you can contrain it to 1 monitor such that you can get into the next desktop by running over the edge, however, I believe the driver will then only support pressure sensitivity on the left hand screen.
You can also use an option to constrain aspect ration so that a bit off the bottom and top will be dead, but the active area will be the same shape as both your monitors combined.
It's been a while since I set mine up, but I think you can find thie info via google search or forum search.

---

### Post by galvheim on 2007-12-14
Thanks! Just knowing that it was possible made me continue my research.
I will advice anyone with a wacom tablet to look at this very helpful guide into the mysteries of xorg.conf.

[http://linuxwacom.sourceforge.net/index.php/howto/inputdev]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev")

So now my setup looks like this:

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Stylus2" "3" # set button to right click
Option "Type" "stylus"
Option "USB" "on"
Option "PressCurve" "50,0,100,50" # Custom preference
Option "Twinview" "horizontal"
Option "ScreenNo" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "USB" "on"
Option "Twinview" "horizontal"
Option "ScreenNo" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "USB" "on"
Option "Twinview" "horizontal"
Option "ScreenNo" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "pad"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on"
Option "Twinview" "horizontal"
Option "ScreenNo" "0"
EndSection

Beautiful...:)

---

### Post by sloggerkhan on 2007-12-14
Hmm.... I'm not sure I have the "pad" section in mine... maybe I'll adjust mine a bit more.

---

### Post by galvheim on 2008-01-02
Developments: 

Well, I can give some more info on this. further testing has shown me that it didn't work at all. 

This is a problem that has mainly arised because I use a dual monitor setup. So when using the Options for the driver in xorg.conf like Twinwiew and ScreenNo i get into some quite exotic problems when using my tablet in the Gimp. See below:

> Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Stylus2" "3" # set button to right click
Option "Type" "stylus"
Option "USB" "on"
Option "PressCurve" "50,0,100,50" # Custom preference
# Option "Twinview" "horizontal"
# Option "ScreenNo" "1"
Option "Mode" "Absolute"
EndSection

In this it's excluded by the '#', because it simply doens't work. 
Problems can be seen as the brush misaligning with the cursor when moving onto the workarea of a picture.This happens both when using the settings above without the #'s 
and when using only the Twinview-setting. Misalignment can be huge or small depending  where I am on the monitor. Usuall monitor 0 has the least. Looks like my tablet and gimp are working in two very diffrent resolutions. This only happens with the stylus on the picture I work on, as my curser is positioned in the correct place. The cursor will also be fine if I turn off the pressure sensitivity in the GIMP settings. Like: Stylus - Turn Off instead of Stylus - Screen | Window. But then it will only work the same way as a mouse. 

I have also tried Twinview without specifying ScreenNo, then it let me chose screen automatically by letting the cursor jump over to the other screen when pushed to the edge of the screen. This also doesn't work, and the more I move from screen 0 the more offset it will become. 
Also when the brush is in close contact with the cursor in GIMP, the cursor will move much faster than the actual brush I use. So it's like a reversed servo or something. The same as I mention above about the brush in GIMP and Tablet using diffrent resolutions. 

Only solution I can find so far is to disable the Twinview and ScreenNo completely and just work with my tablet on both monitors at the same time. In this situation I trust that my brain will automatically adjust itself to the weird aspect that follows this. 
I mean now my work area is stretched in the horisontal direction wheras it's the same in the vertical direction - being much faster in one direction than the other. And since my brain have not yet adjusted to this behaviour I draw elipses instead of circles at the moment.

No good. 

I would not sacrifice my dual monitor setup for such a redicilous bug. 
Too bad I don't know which one is the problem: GIMP or the Driver?

Any help would be greatly appreciated. 
If it's not too much trouble get me a print of your xorg.conf

This could well be the things that makes Linux seem awkward to new people, and having to sacrifice such functionality just becasue I can't stand windows is so sad and unnecessary. 

Boo-hooo!!

---

### Post by sloggerkhan on 2008-01-04
On my dual monitor, I recall finding 2 solutions:
There is an option to make it so that you can mouse off the edge of a 1st to a 2nd monitor, in which case pressure sensitivity only works on the 1st, and an option to make the usable tablet area match in shape the aspect ratio of the multimonitor setup, which leaves large segments of the pad unusable, but will have pressure sensitivity on both screens. Also, it's key to match settings between the different wacom input devices. 

My relevant xorg.conf section (I tinkered with it some and remnants are still there.):
```

Section "InputDevice"

	#Option     "Twinview" "horizontal"
	#Option     "ScreenNo" "1"
	#Option     "mmonitor" "on"
	Option "USB" "on"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	#Option        "TopX"         "1680"
    	#Option        "TopY"         "0"
    	#Option        "BottomX"      "3360"
    	#Option        "BottomY"      "1050"
	#Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
	#Option "KeepShape" "on"
EndSection

Section "InputDevice"

        #Option      "Twinview" "horizontal"
	#Option     "ScreenNo" "1"
	#Option     "mmonitor" "on"
	Option "USB" "on"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	#Option        "TopX"         "1680"
    	#Option        "TopY"         "0"
    	#Option        "BottomX"      "3360"
    	#Option        "BottomY"      "1050"
	#Option	    "ForceDevice" "ISDV4"		# Tablet PC
	#Option "KeepShape" "on"
EndSection

Section "InputDevice"

	#Option     "Twinview" "horizontal"
        #Option     "ScreenNo" "1"
	#Option     "mmonitor" "on"
	Option "USB" "on"	
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	#Option        "TopX"         "1680"
    	#Option        "TopY"         "0"
    	#Option        "BottomX"      "3360"
    	#Option        "BottomY"      "1050"
	#Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
	#Option "KeepShape" "on"
EndSection

```

---

