---
title: "Odd left mouse event behaviour insists on pasting from clipboard"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by Claudia Frers on 2006-04-14
Problem: 
I copy some text to the copy board (I did it from gmail)
and click on the left mouse
to notice that it insists on pasting the text on the editor or
text field that I am trying to type in.

It seems to emulate middle button behaviour for the left button.

for the specified versions below: 
Using Ubuntu 5.10
mouse: Contour classic roller mouse
switch settings: mode s (usb)

and 
Having read:
[http://www.contourdesign.com/rollermouse/rm1_drivers.htm](http://www.contourdesign.com/rollermouse/rm1_drivers.htm)

and configured the following changes to xorg.conf:
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
#	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection

Note that I have tried to change the value 
of 
Option		"Emulate3Buttons"	
to both "true" or "false" 
rebooting of course each time
but with no changed behaviour as a result.

IOW, I still experience the following annoying symptoms.
Been at this for weeks and my head is starting to ](*,) 
Can anyone help me out?

---

