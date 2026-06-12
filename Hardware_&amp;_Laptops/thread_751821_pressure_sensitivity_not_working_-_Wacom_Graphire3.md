---
title: "pressure sensitivity not working - Wacom Graphire3"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by oki-vino on 2008-04-10
Hi! I've tried everything I can find in the forums to get my pressure sensitivity working. The tablet itself works pretty well. 

Sometimes it will have a "stop line" on the screen because the tablet area isn't matching up with the screen area. It's hard to explain, but I have to move the stylus all the way to the opposite side then move it back to get it to use the rest of the screen.

Also, it doesn't differentiate between the eraser and the stylus ends. They both will use the same tool in Gimp. 

Finally, Gimp says there are no extended input devices.

Here is my xorg file..Again, I have tried pretty much every tutorial and post out there. I don't know why it's not working. I have tried /dev/input/wacom also. That was the default.
----------------------------------------------------------
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/event3"
	Option		"Type"	"stylus"
	Option          "PressCurve" "50,0,100,50"# Custom preference
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option 		"USB" 		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/event3"
	Option		"Type"	"eraser"
	Option 		"PressCurve" "50,0,100,50"# Custom preference
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option 		"USB" 		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/event3"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option 		"USB" 		"on"
EndSection
----------------------------------------------------------
And this is under the server stuff
----------------------------------------------------------
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
EndSection
----------------------------------------------------------


Thanks!

---

### Post by oldsoundguy on 2008-04-10
I have an Intuos 3 and this worked for me:
[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

---

### Post by oki-vino on 2008-04-10
Did all the steps, still doesn't have pressure sense.

---

### Post by oki-vino on 2008-04-12
soooo nobody can help me with this?

---

