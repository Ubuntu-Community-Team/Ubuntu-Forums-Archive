---
title: "Ati Hd 2600 Xt 512mb Gddr3"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by Ricardo Matos on 2008-01-09
Hi everyone!!

i have a ATI HD 2600 XT 512MB GDDR3 DVI PCi-x on a brand new box with a plain vanilla UBUNTU 7.10 installation.

I was having trouble to setup my Graphics card until i found the posts in this forum and follow up the guide lines presented.

i have followed instructions exactly as in:

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Afterwards i was able to have the correct driver installed, enable desktop effects, stop the existing flickering and configure settings on the ATI Catalist Control Center.

However, whenever i run some games like Open Arena the screen goes Black and i have to reboot the machine. Another example is the Rhytmbox when i enable the visualization mode with the cool effects i get some horrible flickering...

Can anyone help me?

Thank you in advance...

My fglrxinfoI:

:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7170 Release



My dmesg:


[ 37.678927] [fglrx] Reserve Block - 0 offset = 0X1fffc000 length = 0X4000
[ 37.678934] [fglrx] Reserve Block - 1 offset = 0X0 length = 0X1000000
[ 37.678936] [fglrx] Reserve Block - 2 offset = 0Xff7f000 length = 0X80000
[ 37.921964] [fglrx] interrupt source 60000001 successfully enabled
[ 37.921971] [fglrx] enable ID = 0x00000006
[ 37.921981] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[ 37.922044] [fglrx] interrupt source 00000040 successfully enabled
[ 37.922046] [fglrx] enable ID = 0x00000007
[ 37.922050] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[ 37.930479] [fglrx] interrupt source ff00002c successfully enabled
[ 37.930482] [fglrx] enable ID = 0x00000008
[ 37.930488] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[ 37.930529] [fglrx] interrupt source ff00002d successfully enabled
[ 37.930532] [fglrx] enable ID = 0x00000009
[ 37.930535] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[ 37.930566] [fglrx] interrupt source 20000400 successfully enabled
[ 37.930568] [fglrx] enable ID = 0x0000000A
[ 37.930571] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[ 42.783396] hda-intel: Invalid position buffer, using LPIB read method instead.
[ 45.895026] eth0: no IPv6 routers present
[ 57.299441] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list
[ 57.388929] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.432790] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.501957] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.544431] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.616206] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.659308] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.748072] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 57.790043] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 93.312136] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 93.528090] [fglrx] interrupt source 20000400 successfully disabled!
[ 93.528095] [fglrx] enable ID = 0x00000000
[ 93.528098] [fglrx] Receive disable interrupt message with irqEnableMask: 20000400; dwIRQEnableId: 0000000a
[ 93.528107] [fglrx] interrupt source ff00002d successfully disabled!
[ 93.528108] [fglrx] enable ID = 0x00000000
[ 93.528110] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002d; dwIRQEnableId: 00000009
[ 93.528116] [fglrx] interrupt source ff00002c successfully disabled!
[ 93.528118] [fglrx] enable ID = 0x00000000
[ 93.528120] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002c; dwIRQEnableId: 00000008
[ 93.528126] [fglrx] interrupt source 00000040 successfully disabled!
[ 93.528127] [fglrx] enable ID = 0x00000000
[ 93.528129] [fglrx] Receive disable interrupt message with irqEnableMask: 00000040; dwIRQEnableId: 00000007
[ 93.528135] [fglrx] interrupt source 60000001 successfully disabled!
[ 93.528137] [fglrx] enable ID = 0x00000000
[ 93.528139] [fglrx] Receive disable interrupt message with irqEnableMask: 60000001; dwIRQEnableId: 00000006
[ 100.303985] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 100.556641] [fglrx] Reserve Block - 0 offset = 0X1fffc000 length = 0X4000
[ 100.556646] [fglrx] Reserve Block - 1 offset = 0X0 length = 0X1000000
[ 100.556649] [fglrx] Reserve Block - 2 offset = 0Xff7f000 length = 0X80000
[ 100.612406] [fglrx] interrupt source 60000001 successfully enabled
[ 100.612413] [fglrx] enable ID = 0x00000006
[ 100.612423] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[ 100.612485] [fglrx] interrupt source 00000040 successfully enabled
[ 100.612487] [fglrx] enable ID = 0x00000007
[ 100.612491] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[ 100.619311] [fglrx] interrupt source ff00002c successfully enabled
[ 100.619314] [fglrx] enable ID = 0x00000008
[ 100.619320] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[ 100.619360] [fglrx] interrupt source ff00002d successfully enabled
[ 100.619362] [fglrx] enable ID = 0x00000009
[ 100.619365] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[ 100.619397] [fglrx] interrupt source 20000400 successfully enabled
[ 100.619399] [fglrx] enable ID = 0x0000000A
[ 100.619402] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[ 111.701243] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000003 not found in mutex list
[ 111.782842] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 111.825040] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 111.900511] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 111.945032] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 112.100391] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 112.146014] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 112.347335] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list
[ 112.390810] [fglrx:firegl_free_mutex] *ERROR* mutex id 0x00000002 not found in mutex list

my XORG:


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1400x1050@75"	"832x624@75"	"1600x1200@65"	"800x600@60"	"1600x1200@60"	"800x600@75"	"1792x1344@60"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerFlags"
EndSection
#Section "Extensions"
#	Option		"Composite"	"0"
#EndSection

---

### Post by rockinlinux on 2008-03-05
do you now if that driver install will work with a ATI HD2600PRo super PCI-E?? I can get my 3d working and have not found much on these cards.

---

