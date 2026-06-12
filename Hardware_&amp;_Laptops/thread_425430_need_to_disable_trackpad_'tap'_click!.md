---
title: "need to disable trackpad 'tap' click!"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by zoexii on 2007-04-27
Hello,  I've just installed feisty on a Compaq Presario 1201Z laptop.  I am generally pleased with it, except that I cannot find a way to disable the 'tap clicking' on the trackpad.  It registers unwanted clicks constantly, which can be a disaster, especially with websites that have lots of links.  There's nothing in the GUI to turn this feature off.  That would be a welcome addition.  I did some google searches, and from what I can tell, I need to change an option in /etc/X11/xorg.conf.  I have copied and pasted the sections that seem relevant, but nothing stands out as the problem.   Any help would be appreciated.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

---

### Post by iamaqbot on 2007-04-27
Sounds like you had the same problem as me. This sorted things out for me


[http://ubuntuforums.org/showthread.php?t=421236](http://ubuntuforums.org/showthread.php?t=421236)

---

### Post by zoexii on 2007-05-10
rad bro,
my trackpad woes are over.  sorry to take so long to reply, which brings me to another question... about the forums.  can I set my account to automatically subscribe me to my own posts?  I have to do a search by user name every time I want to find them.

thanks,
zoe

---

