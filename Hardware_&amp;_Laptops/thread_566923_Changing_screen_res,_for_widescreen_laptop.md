---
title: "Changing screen res, for widescreen laptop?"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by snocap on 2007-10-04
Hi all I know you have probably seen a post like this before but none of the problems/solutions I've looked up have related to my situation. I am new to Linux and just installed Ubuntu 7.10 on a partition on my HDD. I am trying to change the screen resolution but can't get anything except for 800x600 or 640x480. I have a Fugitsu Lifebook with a widescreen 17 inch LCD. The reason I say I couldn't find others with the same problem is because everyone else seems to have a 1280x740 option as well and I am only getting the lower 2. My optimum resolution is 1440x900. Ive tried editing the xorg.conf but when I set the new parameters nothing happens. Also my xorg file doesn't look anything like the ones I've seen in screenshots on these forums. heres what my xorg file currently looks like. Oh and by the way im using an ATI Mobility Radeon X1400 video card.


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
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

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "(pitch" "800)"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

any ideas? oh and try not to get TOO technical, I am a newbie. Thanks a lot!!

---

### Post by renzokuken on 2007-10-04
at the moment you are using the vesa driver, which is generic and only supports lower resolutions.

use the Restricted Driver Manager to install the ATI driver and you should be able to achieve higher resolutions

---

### Post by snocap on 2007-10-04
Ok I used the restricted drivers manager to install the ATI module. It downloaded a package and installed successfully. After rebooting though I still don't have access to higher resolutions. Heres my xorg.conf now.
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

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

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"800x600"	"(pitch"	"800)"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"800x600"	"(pitch"	"800)"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"800x600"	"(pitch"	"800)"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"800x600"	"(pitch"	"800)"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"800x600"	"(pitch"	"800)"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"800x600"	"(pitch"	"800)"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

thanks for the help

---

### Post by renzokuken on 2007-10-05
now try running

```
sudo dpkg-reconfigure xserver-xorg
```

leave all options as they are except the resolution options, where you should select your desired res.

may need to reboot once finished

---

### Post by snocap on 2007-10-05
Ok well now I have 1024 x 768 available atleast, much easier on the eyes! I selected 1440x900 in the config but it's still not there. My xorg now shows that I'm using vesa, like this:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Should I change that to ATI in the config or leave it alone?

---

### Post by renzokuken on 2007-10-06
change vesa to **fglrx** (the official ati driver)

---

### Post by strabes on 2007-10-06
Run this:```
sudo depmod -a && sudo aticonfig --initial && sudo aticonfig --overlay-type=Xv
```Then restart your X server with Ctrl+Alt+Backspace.

---

### Post by snocap on 2007-10-08
Ok thanks Renzokuken that fixed it finally! Thanks for all of the help. I didn't have to do what you said strabes but thanks for the help anyway!

---

### Post by 0micron on 2007-10-12
Hi, just wanted to mention that 

```
sudo dpkg-reconfigure xserver-xorg
```

worked like a charm for me.

Thanks

---

