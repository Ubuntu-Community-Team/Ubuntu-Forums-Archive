---
title: "Problem with 4-button mouse"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by anglozaxxon on 2007-05-26
I've got a Microsoft Notebook Optical mouse --  a pretty ordinary mouse with the usual two buttons and a wheel, but also another button under the thumb.  Ubuntu seems to have defaulted the thumb button to the right button; if I check the output of xev, it shows the same event for both buttons as button 3.  However, I would like the thumb button to function as clicking the scroll wheel, which xev reports as button 2.  I'm not sure how to go about this.  It's practically a fresh install of Ubuntu, but here's the relevant (I think) section of xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

Thanks!

---

### Post by Kobalt on 2007-05-26
Check [this]("https://help.ubuntu.com/community/ManyButtonsMouseHowto") out.

---

### Post by affected on 2007-06-21
I had the same problem with the same mouse, couldn't figure it out until I looked up what I'd done with a different mouse on a different system. Basically, using the ExplorerPS/2 protocol seems to have fixed it.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Buttons"		"8"
	Option		"CorePointer"		
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"ButtonMapping" 	"1 7 3 6 2 8"
	Option		"Emulate3Buttons"	"true"
EndSection


That's the entire section in case there's something else there that you don't have. The Buttonmapping line maps button 7 to button position 2, since position 2 is, as far as the OS is concerned, the middle mouse button, and button 7 is what xev told me the side button was. You could also do the remapping with xmodmap, but you'd have to either run that each time you boot or make a boot-time script. Easier to put it in xorg.conf.

I hope this helps.

---

