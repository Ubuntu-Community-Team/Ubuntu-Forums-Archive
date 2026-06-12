---
title: "Logitech MX700"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by luke1 on 2007-05-28
Im trying to get the thumb buttons working on my mx700 and have succeeded but with one problem. The button above my scrollwheel that should scroll up does scroll up, but also presses the back button twice, just wondered if anyone could help. To make it work all I did was alter the mouse input in xorg.conf to:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 6 7"
EndSection

but as I said this makes one of my buttons do two things. :(

It also doesn't seem to be a mapping problem, as no matter how I map the buttons it always presses back twice, even when its mapped as right click or middle mouse or anything it still clicks back twice as well as what its assigned, I really don't know what its up to...
__________________

---

### Post by luke1 on 2007-05-28
I've now altered xorg.conf to use evdev:

Section "InputDevice"
	      Identifier     "Configured Mouse"
	      Driver           "evdev"
	      Option          "Name"			 "Logitech USB Receiver"
	      Option          "Phys"                       "usb-0000:00:1d.1-1/input0"
	      Option          "Device"                    "/dev/input/mice"
	      Option          "Protocol"                 "evdev"
	      Option          "ZAxisMapping"       "4 5"
	      Option          "Buttons"                  "10"
	      Option          "Resolution"             "800"
	      Option          "Emulate3Buttons" "no"
	    EndSection

but im still getting the same problem, i wonder if its something wrong with the mouse itself but what could it be? it works find under windows... its just so irritating to have it almost working

---

### Post by luke1 on 2007-05-29
Doesnt matter now I've fixed it, turns out that it works if you just plug the keyboard and mouse in seperately in the ps/2 ports rather than the usb port, don't know why but it just works that way, all my mouse buttons work now as do my keyboard multimedia buttons :D

---

### Post by kraftm on 2007-05-30
I'm using an MX900 (Bluetooth) and have the same issue.  Pressing up button (above wheel) displays a mousebutton of 8 then 4 then 8 in xev.

Anyone found a solution?

Thanks,
Mark

> **luke1 said:**
> Doesnt matter now I've fixed it, turns out that it works if you just plug the keyboard and mouse in seperately in the ps/2 ports rather than the usb port, don't know why but it just works that way, all my mouse buttons work now as do my keyboard multimedia buttons :D

---

### Post by slick1537 on 2007-05-30
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

works for me with my mx3200 mouse and keyboard.  I believe ZAxisMapping controls the mouse wheel.

---

### Post by kraftm on 2007-05-31
Luke1,

Thanks for the help, but it doesn't work for the MX900...

It's still mapping the up / down arrow buttons as 4 & 5 (same as mouse wheel).  And it doubles up the 4 & 6 buttons when I press the up arrow.

Anyone else have any suggestions??

Mark

---

### Post by mohbana on 2008-01-27
> **slick1537 said:**
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 2 3 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

works for me with my mx3200 mouse and keyboard.  I believe ZAxisMapping controls the mouse wheel.

I can confirm that this also works on my Ubuntu 7.10, fully updated.  Thanks alot slick1

```
uname -r
2.6.22-14-generic

```

/etc/X11/xorg.conf

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option 		"Protocol" 		"ExplorerPS/2"

	Option 		"ZAxisMapping" 		"4 5"
	Option 		"ButtonMapping" 	"1 2 3 6 7"

	#Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


```

---

