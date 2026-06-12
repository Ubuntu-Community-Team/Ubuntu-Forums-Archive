---
title: "Wacom Graphire 3 Problems"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Howitzer on 2005-12-08
I have installed Wacomtools using Synaptic, but in Gimp I can't seem to use pressure sensitivity.  I have searched this forum already for a fix, but was unable to get it working (almost breaking X in the process too).

So far, the tablet can move the cursor, click on stuff, and draw.  What it cannot do is give pressure sensitivity.

I have used **sudo wacdump /dev/input/event2** and it detects my tablet and has no problem seeing the pressure from it.  I don't understand whats going on and I am hoping you can help me.

---

### Post by 23meg on 2005-12-08
Did you enter the required devices along with their options into your xorg.conf file? If so, please post the relevant sections of the file.

---

### Post by Howitzer on 2005-12-08
I'm not sure which sections of xorg.conf are relevant... so here is the entire file

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"cursor"		"SendCoreEvents"
	InputDevice	"stylus"		"SendCoreEvents"
	InputDevice	"eraser"		"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by 23meg on 2005-12-08
Make the following changes and see if it helps.
```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
[COLOR="Red"] Option        "InputFashion" "Tablet"
Option        "SendCoreEvents" "on"
  Option        "Mode"          "absolute" 
  Option        "Speed"         "3.0"
  Option        "Threshold"     "1"
  Option        "Tilt"          "on"
  Option	"Button2"	"3"[/COLOR]
EndSection
```
```

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
[COLOR="Red"]  Option        "InputFashion" "Pen"
  Option        "SendCoreEvents" "on"
  Option        "Mode"          "absolute"
  Option        "Tilt"          "on"
  Option        "TiltInvert"    "on"
  Option        "Threshold"     "1"
  Option	     "Button2"	"3"[/COLOR]
EndSection

```
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
[COLOR="Red"]  Option        "InputFashion" "Eraser"
  Option        "Mode" "absolute"
  Option        "SendCoreEvents" "on"[/COLOR]
EndSection
```

If making them all at once doesn't help, try subtracting the "Button2" options by commenting them out.

---

### Post by 23meg on 2005-12-08
On an unrelated note, you seem to be using the closed source Nvidia drivers and your xorg.conf isn't configured for optimal performance. Make the following changes:

```
Section "Module"
[COLOR="Red"]#[/COLOR]	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
[COLOR="Red"]#[/COLOR]	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

```
[COLOR="Red"]#[/COLOR]Section "DRI"
	[COLOR="Red"]#[/COLOR]Mode	0666
[COLOR="Red"]#[/COLOR]EndSection
```

If that goes fine once you've restarted X, try this:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
[COLOR="Red"]        Option          "RenderAccel" "On"[/COLOR]
EndSection
```

---

### Post by Howitzer on 2005-12-08
Well, thanks, but pressure sensitivity still won't work.  I checked the settings under Gimp as well.  This is frustrating... very-very frustrating.

I'm starting to think Wacom tablets simply don't work properly under Ubuntu.

EDIT:

I tried wacdump again, this time it's not even detecting the pressure.  I looked over the code you gave me, and I think I should erase both instances of   Option        "Mode"          "absolute"

---

### Post by 23meg on 2005-12-08
[QUOTE=Howitzer]I'm starting to think Wacom tablets simply don't work properly under Ubuntu.[/QUOTE]The fact is that they do; mine does, and I've seen others get theirs going so don't worry, it can be sorted.

What are your settings under GIMP? Did you set each of your devices to "screen" mode and what button settings do you use?

Did you try the "GIMP mode" and other options that you can set with xsetwacom? Type ```
xsetwacom list param
``` to see what you can do with it.

Also check out the official docs on [http://linuxwacom.sf.net/](http://linuxwacom.sf.net/) if you already haven't.

---

### Post by 23meg on 2005-12-08
Also try the following, one by one:

- Change the "absolute" values of your eraser and stylus in xorg.conf to "relative"
- Add [COLOR="Red"]Option "TiltInvert" "on"[/COLOR] to the eraser and stylus parts

Here are some links that may be helpful:

[http://www.linuxquestions.org/hcl/showproduct.php/product/186/sort/2/cat/450/page/1](http://www.linuxquestions.org/hcl/showproduct.php/product/186/sort/2/cat/450/page/1)
[https://listas.hispalinux.es/pipermail/gimp/2005-May/000424.html](https://listas.hispalinux.es/pipermail/gimp/2005-May/000424.html)

---

### Post by Howitzer on 2005-12-08
Problem Solved

Apparently I wasn't following directions.  On the [HOWTO: Enable your Wacom Intous/Graphire Tablet with Pressure Sensitivity](http://www.ubuntuforums.org/showthread.php?t=25151) thread it says to do the following:

[color=red]- File-> Preferences-> Input Devices-> "Configure Extended Input Devices".
- Under "Device" you will have 3 settings: Cursor, Eraser and Stylus. Set them from "Disabled" to "Screen".[/color]

I really thank you for your help 23meg, and I have also made the optimial changes to my video settings too.

Once again, thankyou :)

---

### Post by 23meg on 2005-12-08
You're welcome; I'd felt the problem was with GIMP anyway :cool: Happy that you got it sorted.

---

### Post by Howitzer on 2005-12-08
Oh, I changed back to the InputDevice settings because I felt all those extra settings you gave me were unnessesary.

I also changed 	[color=red]Option "Device" "/dev/input/mice"[/color]
to [color=red]Option "Device" "/dev/input/mouse0"[/color] because my mouse is actualy usb, but with a ps2 adapter.  If I had plugged up the mouse to the usb port, I would have suddenly lost the ability to click with the mouse.

**For reference to others...**

In terminal type:
[color=red]sudo gedit /etc/X11/xorg.conf[/color]

Change or add the following in bold(you may save a backup if you wish)
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		**"/dev/input/mouse0"**
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

[B]Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event2"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection[/B]

```
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
[B]	InputDevice	"cursor"		"SendCoreEvents"
	InputDevice	"stylus"		"SendCoreEvents"
	InputDevice	"eraser"		"SendCoreEvents"[/B]
EndSection

```

After that, restart and run Gimp:

[color=red]- File-> Preferences-> Input Devices-> "Configure Extended Input Devices".
- Under "Device" you will have 3 settings: Cursor, Eraser and Stylus. Set them from "Disabled" to "Screen".[/color]

---

### Post by jejones3141 on 2005-12-17
Did that, or tried to; GIMP claimed there weren't any extended input devices.

---

