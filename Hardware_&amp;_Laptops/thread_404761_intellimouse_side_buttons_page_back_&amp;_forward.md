---
title: "intellimouse side buttons page back &amp; forward"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by djthain on 2007-04-08
I have a Microsoft Intellimouse Optical USB & PS2 mouse.  The page forward & back buttons don't work.  The mouse has 4 buttons and a wheel that scrolls and when pushed causes the scroll arrows to appear in Firefox.  Is there a way to make the page forward & back buttons work?  I have tried some of the web forum remedies but there are so many different one's, I don't know which one, if any are correct.  The one's I have tried don't work.

Here is my xorg.conf

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
        Option          "Buttons"               "7"
 
	Option		"ZAxisMapping"		"4 5"
#	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by treaz on 2007-05-19
See this thread [http://ubuntuforums.org/showthread.php?t=446212&highlight=microsoft+intellimouse](http://ubuntuforums.org/showthread.php?t=446212&highlight=microsoft+intellimouse)

---

