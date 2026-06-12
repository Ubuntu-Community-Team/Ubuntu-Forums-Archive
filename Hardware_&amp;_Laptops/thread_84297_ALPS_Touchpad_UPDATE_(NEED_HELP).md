---
title: "ALPS Touchpad UPDATE (NEED HELP)"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by jjoyner on 2005-10-30
Ok this is what happened...I read the post about an ALPS pad finally working and decided to modify my xorg.conf to these options:

> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event3"
	Option		"Protocol"		"event"
	Option		"VertScrollDelta"       "10"
	Option		"HorizScrollDelta"	"0"
 	Option 		"MinSpeed" 		"0.45"
	Option 		"MaxSpeed" 		"0.75"
	Option 		"UpDownScrolling" 	"1"
	Option 		"LeftEdge" 		"120"
	Option 		"RightEdge" 		"830"
	Option 		"TopEdge" 		"120"
	Option 		"BottomEdge" 		"650"
 	Option 		"EdgeMotionMinSpeed" 	"200"
	Option 		"EdgeMotionMaxSpeed" 	"200"
EndSection

And after doing "init 1" in terminal, I restarted X and my scrolling and tapping were working properly.  HOWEVER, I rebooted and it stopped working.  I have repeated steps several times and I cannot get it to work again.  I have cat /proc/bus/input/devices only to find the Synaptics Glide is gone.  I am also back to tap and high sensitivity with my mouse again.  Someone please help!  I lost my mouse!!!!

---

### Post by jjoyner on 2005-10-30
UPDATE -
> 
sudo sh -c "echo options psmouse proto=any > /etc/modprobe.d/psmouse.modprobe" + reboot made the touchpad work again...
Does anyone have any idea what happened?  

BTW - The above Xorg.conf file is for an R3000Z model Compaq.  Now the scrolling and tapping work properly.  But I still need an explanation as to what the hell I did?

* I just realized I removed my USB mouse before rebooting...any ideas?

---

### Post by jjoyner on 2005-10-30
Dammit...rebooted and now it's gone again...

...eh...help?

---

### Post by jjoyner on 2005-10-30
Ok...I removed my USB mouse, sudo sh -c blah blah blah....reboot and scrolling works now...

How do I avoid loosing this when I plug in my USB mouse and want to use the touchpad later????

---

