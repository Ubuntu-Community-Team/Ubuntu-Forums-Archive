---
title: "Do these multitouch instructions work for you?"
date: 2009-03-27
forum: Hardware
---

### Post by hotweiss on 2009-03-27
[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)

I tried following these instructions to get the two finger scrolling on my Asus notebook, but they did not work as expected. All I was able to get is the autoscroll icon when tapping the touchpad with two fingers.

PS-can a mod change Does to Do?

---

### Post by unoodles on 2009-03-27
Nope, doesn't work.
As far as I know, this guy is wrong. There **is** hardware required for multitouch capabilities.

---

### Post by smartboyathome on 2009-03-27
I was able to get it working on my HP laptop, but not the way he posted. You have to disable hotplugging in your Xorg.conf, then use some of the older instructions [such as this]("http://lucumr.pocoo.org/2007/11/13/two-finger-scrolling-on-ubuntu").

---

### Post by Polygon on 2009-03-27
> **unoodles said:**
> Nope, doesn't work.
As far as I know, this guy is wrong. There **is** hardware required for multitouch capabilities.

no there isnt.

my touchpad on my laptop, the native windows drivers dont give me multi touch support, but with linux i can do two touch scrolling out of the box.

---

### Post by hotweiss on 2009-03-27
> **smartboyathome said:**
> I was able to get it working on my HP laptop, but not the way he posted. You have to disable hotplugging in your Xorg.conf, then use some of the older instructions [such as this]("http://lucumr.pocoo.org/2007/11/13/two-finger-scrolling-on-ubuntu").

Thanks. I will try them.

---

### Post by spupy on 2009-03-27
> **Polygon said:**
> no there isnt.

my touchpad on my laptop, the native windows drivers dont give me multi touch support, but with linux i can do two touch scrolling out of the box.

I'm almost certain that there is a hardware requirement. You can enable the option as this guy did, but if your touchpad isn't able to detect more than 2 fingers (like mine), nothing will happen. This is just a case of But-It-Works-For-Me.
In fact, I was able to activate two-finger-scroll on my touchpad. But I did it with a dirty mod of the synaptics driver, and it has nothing to do will how many finger are detected, but rather with the fact that one and two fingers give different pressure. Measuring the pressure is a safe way to tell if there is more than 1 finger on the touchpad.

There is a safe and certain way to know if your touchpad has the ability to detect multiple fingers. For this purpose you need the program **synclient**. (I'm not sure where I have it from. Google it.)
Start it like this:
```
synclient -m 50
```
The output looks like this:
```
~ $ synclient -m 100
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000   828  212   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   0.700   428  272  57 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   0.801   458  242  59 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   0.901   488  229  59 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.001   496  222  59 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.101   500  219  61 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   1.201   501  219   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.001   480  199 117 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.101   480  203 119 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.201   480  205 118 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.301   480  207 120 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.402   478  219 122 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.502   478  222 120 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.602   477  240 118 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.702   476  266 123 1  0  0 0 0 0 0  00000000   0  0  0   0   0
   2.802   476  266   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0
```

The **f** column is the number of fingers currently on the touchpad. If you see the number 2 when you try to scroll with 2 finger - congratulations, you can enable multi-touch (or, ahem, double-touch). Otherwise, you are out of luck.

Also, ALPS touchpads, which are not Synaptics touchpads, also use the synaptics driver. ALPS touchpads generally don't support multitouch, while Synaptics touchpads mostly do. (Words taken from the manual of synclient).

---

### Post by damis648 on 2009-03-27
> **spupy said:**
> Also, ALPS touchpads, which are not Synaptics touchpads, also use the synaptics driver. ALPS touchpads generally don't support multitouch, while Synaptics touchpads mostly do. (Words taken from the manual of synclient).

Completely true. My trackpad (an ALPS) only ever shows 1 finger as touching. I have to emulate two finger by setting it to activate two finger when the Z-axis pressure is at 100 (when two fingers are placed, that pressure jumps dramatically). On the contrary, a friend's Synaptics trackpad work OOTB shows the F value for how many points are touching.:popcorn:

PS. If anyone with ALPS wants to know how to do emulation of two fingers, let me know. I forgot where I learned how, but I can write up some quick directions.

---

### Post by spupy on 2009-03-28
> **damis648 said:**
> Completely true. My trackpad (an ALPS) only ever shows 1 finger as touching. I have to emulate two finger by setting it to activate two finger when the Z-axis pressure is at 100 (when two fingers are placed, that pressure jumps dramatically). On the contrary, a friend's Synaptics trackpad work OOTB shows the F value for how many points are touching.:popcorn:

PS. If anyone with ALPS wants to know how to do emulation of two fingers, let me know. I forgot where I learned how, but I can write up some quick directions.

That is exactly how I made my ALPS touchpad recognize two-finger scroll. :) Did you do some kind of configuration? I added extra code in the driver to check for that pressure threshold.

---

### Post by damis648 on 2009-03-28
Originally, I put something in /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi, but I just noticed that for some reason since I upgraded to jaunty beta last night, now that file is mostly empty. :confused: Maybe it was moved, or something else, or Jaunty has out-of-the-box support for two-finger scrolling, :popcorn:, I don't know. But I suspect that Jaunty has out-of-the-box support, because since I upgraded, my scrolling has been significantly faster. (I used to be able to scroll on my desktop by using my trackpad and moving my fingers about half a centimeter, and it would switch workspaces to the next. Now, it does a full circle of all the workspaces back to the one I'm at with that distance, so it's significantly faster.) If jaunty has OOTB support, I'm sold. :popcorn:

---

### Post by deFlNE on 2009-05-14
> **spupy said:**
> That is exactly how I made my ALPS touchpad recognize two-finger scroll. :) Did you do some kind of configuration? I added extra code in the driver to check for that pressure threshold.


Guys, could you remember how exactly you did it? I need to bind middle button on two thinger tap and my synaptics touchpad in some reason don't differ one and two finger taps.

---

### Post by baucha_linux on 2009-06-27
I got ALPS as well. Can any of u tell me how u enabled two finger scrolling in ALPS. I have been trying the way they described for synaptics it didnt work. I'm using Kubuntu Jaunty n it doesnt seem to hav OOTB support for two fingers scrolling for ALPS.

---

### Post by capleton on 2010-03-11
Hey, I just wanted to say that I created a short tutorial on how to get multi-touch working.  It took me awhile before I could finally get it working, so I thought I would post in case anyone else finds themselves in my predicament.  [You can find it here.]("http://ubuntuforums.org/showthread.php?t=1426782#3")

---

### Post by fachex on 2010-04-19
I've got it to work in my Gateway tablet pc, I can see it recognizing even three fingers. Now what? How do I get the gesture to work on firefox, chrome, picture manager and other apps that make take advantage of the multi-touch technology?
I tried to modified my xorg.conf but when I restart I get all my screen messed up.
Here is my xorg.conf 
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Finepoint Tablet"
	Driver		"fpit"
	Option		"Device"		"/dev/ttyS0"
	# "BaudRate" may need tweaking (9600, 19200, or 38400).
#	Option		"BaudRate"		"19200"
	# For a passive pen, e.g. Stylistic 3400 use "true".
	Option		"Passive"		"false"
	# To make the touchscreen respond automatically to
	# resolution changes and screen rotation:
	Option		"TrackRandR"
	# Not sure if "SendCoreEvents" line is necessary.
	Option		"SendCoreEvents"	"true"
	Option		"Buttons"		"2"
	# not sure which button line works or both together?
	Option		"Button2"		"3"
	# These may need tweaking.
	Option		"MaximumXPosition"	"12550"
	Option		"MaximumYPosition"	"7650"
	Option		"MinimumXPosition"	"400"
	Option		"MinimumYPosition"	"400"
	Option		"InvertY"
	# This is for the touchpad	
	#Identifier “Synaptics Touchpad”
	#Option “HorizEdgeScroll” “on”
	#Option “VertEdgeScroll” “on”
	#Option “VertTwoFingerScroll” “on
	#Option “HorizTwoFingerScroll” “on”
	#Option “CornerCoasting” “on”
	#Option “PalmDetect” “on”
	#Option “CircularScrolling” “on”
	#Option “CircScrollTrigger” “3&#8243;
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
	Inputdevice	"Finepoint Tablet"
#	InputDevice     "Synaptics" "SendCoreEvents"
	
EndSection

#
# Developed and tested with jrozo17 on a Gateway CX2724.
#

---

