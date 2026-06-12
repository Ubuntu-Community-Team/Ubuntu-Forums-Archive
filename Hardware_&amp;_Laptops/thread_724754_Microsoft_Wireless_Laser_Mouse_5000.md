---
title: "Microsoft Wireless Laser Mouse 5000"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by Literati on 2008-03-14
I know that this has been asked before. And I know this isn't the BEST mouse to be using with Linux (apparently anyway) But in none of the other threads have I found an answer to my problem.

First of all. 
I want my mouse to be able to use it's side buttons as a back/forward button.
Linux RECOGNIZES that the buttons exist (Currently, the very left hotkey does what the middle click does (Open a new tab when clicked over a link), and the right hotkey does a simple right click)  
But like I say, I'd like them to be a back/forward function.

Here is my Xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "9"
	Option		"ButtonMapping" "1 2 3 6 7 8 9"
EndSection

I've tried Emulate3Button to True.
I've tried "Buttons" 7
I've tried "Button Mapping" "1 2 3 6 7"
I've tried "Button Mapping" "1 2 3 4 5"

I have NO IDEA what to try next. :(

---

### Post by Literati on 2008-03-15
There must be someone who can configure this mouse :(

---

### Post by Bartender on 2008-03-15
I haven't tried this, so can't say whether it'll work or not...

[http://www.linux.com/feature/126295](http://www.linux.com/feature/126295)

This btnx utility sounds interesting.  Looks like you can download an Ubuntu version if you know how.  If there's not a btnx in the repos I expect there soon will be.

---

