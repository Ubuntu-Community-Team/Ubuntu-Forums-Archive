---
title: "[resolved] IBM ThinkPad 1161 (i Series 1200) screen resolution on Xubuntu 8.04"
date: 2009-05-17
forum: Hardware
---

### Post by virgo977virgo on 2009-05-17
Using advice from this site [http://d.hatena.ne.jp/kamekamekame877/20090122]("http://d.hatena.ne.jp/kamekamekame877/20090122") I made a working xorg.conf supporting the resolution 1024x768 in full screen.

```

# tested with Xubuntu 8.04

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Silicon Motion LynxEM+ (generic)"
	Busid		"PCI:0:2:0"
	Driver		"siliconmotion"
	Screen	0
	Vendorname	"Silicon Motion"
	Option "UseBIOS" "off"
	Option "fifo_aggressive"
#	Option "fifo_moderate"
#	Option "fifo_conservative"
	Option "pci_burst" "on"
	Option "pci_retry" "on"
	Option "AccelMethod" "EXA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"Default Screen"
	Inputdevice	"Mouse0"
EndSection

Section "Module"
#	Load		"GLcore"
#	Load		"v4l"
EndSection

```

To use this xorg.conf in your system open as root the file */etc/X11/xorg.conf* with the following command:

```
sudo mousepad /etc/X11/xorg.conf
```

replace the file content with the code posted above and reboot your system.

For more advice on X configuration do refer to the following pages:
[LIST]
[*][https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")
[*][http://www.x.org/wiki/FAQ]("http://www.x.org/wiki/FAQ")
[/LIST]

---

### Post by kamala.ferris on 2009-09-02
I just used this solution to fix the display on my VersaTab II (also called a WalkAbout Hammerhead XRT), running Ubuntu 9.04.  I did have to make a couple modifications that I thought I would explain here.

I had to change the Device Bus ID (obviously) - to get your Bus ID, run lspci, find your VGA compatible controller (Silicon Motion, Inc. SM712 LynxEM+ on my system), and your Bus ID is the series of numbers on the left.  
```

> lspci
02:05.0 VGA compatible controller: Silicon Motion, Inc. SM712 LynxEM+ (rev a0)

```The format in the lspci printout is different from what is required in the xorg file... the last two numbers in the lspci display are separated by a period (.); in the xorg file, this should be a colon {:}, as shown above.  

The other thing I changed was my default resolution - in the example above it's 1024x768, but the max res on my machine is 800x600, so I changed it accordingly.  Hope that helps others.  

Many thanks to virgo977virgo!!! :KS

---

