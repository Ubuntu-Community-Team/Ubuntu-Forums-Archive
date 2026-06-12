---
title: "Nvidia drivers, Viewsonic 19&quot; LCD and its refresh rate."
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by sktrad_ on 2007-10-30
Greetings -

Having installed Ubuntu on a workstation that sports a ViewSonic VX 922 - I was meaning to set it up with its native resolution and refresh rate. 

I have in fact installed my system from a Kubuntu disc, apt-installing later on *ubuntu-dekstop* and all its Gnome offspring.

Now - as things stand now - I can see that the LCD is set on 64KHz horizontal frequency and 60.09 Hz vertical frequency (108.03 pixel clock - whatever that is) - that is what the LCD's OSD reports. 

Upon booting Windows XP I can otherwise read values ov 82-75 on the same OSD screen, which - You've guessed - are actually the native ones. On ViewSonic's site the specs tell:

```

VIDEO INPUT  	Analog/Digital RGB analog etc. DVI-D (TMDS, 100 ohms)
Frequency 	Fh: 30~82kHz, Fv: 50~75Hz
Sync     H/V separated (TTL), composite, sync-on-green
```

I would like to have my LCD to display a v75Hz image. My rig is equipped with a GeForce 8800 GTS 320MB - the Nvidia drivers were installed with adept_manager.

I have edited (various times) the xorg.conf file so that it now reads as:

```

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen0" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Logitech MX518"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
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
	Identifier	"Logitech MX518"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
	#	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Monitor"
	Identifier	"ViewSonic VX 922"
	Modelname	"ViewSonic VX900"
	Vendorname	"ViewSonic"
	Horizsync	30-82
	Vertrefresh	50-80
	modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Device"
	Identifier	"GeForce 8800 GTS"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Screen 0"
	Device		"GeForce 8800 GTS"
	Monitor		"ViewSonic VX 922"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@75"
	EndSubSection
	Option 		"DynamicTwinView" 	"False"
	Option		"NoLogo"		"true"
	Option		"UseEdidFreqs"		"false"
	Option		"ModeValidation"	"AllowNon60HzDFPModes"
EndSection

Section "ServerFlags"
EndSection

```

I've tampered with all the options I could think ov - reading the *xorg.conf* manual and the Nvidia notes. The display module in *kcontrol* now reports (after setting *DynamicTwinView* to 0) a refresh rate ov 75Hz but my LCD disagrees (setting I]DynamicTwinView[/I] to 0 also disables some nvidia-settings options).

To sum it all up, my questions are:

A. Why the dissonance between the LCD's own information and what is reported by the KDE module? Which one do I need to trust, considering the LCD reports the correct refresh rate under the loathed WinXP.

B. How do I set my LCD's refresh rate to its native settings? 1280*1024@75.

C. Why oh why do I see a flurry ov modules being loaded, in Xorg.log.0 (fonts, dbe and whatnot) despite being no mention ov these in xorg.conf (where do they come from?) - as can be read here:

```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux sktrad-zeus 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 30 18:08:03 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen 0" (0)
(**) |   |-->Monitor "ViewSonic VX 922"
(**) |   |-->Device "GeForce 8800 GTS"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Logitech MX518"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1043,8178 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,81a0 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,27e0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,27e2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1043,2601 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:03:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:00:0: chip 1095,3132 card 1043,819f rev 01 class 01,80,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,4362 card 1043,8142 rev 19 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10de,0193 card 1043,823c rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:1:0), (0,5,5), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdbf00000 - 0xdbffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdbe00000 - 0xdbefffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdbd00000 - 0xdbdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(5:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xdf000000/24, 0xe0000000/28, 0xdc000000/25, I/O @ 0xe800/7, BIOS @ 0xdefe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[1] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[2] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[3] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[4] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[5] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[6] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[7] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[8] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[16] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[17] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[18] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[19] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[26] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[27] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[28] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[1] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[2] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[3] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[4] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[5] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[6] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[7] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[8] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[16] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[17] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[18] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[19] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[26] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[27] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[28] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[5] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[6] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[7] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[8] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[9] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[10] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[11] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[12] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[13] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[25] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[32] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[33] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[34] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[5] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[6] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[7] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[8] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[9] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[10] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[11] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[12] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[13] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[25] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[32] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[33] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[34] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[5] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[6] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[7] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[8] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[9] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[10] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[11] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[12] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[13] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[23] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[24] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[25] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[26] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[27] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[28] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[35] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[36] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[37] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[38] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "ModeValidation" "AllowNon60HzDFPModes"
(**) NVIDIA(0): Option "DynamicTwinView" "False"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 327680 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.18.00.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:5:0:0:
(--) NVIDIA(0):     ViewSonic VX922 (DFP-1)
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Mode Validation Overrides for ViewSonic VX922 (DFP-1):
(II) NVIDIA(0):     AllowNon60HzDFPModes
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024@75"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (87, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[8] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[9] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[10] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[11] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[12] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[13] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[14] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[15] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[16] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[30] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[31] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[32] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[39] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[40] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[41] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[42] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x1024@75"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: Core Pointer
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Found 3 relative axes.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Configuring as pointer.
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Found 8 mouse buttons
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: Configuring 3 relative axes.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Configured 10 mouse buttons
(II) XINPUT: Adding extended input device "Logitech MX518-usb-0000:00:1d.0-1/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: 3 valuators.
(**) ../../src/evdev_btn.c (166): Registering 10 buttons.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: On

```

Can You help? Thank You, cheers.

---

### Post by dabl on 2007-10-30
You probably do not have the most recent Nvidia driver, which you really need for that card.  You can check by running ```
nvidia-settings
``` in a console window -- that should bring up the Nvidia configuration utility, and it will say which version is running.

To get the new driver, I recommend downloading and installing the Envy installer. Download the file

envy_0.9.8-0ubuntu10_all.deb

from this web site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Right-click the downloaded file and choose "Open with Gdebi" (or something like that) and install it.  It will put an icon in your System folder, and you can also run it from a console window with ```
sudo envy -t
``` which is helpful after you accept a kernel upgrade and then have no GUI.

After the new driver is installed and the X server has restarted, you can configure your xorg.conf file by entering in a console:

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

and then you can set your default resolution and refresh rates with the settings utility by entering

```
sudo nvidia-settings
```

Click the "X Server Configuration" tab, click "detect displays", then adjust the resolution, and finally the refresh rates.  If it happens that the refresh rate is set to "Auto" like mine, you might want to just leave it there, unless you are seeing screen flicker.  Your last step is to click the "Save To X Configuration File" button in the lower right of the panel, and "x" "merge" and then save.

:guitar:

---

### Post by sktrad_ on 2007-10-30
Hello.

Thanks for the suggestions.

I am already running the latest Nvidia drivers, namely the 100.14.19 ones.

I have already tried setting the refresh rate through nvidia-settings (my Xserver otherwise works flawlessly, including the now configured mouse). 
The problem is: my LCD reports a different refresh rate than the one I set it to (75), which is also reported by *xvidtune*. There's no flicker.

Can my LCD OSD's information be actually incorrect?

PS. I don't want to set the refresh rate to "auto" - otherwise Nvidia will pick its own, according to its (possibly) messed up EDID database (a refresh rate that is as low as 50).

---

### Post by dabl on 2007-10-30
Yes, you do have the new driver -- good!

Hmmmmmmm, I'm not sure what is going on with that Viewsonic, then.

In xorg.conf, I see only a single mode -- 1280x1024@75Hz.  Is that what you intend?  I also see ```
Option		"UseEdidFreqs"		"false"
```   Hmmmmm, I wonder what would happen if you changed that to "true"?????  (Back it up, first!).

---

### Post by sktrad_ on 2007-10-30
The single modeline is the one I intend to use.

As for the ```
Option		"UseEdidFreqs"		"false"
```

... that was my attempt to force the 75 refresh rate: I would otherwise check (within the log) that the nvidia drivers were overwriting my xconf settings with their own metamode (or however they call it), which imposed a refresh ov 60.

Thank You for the prompt answer anyway, it's quite reassuring being welcomed so quickly.

---

### Post by sktrad_ on 2007-10-31
So ... update:

Upon checking nvidia-settings (sudoed - I supposed I needed to do that to write on xorg.conf), I can tell that the driver sets the refresh rate to 60.02Hz - which is what is reported by my monitor. Even though xvidtune, apparently clueless, reports a 75 refresh rate.

The nvidia driver otherwise reports the correct and desired "best fit" and "frontend resolution", it also mentions a TDMS signal, with a double DVI connection link (only one in actual use).

Anybody got a clue? Shall I try and force ("acquire") another EDID to load a proper refresh rate?

---

### Post by dabl on 2007-10-31
> **sktrad_ said:**
> So ... update:

Anybody got a clue? Shall I try and force ("acquire") another EDID to load a proper refresh rate?



That's what I would try, running nvidia-settings as Super User with "sudo".  Then, after doing the EDID acquire, I would set the refresh to 75, and then click the "Save To X Configuration File" button, and "save" this setup. 

Restart the X server with Ctrl-Alt-Backspace and you'll see whether it worked or not.  :)

---

### Post by sktrad_ on 2007-10-31
> **dabl said:**
> That's what I would try, running nvidia-settings as Super User with "sudo".  Then, after doing the EDID acquire, I would set the refresh to 75, and then click the "Save To X Configuration File" button, and "save" this setup. 

Restart the X server with Ctrl-Alt-Backspace and you'll see whether it worked or not.  :)

Been there, done that: *nvidia-settings* modifies xorg.conf, I prefer to do so myself, while checking the drivers' readme.

The EDID acquire actually begs to be fed a .bin which contains the EDID specs and can be generated by several utilities (which, by the way, run on Windows).

Whenever I disable EDID checking, nvidia-auto-select puts me on 640 res mode, even though I specify the desired modelines (namely "1280x1024_75").

I tried starting Xorg with a verbose level ov 5 to see whether I could gain some insight and that's what I learnt:

```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux sktrad-zeus 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 31 16:18:23 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen 0" (0)
(**) |   |-->Monitor "ViewSonic VX922"
(**) |   |-->Device "GeForce 8800 GTS"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Logitech MX518"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 8

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1043,8178 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,81a0 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,27e0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,27e2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1043,2601 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:03:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:00:0: chip 1095,3132 card 1043,819f rev 01 class 01,80,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,4362 card 1043,8142 rev 19 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10de,0193 card 1043,823c rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:1:0), (0,5,5), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdfffffff (0x4000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdbf00000 - 0xdbffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdbe00000 - 0xdbefffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdbd00000 - 0xdbdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(5:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xdf000000/24, 0xe0000000/28, 0xdc000000/25, I/O @ 0xe800/7, BIOS @ 0xdefe0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[1] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[2] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[3] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[4] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[5] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[6] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[7] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[8] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[16] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[17] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[18] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[19] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[26] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[27] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[28] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[1] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[2] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[3] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[4] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[5] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[6] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[7] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[8] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[13] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[16] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[17] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[18] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[19] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[26] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[27] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[28] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[5] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[6] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[7] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[8] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[9] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[10] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[11] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[12] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[13] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[25] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[32] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[33] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[34] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[5] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[6] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[7] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[8] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[9] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[10] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[11] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[12] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[13] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[22] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[25] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[32] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[33] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[34] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[5] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[6] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[7] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[8] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[9] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[10] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[11] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[12] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[13] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[23] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[24] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[25] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[26] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[27] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[28] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[35] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[36] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[37] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[38] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "false"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "TwinView" "false"
(**) NVIDIA(0): Option "MetaModes" "1280x1024_75, 1280x1024_75"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 327680 kBytes
(II) NVIDIA(0): GPU Architecture: 0x50
(II) NVIDIA(0): GPU Implementation: 0x50
(II) NVIDIA(0): GPU Revision: 0xa2
(II) NVIDIA(0): GPU RAM Type: GDDR3
(--) NVIDIA(0): VideoBIOS: 60.80.18.00.01
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, DFP-1, TV-0
(II) NVIDIA(0): Bus detected as PCI Express
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): SPS  : 6
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce 8800 GTS
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 32767
(II) NVIDIA(0):     Horizontal Blank Start   : 32767
(II) NVIDIA(0):     Horizontal Blank Width   : 32767
(II) NVIDIA(0):     Horizontal Sync Start    : 32767
(II) NVIDIA(0):     Horizontal Sync Width    : 32767
(II) NVIDIA(0):     Horizontal Total Width   : 32767
(II) NVIDIA(0):     Vertical Visible Height  : 32767
(II) NVIDIA(0):     Vertical Blank Start     : 32767
(II) NVIDIA(0):     Vertical Blank Width     : 32767
(II) NVIDIA(0):     Veritcal Sync Start      : 32767
(II) NVIDIA(0):     Vertical Sync Width      : 32767
(II) NVIDIA(0):     Vertical Total Height    : 32767
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 8
(II) NVIDIA(0):     Vertical Total Height    : 5
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 1
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 1
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 1
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 1
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 1
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 1
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:5:0:0:
(--) NVIDIA(0):     ViewSonic VX922 (DFP-1)
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): Internal Dual Link TMDS
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): Native FlatPanel Scaling is
(--) NVIDIA(0):     supported
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): DFP modes are not limited to 60 Hz
(--) NVIDIA(0):     refresh rate
(--) NVIDIA(0): ViewSonic VX922 (DFP-1): DFP is not internal to notebook
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for ViewSonic VX922 (DFP-1) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : VSC
(--) NVIDIA(0): Monitor Name                 : ViewSonic VX922
(--) NVIDIA(0): Product ID                   : 44316
(--) NVIDIA(0): 32-bit Serial Number         : 16843009
(--) NVIDIA(0): Serial Number String         : PXU060703418
(--) NVIDIA(0): Manufacture Date             : 2006, week 7
(--) NVIDIA(0): DPMS Capabilities            : Active Off
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 370mm x 300mm
(--) NVIDIA(0): Valid HSync Range            : 30.0 kHz - 82.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 50 Hz - 75 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 140.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   640  x 480  @ 72 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 56 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 72 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 70 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0):   1280 x 1024 @ 75 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   1280 x 960  @ 60 Hz
(--) NVIDIA(0):   1152 x 864  @ 75 Hz
(--) NVIDIA(0):   640  x 400  @ 70 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1280 x 1024 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 108.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1328
(--) NVIDIA(0):     HSyncEnd, HTotal : 1440, 1688
(--) NVIDIA(0):     VRes, VSyncStart : 1024, 1025
(--) NVIDIA(0):     VSyncEnd, VTotal : 1028, 1066
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for ViewSonic VX922 (DFP-1) ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for ViewSonic VX922 (DFP-1):
(II) NVIDIA(0):   HorizSync   : 30.000-82.000 kHz
(II) NVIDIA(0):   VertRefresh : 50.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):     section)
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for ViewSonic VX922 (DFP-1):
(II) NVIDIA(0):   1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):     HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):     HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):     VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):     VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):     H/V Polarity     : +/+
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for ViewSonic VX922 (DFP-1) ---
(II) NVIDIA(0): "nvidia-auto-select" : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_75"       : 1280 x 1024 @  75.0 Hz  (from: X Configuration file ModeLine)
(II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  75.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x1024_75_3"     : 1280 x 1024 @  75.0 Hz  (from: X Configuration file ModeLine)
(II) NVIDIA(0): "1280x1024_75_0"     : 1280 x 1024 @  75.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x1024_75_1"     : 1280 x 1024 @  75.0 Hz  (from: VESA)
(II) NVIDIA(0): "1280x1024_75_2"     : 1280 x 1024 @  75.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x800_60"        : 1280 x  800 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1280x768_60"        : 1280 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864"           : 1152 x  864 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1152x864_75"        : 1152 x  864 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1152x768"           : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1152x768_55"        : 1152 x  768 @  54.8 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x600d60"         :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525"            :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "832x624"            :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"            :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600d65"         :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x512"            :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525"            :  700 x  525 @  74.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d75"         :  700 x  525 @  74.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d70"         :  700 x  525 @  70.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "700x525d60"         :  700 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512"            :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d75"         :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz  (from: VESA, EDID)
(II) NVIDIA(0): "640x400"            :  640 x  400 @  70.1 Hz  (from: EDID)
(II) NVIDIA(0): "640x400_70"         :  640 x  400 @  70.1 Hz  (from: EDID)
(II) NVIDIA(0): "640x400d60"         :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"         :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x384"            :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x384d55"         :  576 x  384 @  54.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for ViewSonic VX922 (DFP-1): ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): Invalid display device in Mode Description "1280x1024_75"
(WW) NVIDIA(0): Not using mode description "1280x1024_75"; unable to map to
(WW) NVIDIA(0):     display device
(II) NVIDIA(0): Using MetaMode string: "1280x1024_75, 1280x1024_75"
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1280x1024_75,1280x1024_75"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1280x1024_75,1280x1024_75":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1280, 1024]
(II) NVIDIA(0):     ViewSonic VX922 (DFP-1): "1280x1024_75"
(II) NVIDIA(0):         Size          : 1280 x 1024
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1280 x 1024
(II) NVIDIA(0):         Position      : [0, 0, 1280, 1024]
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "nvidia-auto-select" : 1280 x 1024 @  60.0 Hz 
(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz 
(II) NVIDIA(0): "1280x800"           : 1280 x  800 @  60.0 Hz 
(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz 
(II) NVIDIA(0): "1152x864"           : 1152 x  864 @  75.0 Hz 
(II) NVIDIA(0): "1152x768"           : 1152 x  768 @  54.8 Hz 
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  75.0 Hz 
(II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz 
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz 
(II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "840x525"            :  840 x  525 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "832x624"            :  832 x  624 @  74.5 Hz 
(II) NVIDIA(0): "800x600"            :  800 x  600 @  75.0 Hz 
(II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz 
(II) NVIDIA(0): "800x600d65"         :  800 x  600 @  65.0 Hz DoubleScan 
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz 
(II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz 
(II) NVIDIA(0): "800x512"            :  800 x  512 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan 
(II) NVIDIA(0): "700x525"            :  700 x  525 @  74.8 Hz DoubleScan 
(II) NVIDIA(0): "700x525d70"         :  700 x  525 @  70.0 Hz DoubleScan 
(II) NVIDIA(0): "700x525d60"         :  700 x  525 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x512"            :  640 x  512 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x480"            :  640 x  480 @  75.0 Hz 
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz 
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz 
(II) NVIDIA(0): "640x400"            :  640 x  400 @  70.1 Hz 
(II) NVIDIA(0): "640x400d60"         :  640 x  400 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "576x384"            :  576 x  384 @  54.8 Hz DoubleScan 
(II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan 
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan 
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan 
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): 
(II) NVIDIA(0): Computing DPI using physical size from ViewSonic VX922
(II) NVIDIA(0):     (DFP-1)'s EDID and first mode to be programmed on
(II) NVIDIA(0):     ViewSonic VX922 (DFP-1):
(II) NVIDIA(0):   width  : 1280 pixels  370  mm (DPI: 87)
(II) NVIDIA(0):   height : 1024 pixels  300  mm (DPI: 86)
(--) NVIDIA(0): DPI set to (87, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdbffc000 - 0xdbffffff (0x4000) MX[B]
	[8] -1	0	0xdbef8000 - 0xdbefbfff (0x4000) MX[B]
	[9] -1	0	0xdbeffc00 - 0xdbeffc7f (0x80) MX[B]
	[10] -1	0	0xdbdf8000 - 0xdbdfbfff (0x4000) MX[B]
	[11] -1	0	0xdbdff800 - 0xdbdfffff (0x800) MX[B]
	[12] -1	0	0xdbcffc00 - 0xdbcfffff (0x400) MX[B]
	[13] -1	0	0xdbcff800 - 0xdbcffbff (0x400) MX[B]
	[14] -1	0	0xdbcf8000 - 0xdbcfbfff (0x4000) MX[B]
	[15] -1	0	0xdefe0000 - 0xdeffffff (0x20000) MX[B](B)
	[16] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[29] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[30] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[31] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[32] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[39] -1	0	0x00007800 - 0x0000781f (0x20) IX[B]
	[40] -1	0	0x00007400 - 0x0000741f (0x20) IX[B]
	[41] -1	0	0x00007000 - 0x0000701f (0x20) IX[B]
	[42] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Created acpid client socket 14.
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "1280x1024_75,1280x1024_75"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): First mode initialized
(II) NVIDIA(0): Using built-in logo image.
(II) NVIDIA(0): Logo is 744x537 with depth 24.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: Core Pointer
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Found 3 relative axes.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Configuring as pointer.
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: WHEELRelativeAxisButtons: 4 5.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Found 8 mouse buttons
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: Configuring 3 relative axes.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Configured 10 mouse buttons
(II) XINPUT: Adding extended input device "Logitech MX518-usb-0000:00:1d.0-1/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Logitech MX518-usb-0000:00:1d.0-1/input0: 3 valuators.
(**) ../../src/evdev_btn.c (166): Registering 10 buttons.
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: On
AUDIT: Wed Oct 31 16:18:25 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:27 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:29 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:31 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:33 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:35 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:37 2007: 6520 X: client 1 rejected from local host (uid 1000)
AUDIT: Wed Oct 31 16:18:39 2007: 6520 X: client 1 rejected from local host (uid 1000)
(II) Logitech MX518-usb-0000:00:1d.0-1/input0: Off
(II) UnloadModule: "evdev"
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

My modelines (1280x1024_75) make it in the pool and are actually validated! Yet the monitor still reports 60.09Hz - I surrender.

I have come to the conclusion that it must be nvidia's drivers ... which behave differently than in Windows (where the vrefresh rate is 75).

I wonder whether I should test standard vesa drivers ...

Also notice that my assumption that the monitor provided the wrong EDID information to the nvidia drivers was wrong - the EDID numbers look correct (no need to disable EDID checking then).

---

### Post by dabl on 2007-10-31
Hmmmmmmmm.  Kind of a disappointment.  That 8800GTS is pretty new, and they don't put their best programmer on the Linux driver.  Future driver versions will probably do a better job with your card.

I don't supposed you've tried overclocking it with the "Coolbits" option, have you?  I can't imagine that would make any difference.

---

### Post by sktrad_ on 2007-10-31
I haven't overclocked the GTS (I only play one game: Europa Universalis 3, which doesn't require fancy graphics -  soon, perhaps Crysis).

I expect that overclocking it will shorten its lifespan. As the previous 7900GT died on me because of faulty memory I will refrain to do so until I really need to (so why bother buying a 8800 ... good question).

Well, I have learnt my bits of wisdom, by reading here and there about these topics - I will be typing, mostly, on my ubuntu box so I hope I won't notice the below norm refresh rate.

Thank You Dabl for the attention You've given to these issues - thanks for lending a hand :KS

---

