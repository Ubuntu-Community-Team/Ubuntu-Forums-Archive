---
title: "Wacom Volito2 &amp; 7.04"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by william_nbg on 2007-09-10
Just got my 'Wacom Volito 2' pad and it worked right out of the box, but doesn't show up in the Gimp input devices. I can use it in Gimp but can't set up the pressure sen. or anything.

Anyone have this problem and figured out how to fix it?

Would appreciate any help.:)

---

### Post by william_nbg on 2007-09-11
After a little looking around I have found out a few things:

The pad works OK in the 'wacdump' test

But doesn't even show up in xidump

????:(

---

### Post by william_nbg on 2007-09-11
Another thing I've noticed is: I can take the device completely out of 'xorg.conf' 

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "stylus"
  Option        "PressCurve"    "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option  


Which I put in there myself anyway - after removing, restarting X, the pad works just as it had. OK, but can't set it up in Gimp. So the driver seems to work, it show up, but X doesn't recognize it at all??

---

### Post by william_nbg on 2007-09-12
Oh yeah! I figured it out. -sweet!

For some reason when I first plugged the pad in, installed Wacom tools, it didn't write it into my xorg.conf as it should have. I later wrote it in myself - which doesn't really work.

So after sleeping on it - often a good idea. I just ran:

sudo dpkg-reconfigure xserver-xorg

and presto! it was all written into the xorg.conf and X see it - meaning Gimp too.

Now I'm off and drawing.

Hope this helps, if anybody else has the same hang-up.

---

### Post by Segolas on 2007-09-28
can you post your xorg lines?

---

### Post by william_nbg on 2007-09-28
> Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

This is what was generated.

Hope it helps

---

