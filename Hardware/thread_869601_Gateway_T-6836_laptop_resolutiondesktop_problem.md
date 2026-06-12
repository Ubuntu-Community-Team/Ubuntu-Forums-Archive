---
title: "Gateway T-6836 laptop resolution/desktop problem"
date: 2008-07-25
forum: Hardware
---

### Post by Ecologger on 2008-07-25
I just installed Ubuntu 8.04 Hardy Heron on my laptop and I am unable to use the correct graphics drivers. There are several issues:
The login screen is about 3/4 the size of the laptop screen.
When loaded the top gnome panel does not extend all the way to the right and video does not play unless in full screen mode. Trying to configure the display properties I see that the driver being used is (none). I change to the i810 intel graphics driver and reboot. The driver does not work and I am stuck at 800x600 until a random reboot sets it back to 1200x800 without the ability to extend the top panel all the way to the right. I had also got it to a point where the desktop environment would only appear in the top,left 3/4 of the screen, even though my mouse could travel the entire screen. Any ideas?
xorg:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
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

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by snyperx on 2008-07-25
I have a Gateway 6721 with the same issue.  Hopefully someone will chime in.  I haveno clue how to fix it.

---

### Post by Ecologger on 2008-07-25
Thank god. I thought I was the only one. I have scoured the internet looking for a clue but so far have turned up nothing.

---

### Post by Ecologger on 2008-07-25
So I found a solution sort of...
do a gksu displayconfig-gtk
then select generic monitor at 1280 X 1024
still looks kind of fuzzy however

---

### Post by Ecologger on 2008-07-25
except now I cannot run compiz and my color depth is low.

---

### Post by Ecologger on 2008-07-26
I'm still looking for a solid issue. I am assuming I am going to have to edit the xorg but I am not sure what steps to take next. Please help.

---

### Post by kaoskorruption on 2008-07-26
I'm thining of getting this laptop as well, and I was just wondering if you've made any progress with this issue.

You have the integrated Intel graphics correct?

---

### Post by Ecologger on 2008-07-26
I have not fixed it yet. I do have the intel X3100 graphics chip or also known as GM965 intel chip.

---

### Post by kaoskorruption on 2008-07-26
Yikes.

Well, for the price it is a good laptop and it's gotten so many good reviews. The 1600 version is the same thing with an AMD processor and ATI graphics.

Do you think that this would work better?

---

### Post by Ecologger on 2008-07-26
I couldn't tell you because I still can't identify the problem.

---

### Post by kaoskorruption on 2008-07-26
What's strange is that Dell's laptops that come pre-loaded with Ubuntu have the exact same graphics setup.

BTW, did you use the 64bit version of Ubuntu or normal?

---

### Post by Ecologger on 2008-07-26
64 bit, I think it may have to do with the screen and ubuntu not being able to match the intel graphics driver to the screen.I am trying to find match in the displayconfig but it is kind of like shooting in the dark.

---

### Post by kaoskorruption on 2008-07-27
[http://ubuntuforums.org/showthread.php?t=845086&highlight=resolution+nvidia](http://ubuntuforums.org/showthread.php?t=845086&highlight=resolution+nvidia)

Try this, perhaps it will work.

---

### Post by Ecologger on 2008-07-29
NO its an intel chip, not an Nvidia one. I tried for a solid 7 days to resolve this issue but I got nowhere. So I ditched Ubuntu and installed Mac Pup (puppy linux) instead. It still sometimes won't load Xorg stating that the intel chip device is not recognized and the 915 resolution does not solve it, but other times it works. I don't pretend to understand it but I would stay away from Ubuntu if you have this laptop, atleast for now.

---

### Post by antmo on 2008-07-31
fwiw, i've got the same issue on my 6836 as well.  i've seen this before on other laptops i've owned and it typically went away if i did a "restart" from windows as opposed to "shutdown" and then powering back on to boot into linux.  i have a feeling that there's some weirdness with this laptop's bios which isn't initializing the graphics subsystem properly.  besides for having to run windows at the moment (i prefer linux, but all i really need is something that'll run vim, perl, python, java, firefox, openoffice and play my flac images through a sound card), it's a nice little computer.

mjb

---

### Post by Ecologger on 2008-08-01
Well I actually found a work around... sort of. Xorg will not stay still, you have to set up the monitor, screen, and card all manually. But sometimes when you restart Xorg will revert for no reason at all. when you get a monitor setting working save the info in the gtk displayconfig window. Here is the Xorg:
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
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "device" #  
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" #  
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

But under screen modes you have to add in 1280x800@60, then restart Xorg and go to displayconfig-gtk and change monitor resolution to 1280x800.
BTW I have full acceleration compiz and all that Jazz. The trouble is keeping Xorg from overwriting my changes.

---

### Post by kaoskorruption on 2008-08-03
I just got the laptop.

I noticed that checking the "Clone Screens" box basically fixed the problem. The only thing is that when you do this, it stretches the screen out slightly, rather than making it widescreen dimensions.

I might make a post about this, with a picture just for fresh help.

---

### Post by kaoskorruption on 2008-08-04
Hey everybody,

I just opened a new post to see if I could maybe put the problem into different words and give it another chance, and it worked: 
[http://ubuntuforums.org/showthread.php?p=5519365#post5519365](http://ubuntuforums.org/showthread.php?p=5519365#post5519365)

```
xrandr --output TV --off
```

K2712 was very nice and he managed to find the cure. It was SO simple too! I hope this helps everybody.

---

