---
title: "xorg won't set lcd res."
date: 2005-11-08
forum: General Help
---

### Post by slimg on 2005-11-08
I use Kubuntu 5.10, but i've also tried ubuntu 5.10 and got the same problem so i've figured it's the xorg that is my problem.

Laptop with:
Centrino CPU
12" (native res.: 1280x800) LCD
Intel 855GME chipset
Intel Extreme Graphics 2 (8000KB shared memory) graphic card

I'm a noob, i have only managed to learn some of the basics in the linux system so far.

My problem is that when i run:
sudo dpkg-reconfigure xserver-xorg
It allways ends up setting the res. 1024x768 and not 1280x1024 after reboot, i can choose from a list of resolutions after reboot but i can only select 640x480, 800x600 and 1024x768, never get any higher res. option.

i've tried both i810 and vesa driver, and every time i autodetect the display i either get logged out or the config gui returns that i have a generic CRT display.

I've searched quite a lot around in the forums, tried around with the 810resolution without luck, i also got a suggestion that the problem was that the graphic card uses shared memory and x have trouble defining the shared memory (also that i needed an extra module to do the job: agpgart)

i really hope someone could help me, this is the best os i've ever used, it looks slick and it's rock stable :).

---

### Post by Teroedni on 2005-11-08
have you tried a modeline generator?

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

tell me if you need help in xorg configuration

---

### Post by slimg on 2005-11-08
Modline didn't work.
Here's my xorg.conf file:
_________________________________________________________-
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ieg2"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	VideoRam	8000
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ieg2"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
____________________________________________________

Hope this could give you a clue or something.

---

### Post by Teroedni on 2005-11-08
```
 SubSection "Display"
Depth 24
Modes "1280x800@60" "1280x800"
EndSubSection
EndSection
```


I f you add "1280x800@60" in subsection display depth24 as in the example over it should work;)

---

### Post by slimg on 2005-11-08
Still just giving me the options between
1024x768 (default)
800x600
640x480

The Refreshrate List only has one "0 Hz" option.

it seems as no matter what i do with xorg.conf i end up with exacly those choice i described above

---

### Post by Teroedni on 2005-11-08
could you post Xorg log

sudo gedit /var/log/Xorg.0.log


post the whole file in the pastebin
[http://pastebin.com](http://pastebin.com)

---

### Post by slimg on 2005-11-08
I DID IT THANKS TO YOU! :)

I read the log and realised that all the VBIOS modes above 1024x768 was emty (no name, no values)
So i apt-get install 855resolution and setup mode 7e with 1280x800 (that was my original mode for that resolution)

Now my screen is as crystal clear as ever :) thanks for showing me the log, btw: i've never read such an easy log :)

You have made my day fantastic, can't thank you enough!

Have a splendid day!

---

