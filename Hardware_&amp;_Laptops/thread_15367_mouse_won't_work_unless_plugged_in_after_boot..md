---
title: "mouse won't work unless plugged in after boot."
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by maccam on 2005-02-14
Hi, Linux Newbie here. I've played around with Fedora and Knoppix before, however, I've found a keeper in Ubuntu (Warty for now). I've got everything working just about the way I want outside a few nitpicks. (with a lot of help from searching these boards) However, I find this problem annoying.

If the mouse is plugged in while booting, the proccess hangs for awhile during both the Starting Hotplug Subsystem and Configuring Network Interface bits. Also, the mouse will not work. It's an older USB Logitech first wheel mouse. It doesn't matter if  the mouse is in a USB port or connected with a USB to PS/2 converter.  Searching for a solution has proven fruitless thus far. 

Thanks in advance!

EDIT> actually, with the PS2 converter the mouse works but I have no network connection.

---

### Post by Xian on 2005-02-14
In your /etc/X11/XF86Config-4 file what is listed in the "InputDevice" Section?
For example, here is mine:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

---

### Post by maccam on 2005-02-14
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

---

### Post by Xian on 2005-02-14
[QUOTE=maccam]If the mouse is plugged in while booting, the proccess hangs for awhile during both the Starting Hotplug Subsystem and Configuring Network Interface bits.[/quote]
I do not find this terribly odd and doubt it is related to your larger issue - no mouse functionality.

[QUOTE=maccam]Also, the mouse will not work. It's an older USB Logitech first wheel mouse. It doesn't matter if  the mouse is in a USB port or connected with a USB to PS/2 converter.  Searching for a solution has proven fruitless thus far. [/QUOTE]
I have no explanation save that the setting in your Xconfig might need to be altered. If the config matches your hardware it should work, save there is another problem associated with your hardware. I am not familiar with your exact mouse, but as you say if you have searched for the correct entry in your Xconfig, and that is what is recommended, then I'd say it's time to go shopping. 

Maybe someone has a loaner you can try just to troubleshoot. :)

---

### Post by maccam on 2005-02-14
Yeah I've been meaning to try another mouse. This one is just about done.

I'll try...

---

### Post by maccam on 2005-02-14
The issue remains with a different mouse

---

