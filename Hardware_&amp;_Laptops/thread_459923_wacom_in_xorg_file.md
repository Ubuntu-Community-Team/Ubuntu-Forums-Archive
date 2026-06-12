---
title: "wacom in xorg file"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by nutz on 2007-05-31
What are the driver entries below for? If they are for tablet pc's only then why can't remove them? I tried and it hoses my xconfig...



Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

---

### Post by Stephen Howard on 2007-05-31
I removed mine without causing any problem.  Remember that you've also got to delete or comment-out the three equivalent entries in the ServerLayout section.'

Deleting the wacom rubbish will also stop the irritating command line message:  *X Error: BadDevice, invalid or uninitialized input device 169*

---

### Post by nutz on 2007-05-31
Cool; thanks...

---

