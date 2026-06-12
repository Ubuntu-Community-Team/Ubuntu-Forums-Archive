---
title: "Unable to startx as user, possible in recovery mode"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by brandon_r87 on 2007-06-04
Hello,

I'm not sure what caused this problem, as I don't believe I edited the xorg.conf file before the problem started.  Anyway, when I start up the computer, I get the Nvidia logo as usual, but after showing me the cursor, the screen goes back to the Kubuntu loading screen.  I use Ctrl-Alt-F1 to get logged in, then use the startx command.  At this point it repeats the logo, but halts on a black screen, sometimes has a large blinking cursor.  After that, Ctrl-Alt-F1 doesn't work, but Ctrl-Alt-F2 and up work with very low resolutions coming up.  Like the title says, if I run startx in recovery mode, it does work.

Edit: I restarted to get an updated xorg log file and got different results.  This time it gave me errors instead of a blank screen.  These errors should be in the updated log file.  Also, I meant to put this in Multimedia & Video but misclicked as Hardware & Laptops.  If someone could move this to the appropriate spot, I'd be grateful.

My xorg.conf
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen[0]"
    Screen 1	   "Screen[1]" LeftOf "Screen[0]"  
    InputDevice    "Keyboard1"
    InputDevice    "Mouse1"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Keyboard1"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "evdev"				###"mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/event9"		###"/dev/input/mice"
    Option	   "Buttons" "8"
    Option	   "ZAxisMapping"	"4 5 7 8"
    ###Option         "Protocol" "ImPS/2"
    ###Option         "ZAxisMapping" "4 5"
    ###Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor[0]" #Gateway Monitor
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier	"Monitor[1]" #TV
    HorizSync	30-50
    VertRefresh	60
EndSection

Section "Device"
    Identifier     "Device[0]" #NVIDIA GeForce 7600GS #1
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    screen 0
EndSection

Section "Device"
    Identifier	"Device[1]" #NVIDIA GeForce 7600GS #1 S-Video Out
    Driver	"nvidia"
    Screen 1
    Option	"TVOutFormat" "SVIDEO"
    Option	"TVStandard" "NTSC"
    Option	"ConnectedMonitor" "Monitor[1]"
    BusID	"PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
	Device		"Device[1]"
	Identifier	"Screen[1]"
	Monitor		"Monitor[1]"
	DefaultDepth	24
	SubSection	"Display"
		Depth 24
		Modes "1024x768_60"
	EndSubSection
EndSection
```

Here's /var/log/Xorg.0.log
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux server1.example.com 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun  4 22:36:32 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen[0]" (0)
(**) |   |-->Monitor "Monitor[0]"
(**) |   |-->Device "Device[0]"
(**) |-->Screen "Screen[1]" (1)
(**) |   |-->Monitor "Monitor[1]"
(**) |   |-->Device "Device[1]"
(**) |-->Input Device "Keyboard1"
(**) |-->Input Device "Mouse1"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,0071 card 1043,8189 rev a3 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,007f card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,0075 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,006f card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:4: chip 10de,00b4 card 0000,0000 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0076 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0078 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,0079 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,007a card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,007b card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,007c card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,007d card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,007e card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,007e card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,007e card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 10de,007e card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 10de,007e card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81bc rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1043,81bc rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81bc rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,0272 card 1043,81bc rev a2 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81bc rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81bc rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81bc rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 1043,818f rev a2 class 04,03,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0392 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0392 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 06:07:0: chip 12d8,8140 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 06:0c:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 07:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 07:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcaffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xcd000000 - 0xcfffffff (0x3000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:5:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:6:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:7:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:16:0), (0,6,7), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xcb000000 - 0xccffffff (0x2000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (6:7:0), (6,7,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xc8000000/24, 0xa0000000/28, 0xc9000000/24, I/O @ 0x9000/7, BIOS @ 0xca000000/17
(--) PCI: (2:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xcd000000/24, 0xb0000000/28, 0xce000000/24, I/O @ 0xa000/7
(--) PCI: (7:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xc0000000/26
(--) PCI: (7:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xc4000000/26
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
	[0] -1	0	0xcc000000 - 0xcc003fff (0x4000) MX[B]
	[1] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[2] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[3] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[4] -1	0	0xd0006000 - 0xd00060ff (0x100) MX[B]
	[5] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[6] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[11] -1	0	0xca000000 - 0xca01ffff (0x20000) MX[B](B)
	[12] -1	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x00005100 - 0x0000513f (0x40) IX[B]
	[28] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[30] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcc000000 - 0xcc003fff (0x4000) MX[B]
	[1] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[2] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[3] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[4] -1	0	0xd0006000 - 0xd00060ff (0x100) MX[B]
	[5] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[6] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[8] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[9] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[11] -1	0	0xca000000 - 0xca01ffff (0x20000) MX[B](B)
	[12] -1	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[17] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[18] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[19] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[20] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[22] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[23] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[24] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[25] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x00005100 - 0x0000513f (0x40) IX[B]
	[28] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[30] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
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
	[4] -1	0	0xcc000000 - 0xcc003fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[7] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[8] -1	0	0xd0006000 - 0xd00060ff (0x100) MX[B]
	[9] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[10] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xca000000 - 0xca01ffff (0x20000) MX[B](B)
	[16] -1	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x00005100 - 0x0000513f (0x40) IX[B]
	[34] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[36] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:2:0:0) found
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc000000 - 0xcc003fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[7] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[8] -1	0	0xd0006000 - 0xd00060ff (0x100) MX[B]
	[9] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[10] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xca000000 - 0xca01ffff (0x20000) MX[B](B)
	[16] -1	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[23] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[24] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[25] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[26] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x00005100 - 0x0000513f (0x40) IX[B]
	[34] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[36] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcc000000 - 0xcc003fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[6] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[7] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[8] -1	0	0xd0006000 - 0xd00060ff (0x100) MX[B]
	[9] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[10] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xca000000 - 0xca01ffff (0x20000) MX[B](B)
	[16] -1	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[36] -1	0	0x00005100 - 0x0000513f (0x40) IX[B]
	[37] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[38] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[39] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-1 is invalid
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.01
(II) NVIDIA(0): Detected PCI Express Link width: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): CRT-1: 342.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 342.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "Monitor[1]"
(**) NVIDIA(1): Option "TVStandard" "NTSC"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "NTSC"
(WW) NVIDIA(1): Unknown TV Standard "NTSC"; defaulting to "NTSC-M"
(II) NVIDIA(1): NVIDIA GPU GeForce 7600 GS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.73.22.16.01
(II) NVIDIA(1): Detected PCI Express Link width: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(1):     CRT-1
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): CRT-1: 342.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 342.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(II) NVIDIA(1): Assigned Display Device: TV-0
(WW) NVIDIA(1): No valid modes for "1024x768_60"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(1): Unable to load "xf86ExecX86int10".
(EE) NVIDIA(1): Unable to initialize the X Int10 module; the console may not
(EE) NVIDIA(1):     be restored correctly on your TV.
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B]
	[1] 0	0	0xa0000000 - 0xafffffff (0x10000000) MX[B]
	[2] 0	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcc000000 - 0xcc003fff (0x4000) MX[B]
	[8] -1	0	0xd0000000 - 0xd0003fff (0x4000) MX[B]
	[9] -1	0	0xd0004000 - 0xd0004fff (0x1000) MX[B]
	[10] -1	0	0xd0007000 - 0xd0007fff (0x1000) MX[B]
	[11] -1	0	0xd0006000 - 0xd00060ff (0x100) MX[B]
	[12] -1	0	0xd0005000 - 0xd0005fff (0x1000) MX[B]
	[13] -1	0	0xc4000000 - 0xc7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc3ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xcd000000 - 0xcdffffff (0x1000000) MX[B](B)
	[18] -1	0	0xca000000 - 0xca01ffff (0x20000) MX[B](B)
	[19] -1	0	0xc9000000 - 0xc9ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B](B)
	[21] -1	0	0xc8000000 - 0xc8ffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] 0	0	0x00009000 - 0x0000907f (0x80) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[30] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[31] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[32] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[33] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[35] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[36] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[37] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[38] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[39] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[40] -1	0	0x00005100 - 0x0000513f (0x40) IX[B]
	[41] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[42] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[43] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(GPU-1): NVIDIA GPU GeForce 7600 GS at PCI:2:0:0 (GPU-1)
(--) NVIDIA(GPU-1): Memory: 262144 kBytes
(--) NVIDIA(GPU-1): VideoBIOS: 05.73.22.16.01
(II) NVIDIA(GPU-1): Detected PCI Express Link width: 8X
(--) NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) NVIDIA(GPU-1): Connected display device(s) on GeForce 7600 GS at PCI:2:0:0:
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(**) Keyboard1: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard1: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Keyboard1: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Keyboard1: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard1: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Mouse1-PNP0C0C/button/input0: Core Pointer
(WW) Mouse1-PNP0C0C/button/input0: does not have core pointer capabilities
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Mouse1-PNP0C0C/button/input0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Keyboard1" (type: KEYBOARD)
(II) Mouse1-PNP0C0C/button/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) Mouse1-PNP0C0C/button/input0: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]
2: /usr/bin/X11/X(main+0x6bf) [0x80749af]
3: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d31ebc]
4: /usr/bin/X11/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

---

