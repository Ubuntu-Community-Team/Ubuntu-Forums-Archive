---
title: "Issues with Multiscreen setup"
date: 2008-08-07
forum: General Help
---

### Post by theurgy on 2008-08-07
Hey guys,

Just switched distros over to Kubuntu 8.04.1 from Xandros Desktop 4.2 Pro.
Now my only gripe in this case is that I am running an ATI card with two monitors that I used to have enabled for Multihead setup.
I tried enabling it in Kubuntu and all I get is failed error messages (I'll paste those in a minute). All I get with my current setup is my screen replicated on my secondary screen.

Here is my current xorg.conf file:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "ca"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```


Now here is my previous xorg.conf file from my Xandros installation which worked beautifully:

```

Section "ServerLayout"
        Identifier     "Xandros"
        Screen         "Screen0"
        Screen         "Screen1" RightOf "Screen0"
        InputDevice    "keyboard"
        InputDevice    "mouse"
        InputDevice    "stylus"
        InputDevice    "eraser"
        InputDevice    "cursor"
        InputDevice    "pad"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules/altdrivers"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
EndSection

Section "Module"
        Load  "ddc"
        Load  "int10"
        Load  "glx"
        Load  "dbe"
        Load  "dri"
        Load  "extmod"
        Load  "record"
        Load  "bitmap"
        Load  "freetype"
        Load  "type1"
        Load  "vbe"
        Load  "xandetect"
EndSection

Section "ServerFlags"
        Option      "AllowMouseOpenFail"
EndSection

Section "InputDevice"
        Identifier  "keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
EndSection

Section "InputDevice"
        Identifier  "mouse"
        Driver      "mouse"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "IMPS/2"
        Option      "Emulate3Buttons" "yes"
        Option      "ZAxisMapping" "4 5"
        Option      "CorePointer"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "USB" "on"
        Option      "Mode" "Absolute"
        Option      "SendcoreEvents" "yes"
        Option      "Type" "stylus"
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "USB" "on"
        Option      "Mode" "Absolute"
        Option      "SendcoreEvents" "yes"
        Option      "Type" "eraser"
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "USB" "on"
        Option      "Mode" "Relative"
        Option      "SendcoreEvents" "yes"
        Option      "Type" "cursor"
EndSection

Section "InputDevice"
        Identifier  "pad"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Mode" "Absolute"
        Option      "USB" "on"
        Option      "Type" "pad"
EndSection

Section "Modes"
        Identifier     "Monitor0"
        ModeLine     "1280x1024@60" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1280x1024@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1152x864@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1024x768@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1024x768@70" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1024x768@60" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@72" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@60" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@56" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "640x480@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "640x480@72" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "640x480@60" 0.0 0 0 0 0 0 0 0 0
EndSection

Section "Modes"
        Identifier     "Monitor1"
        ModeLine     "1280x1024@60" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1280x1024@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1152x864@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1024x768@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1024x768@70" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "1024x768@60" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@72" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@60" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "800x600@56" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "640x480@75" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "640x480@72" 0.0 0 0 0 0 0 0 0 0
        ModeLine     "640x480@60" 0.0 0 0 0 0 0 0 0 0
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Dell"
        ModelName    "1901FP"
 ### Comment all HorizSync and VertSync values to use DDC:
        HorizSync    30.0 - 80.0
        VertRefresh  56.0 - 76.0
        Option      "DPMS" "off"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Dell"
        ModelName    "1901FP"
 ### Comment all HorizSync and VertSync values to use DDC:
        HorizSync    30.0 - 80.0
        VertRefresh  56.0 - 76.0
        Option      "DPMS" "off"
EndSection

Section "Device"
        Identifier  "Device0"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV280 [Radeon 9200 PRO]"
        BusID       "PCI:1:0:0"
        Screen 0
EndSection

Section "Device"
        Identifier  "Device1"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "RV280 [Radeon 9200 PRO]"
        BusID       "PCI:1:0:0"
        Screen 1
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Device0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Depth     8
        EndSubSection
        SubSection "Display"
                Depth     15
        EndSubSection
        SubSection "Display"
                Depth     16
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Device1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Depth     8
        EndSubSection
        SubSection "Display"
                Depth     15
        EndSubSection
        SubSection "Display"
                Depth     16
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```

Now based from that I tried the following as my xorg.conf:

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
EndSection

Section "Device"
	Identifier	"Configured Video Device 0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Configured Video Device 1"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Configured Monitor 0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor 1"
EndSection


Section "Screen"
	Identifier	"Default Screen 0"
	Monitor		"Configured Monitor 0"
	Device		"Configured Video Device 0"
EndSection

Section "Screen"
	Identifier	"Default Screen 1"
	Monitor		"Configured Monitor 1"
	Device		"Configured Video Device 1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0 	"Default Screen 0"
	Screen	1 	"Default Screen 1" RightOf "Default Screen 0"
	Option 		"Xinerama" "true"
EndSection

```

---

### Post by theurgy on 2008-08-07
OK here the output of my /var/log/Xorg.0.log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux mikepc 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  7 17:42:43 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 1043,8159 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0965 card 0000,0000 rev 47 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1043,8139 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1043,810d rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1043,8139 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1043,8139 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1043,8139 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1043,8139 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0190 card 1043,8139 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0182 card 1043,8139 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: 00:09:0: chip 1106,3106 card 1186,1407 rev 86 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,5960 card 174b,0260 rev 01 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5940 card 174b,0261 rev 01 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfbf00000 - 0xfbffffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xf3ffffff (0x14000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe0000000/27, 0xfbfe0000/16, I/O @ 0xe000/8, BIOS @ 0xfbfc0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) rev 1, Mem @ 0xe8000000/27, 0xfbff0000/16
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
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfbefb800 - 0xfbefb8ff (0x100) MX[B]
	[1] -1	0	0xfbefb000 - 0xfbefb7ff (0x800) MX[B]
	[2] -1	0	0xfbefbc00 - 0xfbefbc7f (0x80) MX[B]
	[3] -1	0	0xfbeff000 - 0xfbefffff (0x1000) MX[B]
	[4] -1	0	0xfbefe000 - 0xfbefefff (0x1000) MX[B]
	[5] -1	0	0xfbefd000 - 0xfbefdfff (0x1000) MX[B]
	[6] -1	0	0xfbefc000 - 0xfbefcfff (0x1000) MX[B]
	[7] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[8] -1	0	0xfbff0000 - 0xfbffffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfbfc0000 - 0xfbfdffff (0x20000) MX[B](B)
	[11] -1	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbefb800 - 0xfbefb8ff (0x100) MX[B]
	[1] -1	0	0xfbefb000 - 0xfbefb7ff (0x800) MX[B]
	[2] -1	0	0xfbefbc00 - 0xfbefbc7f (0x80) MX[B]
	[3] -1	0	0xfbeff000 - 0xfbefffff (0x1000) MX[B]
	[4] -1	0	0xfbefe000 - 0xfbefefff (0x1000) MX[B]
	[5] -1	0	0xfbefd000 - 0xfbefdfff (0x1000) MX[B]
	[6] -1	0	0xfbefc000 - 0xfbefcfff (0x1000) MX[B]
	[7] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[8] -1	0	0xfbff0000 - 0xfbffffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfbfc0000 - 0xfbfdffff (0x20000) MX[B](B)
	[11] -1	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfbefb800 - 0xfbefb8ff (0x100) MX[B]
	[5] -1	0	0xfbefb000 - 0xfbefb7ff (0x800) MX[B]
	[6] -1	0	0xfbefbc00 - 0xfbefbc7f (0x80) MX[B]
	[7] -1	0	0xfbeff000 - 0xfbefffff (0x1000) MX[B]
	[8] -1	0	0xfbefe000 - 0xfbefefff (0x1000) MX[B]
	[9] -1	0	0xfbefd000 - 0xfbefdfff (0x1000) MX[B]
	[10] -1	0	0xfbefc000 - 0xfbefcfff (0x1000) MX[B]
	[11] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[12] -1	0	0xfbff0000 - 0xfbffffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfbfc0000 - 0xfbfdffff (0x20000) MX[B](B)
	[15] -1	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbefb800 - 0xfbefb8ff (0x100) MX[B]
	[5] -1	0	0xfbefb000 - 0xfbefb7ff (0x800) MX[B]
	[6] -1	0	0xfbefbc00 - 0xfbefbc7f (0x80) MX[B]
	[7] -1	0	0xfbeff000 - 0xfbefffff (0x1000) MX[B]
	[8] -1	0	0xfbefe000 - 0xfbefefff (0x1000) MX[B]
	[9] -1	0	0xfbefd000 - 0xfbefdfff (0x1000) MX[B]
	[10] -1	0	0xfbefc000 - 0xfbefcfff (0x1000) MX[B]
	[11] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[12] -1	0	0xfbff0000 - 0xfbffffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfbfc0000 - 0xfbfdffff (0x20000) MX[B](B)
	[15] -1	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbefb800 - 0xfbefb8ff (0x100) MX[B]
	[5] -1	0	0xfbefb000 - 0xfbefb7ff (0x800) MX[B]
	[6] -1	0	0xfbefbc00 - 0xfbefbc7f (0x80) MX[B]
	[7] -1	0	0xfbeff000 - 0xfbefffff (0x1000) MX[B]
	[8] -1	0	0xfbefe000 - 0xfbefefff (0x1000) MX[B]
	[9] -1	0	0xfbefd000 - 0xfbefdfff (0x1000) MX[B]
	[10] -1	0	0xfbefc000 - 0xfbefcfff (0x1000) MX[B]
	[11] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[12] -1	0	0xfbff0000 - 0xfbffffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfbfc0000 - 0xfbfdffff (0x20000) MX[B](B)
	[15] -1	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000fbfe0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(--) RADEON(0): BIOS at 0xfbfc0000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 16600, sclk: 166.000000, mclk: 240.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=16600
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): Panel infos found from DDC detailed: 1280x1024
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
(II) RADEON(0): Output DVI-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (380, 310) mm
(**) RADEON(0): DPI set to (85, 98)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfbefb800 - 0xfbefb8ff (0x100) MX[B]
	[7] -1	0	0xfbefb000 - 0xfbefb7ff (0x800) MX[B]
	[8] -1	0	0xfbefbc00 - 0xfbefbc7f (0x80) MX[B]
	[9] -1	0	0xfbeff000 - 0xfbefffff (0x1000) MX[B]
	[10] -1	0	0xfbefe000 - 0xfbefefff (0x1000) MX[B]
	[11] -1	0	0xfbefd000 - 0xfbefdfff (0x1000) MX[B]
	[12] -1	0	0xfbefc000 - 0xfbefcfff (0x1000) MX[B]
	[13] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[14] -1	0	0xfbff0000 - 0xfbffffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0xfbfc0000 - 0xfbfdffff (0x20000) MX[B](B)
	[17] -1	0	0xfbfe0000 - 0xfbfeffff (0x10000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c403 (0x4) IX[B]
	[32] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[36] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x8000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
disable montype: 3
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1838000
(II) RADEON(0): Will use depth buffer at offset 0x1e14000
(II) RADEON(0): Will use 94208 kb for textures at offset 0x23f0000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(==) RADEON(0): Using AGP 8x
(II) RADEON(0): [agp] Mode 0x1f004e0a [AGP 0x1039/0x0760; Card 0x1002/0x5960]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xf4000000
(II) RADEON(0): [agp] Ring mapped at 0xb7928000
(II) RADEON(0): [agp] ring read ptr handle = 0xf4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7ee1000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xf4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xaf663000
(II) RADEON(0): [agp] GART texture map handle = 0xf4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xaf183000
(II) RADEON(0): [drm] register handle = 0xfbfe0000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
disable montype: 3
init memmap
init common
init crtc2
init pll2
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore FP
enable montype: 3
disable montype: 1
disable montype: 3
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 23
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe7ffe000 is: 0xe7ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf47ff400
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xe7ffe000 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xf47ff400
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1205)
(II) RADEON(0): Largest offscreen area available: 1280 x 6982
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 376 x 301
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "ca"
(**) Generic Keyboard: XkbLayout: "ca"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
enable montype: 3
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
enable montype: 1
enable montype: 3
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 400c  Serial#: 1111568728
(II) RADEON(0): Year: 2004  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.641 redY: 0.353   greenX: 0.289 greenY: 0.626
(II) RADEON(0): blueX: 0.142 blueY: 0.078   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: T61164BGBA1X
(II) RADEON(0): Monitor name: DELL 1905FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac0c4058314142
(II) RADEON(0): 	2f0e01030e261f78ee1145a45a4aa024
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00543631
(II) RADEON(0): 	3136344247424131580a000000fc0044
(II) RADEON(0): 	454c4c203139303546500a20000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200065
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16396
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4001  Serial#: 1111709272
(II) RADEON(0): Year: 2004  Week: 5
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 31
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) RADEON(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: 5Y23241PBCVX
(II) RADEON(0): Monitor name: DELL 1901FP
(II) RADEON(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac014058564342
(II) RADEON(0): 	050e010380261f78ee6f86a25a4d9424
(II) RADEON(0): 	1a4f54a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00355932
(II) RADEON(0): 	3332343150424356580a000000fc0044
(II) RADEON(0): 	454c4c203139303146500a20000000fd
(II) RADEON(0): 	00384c1e500e000a202020202020004b
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16385
disable montype: 1
disable montype: 3
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000 0xe7ffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf8c29000 at 0xb7ee2000
(II) RADEON(0): [drm] Closed DRM master.

```

---

