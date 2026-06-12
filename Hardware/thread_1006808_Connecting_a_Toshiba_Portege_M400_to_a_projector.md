---
title: "Connecting a Toshiba Portege M400 to a projector"
date: 2008-12-09
forum: Hardware
---

### Post by Vir Novum on 2008-12-09
First off, I want to thank all the very helpful people here.  It must get tiring answering the same questions over and over.  I appreciate what you guys do, so I did an extensive search both here and with Google before posting this one.

Now, I've wanted to switch over to Ubuntu on my laptop (Toshiba Portege M400, it's a tablet PC with an Intel 945GM display adapter) for a while.  Last week a virus snuck by avast and started redirecting me to annoying web sites and gave me the excuse I needed.  I use my laptop more than my desktop, and use it for only a few things.  If I could get all those things working under Linux, I'd be all set.  On my laptop I mainly use the internet, play flash games, read pdf files, listen to music, and watch movies.  Now the good news is that I got all of that working with Ubuntu 8.10.  The bad news is, when I watch movies I usually hook my laptop up to either a projector or this VGA adapter that lets me hook up to an ordinary TV, and that doesn't work very well.  Here's a link to what I'm talking about:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=578791&CatId=1428](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=578791&CatId=1428)

Anyway, I tried just about every option in the System -> Preferences -> Screen Resolution menu, and it's not giving me a display on the TV.  The only thing that works is rebooting with the TV adapter plugged in, which makes my laptop's BIOS set the VGA port as the primary display, no thanks to linux.  But when I do that, my laptop's LCD display is dim and doesn't have the menus on it, ie, it's working as the secondary display.  While this technically works, it's a huge inconvenience to have to restart my computer every time I want to hook it up to the TV, and then restart it again when I'm done.

xrandr does detect the TV adapter.  Here's the output when it's connected:
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 768
VGA connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
```

The VGA shows up as not being connected when it's disconnected too.

Here's xorg.conf.  It's using the "intel" driver.  I tried using the i810 driver, but that didn't work and besides, everyone seems to recommend the "intel" one.

```
# xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 777
	EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver          "wacom"
	Identifier      "stylus"
	Option		"SendCoreEvents"	"true"
	Option          "Device"        "/dev/input/wacom"
	Option          "Type"          "stylus"
	Option 		"ForceDevice" 	"ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver          "wacom"
	Identifier      "eraser"
	Option		"SendCoreEvents"	"true"
	Option          "Device"        "/dev/input/wacom"
	Option          "Type"          "eraser"
	Option 		"ForceDevice" 	"ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver          "wacom"
	Identifier      "cursor"
	Option		"SendCoreEvents"	"true"
	Option          "Device"        "/dev/input/wacom"
	Option          "Type"          "cursor"
	Option 		"ForceDevice" 	"ISDV4" # Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"
	InputDevice     "cursor"
	InputDevice     "eraser"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
	Option          "Clone" "On"
	Option          "MonitorLayout" "CRT,LFP"
EndSection
```

I added the "Clone" "On" part after reading it on a website, but I think that only works for the i810 driver.  Regardless, I have the exact same problems when those options aren't there.

Honestly, I'd be happy if the display was cloned to the VGA and LCD displays.  I don't need to do any of that fancy xinerama stuff, I just want to be able to get this laptop to output a signal on it's VGA port without a lot of messing around.  Any help would certainly be appreciated. :KS

---

### Post by Vir Novum on 2008-12-10
I did hear that i can use the "toshset" tool for Toshiba laptops, but it responds with "required kernel toshiba support not enabled".

Does this mean I have to recompile the kernel in order to use the VGA port on my laptop.  I sure hope not. :(

---

### Post by MWorks on 2009-01-31
Hi, similar problem here... when I connect my dual screen to my laptop (same one m400) it just turns blue... what can I do? Thx!!

---

