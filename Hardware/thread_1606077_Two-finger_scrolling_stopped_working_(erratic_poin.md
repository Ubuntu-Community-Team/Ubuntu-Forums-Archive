---
title: "Two-finger scrolling stopped working (erratic pointer instead)"
date: 2010-10-26
forum: Hardware
---

### Post by Valentini on 2010-10-26
Hi,

I've got a Acer TravelMate 8471 running Ubuntu 10.10 x64 (upgraded from 10.04, but this is a week ago, and should not have anything to do with my problem).
Under mouse-preferences > Touchpad, the two-finger scroll option is grayed out, but by setting the value manually in gconf, it have been working just fine until today (I've tried to figure out what made it screw up, but I can't find anything that would have any influence).
When I try to enable two-finger scrolling, the driver never figures out that I've got two fingers on the pad, and instead my mouse flies around on the screen.

I've tried configuring the driver through xinput with a script I've used before:
```

	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 10
	
	# 	Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 7        
	
	# 	vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
	xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 1   
	
	# 	vertical, horizontal, corner - values: 0=disable  1=enable
	xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 0 0 0       
	
	# 	stabilize 2 finger actions - value=pad-pixels
	xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 120 
```
But even this fails.

When I tried using synclient with these four commands:
```
synclient HorizTwoFingerScroll=1
synclient VertTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48

```
it begins scrolling, but it scrolls rapidly up and down while and for some time after I've tried to use two fingers.

Any help is appreciated.

---

### Post by Valentini on 2010-10-26
My problem have now seemingly fixed itself, however weird that sounds.

I took a look at the props in synclient, and as far as I can remember they were the same.

Come to think of it, I have tried this once before.
I dual-boot Win7 and Ubuntu, and the problem seems to arise sometimes when I restart from Win7. This time I booted into Win7 and then turned off the laptop, and booted into Ubuntu. I'm not sure if it matters that I restart instead of switching off/on my laptop.

---

### Post by nostalgic_sun on 2010-11-26
I have  a Dell Inspiron N4010, I also faced the same problem with two finger scrolling, while rebooting from windows 7 to Ubuntu. I again rebooted to windows7 and shut down the laptop. I booted into ubuntu again and guess what....two fingers scrolling started working again!!!!!!  
Is it a bug?

---

