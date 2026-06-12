---
title: "Help with touchpad scroll sensitivity"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by agiamba on 2007-02-10
Hi, I'm fairly new to Ubuntu, I've been with it for about 2-3weeks or so and thus far I really like it, I like the combination of the gui and the commandline.

I have a laptop with an ALPS touchpad. I use a USB mouse most of the time, and it's peachy, just fine. But my touchpad's sensitivity is way too low and I was wondering how to change it, but not my USB-mouse sensitivity?

---

### Post by teaker1s on 2007-02-10
desktop system tab 
either in administration or preferences you can alter settings under mouse
reason I can't say more is I'm on feisty and the layout has changed

---

### Post by kpolice on 2007-02-11
First backup your /etc/X11/xorg.conf file and then find the InputDevice section for your Touchpad. I also have an ALPS touchpad and I have the following values in my xorg.conf file:

```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mouse1"
	Option	    "Protocol" "auto"
        Option      "SHMConfig" "on"

 	Option	"LeftEdge" "130"
 	Option	"RightEdge" "840"
 	Option	"TopEdge" "130"
 	Option	"BottomEdge" "640"
 	Option	"FingerLow" "7"
 	Option	"FingerHigh" "8"
 	Option	"MaxTapTime" "180"
 	Option	"MinTapTime" "110"
 	Option	"ClickTime" "0"
 	Option	"EmulateMidButtonTime" "75"
 	Option	"VertScrollDelta" "30"
 	Option	"HorizScrollDelta" "0"
 	Option	"MinSpeed" "0.45"
 	Option	"MaxSpeed" "0.75"
 	Option	"AccelFactor" "0.030"
 	Option	"EdgeMotionMinSpeed" "200"
 	Option	"EdgeMotionMaxSpeed" "200"
 	Option	"UpDownScrolling" "1"
 	Option	"CircularScrolling" "1"
 	Option	"CircScrollDelta" "0.1"
 	Option	"CircScrollTrigger" "3"
 	Option	"Emulate3Buttons" "on"
 	Option	"VertEdgeScroll" "on"
EndSection
```

---

