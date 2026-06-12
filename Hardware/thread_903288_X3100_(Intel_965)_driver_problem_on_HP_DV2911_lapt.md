---
title: "X3100 (Intel 965) driver problem on HP DV2911 laptop with Hardy Heron"
date: 2008-08-28
forum: Hardware
---

### Post by ihamid on 2008-08-28
Hi all,

I've always had machines with NVidia hardware and have never had problems with them under Kubuntu. Recently I bought a new HP DV2911 laptop with an X3100 graphics system, which I found has an Intel 965 chipset. Upon installing Hardy Heron, it doesn't automatically detect the chipset and uses the generic Vesa driver. When I tried to change the driver to Intel 965 from the System Settings, it gives a distorted screen if I restart X. I am reproducing the xorg.conf file produced by the System Settings utility:

```
[FONT="Courier New"]Section "InputDevice"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 965"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
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
	Boardname	"Intel 965"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" # 
	Identifier	"monitor1"
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
EndSection

Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection[/FONT]

```
Any help in this regard would be highly appreciated.

TIA,
Irfan.

---

### Post by overdrank on 2008-08-28
> **ihamid said:**
> Hi all,

I've always had machines with NVidia hardware and have never had problems with them under Kubuntu. Recently I bought a new HP DV2911 laptop with an X3100 graphics system, which I found has an Intel 965 chipset. Upon installing Hardy Heron, it doesn't automatically detect the chipset and uses the generic Vesa driver. When I tried to change the driver to Intel 965 from the System Settings, it gives a distorted screen if I restart X. I am reproducing the xorg.conf file produced by the System Settings utility:

```
[FONT="Courier New"]Section "InputDevice"
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
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 965"
	Busid		"PCI:0:2:0"
	[COLOR="Red"]Driver		"i810"[/COLOR]
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
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
	Boardname	"Intel 965"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
[COLOR="Red"]	Driver		"vesa"[/COLOR]
	Screen	0
EndSection

Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection

Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection[/FONT]

```
Any help in this regard would be highly appreciated.

TIA,
Irfan.

Hi and this is the second time I have seen two drivers listed in the xorg. It has the i810 driver and the vesa listed as I have highlighted. Have you tried and use the xfix option from recovery mode? How much memory is shared with the graphics as this may cause some issues.

---

### Post by Juhla Mokka on 2008-08-28
*Edit.Just found a thread probably more suitable for my trouble ([http://ubuntuforums.org/showthread.php?t=875271](http://ubuntuforums.org/showthread.php?t=875271))*

Hi, I think I may have a similar problem. I have a new laptop running Ubuntu on Hardy and I was trying to run a game called Balazar - but both sound and video are very choppy. My card is 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

I believe Intel has newer driver available on their site than is available via Ubuntu, but it's tarball and I don't know how to install it. [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)

Typing the following code gave me similar output to *ihamid*'s (above), showing both vesa and intel drivers.. ```
cat /etc/X11/xorg.conf

```

Searching a solution, somebody told me to run code  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And now lots of stuff has disappeared..?

```
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
	Option		"Emulate3Buttons"	"true"
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

```

---

