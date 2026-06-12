---
title: "Enabling evdev breaks my mouse and touchpad, but not my wacom tablet"
date: 2008-09-10
forum: Hardware
---

### Post by Ecna on 2008-09-10
I'm currently using the mouse driver for my Logitech G7, but I'd like to use evdev so I can use my cool extra buttons. When I enable these lines in my xorg:

#	Driver		"evdev"
#        Option          "Protocol"              "evdev"

both my G7 and my Synaptics touchpad stop working.My wacom tablet continues to work fine. Can someone point me in the right direction to start tracking this down? 

cat /proc/bus/input/devices gives this:
```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=1f
B: KEY=37fff ac3027 bf004444 0 0 1 f84 8a37c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=event6 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input10
U: Uniq=
H: Handlers=mouse2 event10 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=056a Product=0016 Version=0403
N: Name="Wacom Graphire4 6x8"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input11
U: Uniq=
H: Handlers=mouse3 event11 
B: EV=1f
B: KEY=1c63 0 70011 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 3000003
B: MSC=1

```

Relevant sections of my xorg.conf that causes the mouse to not work:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0	   "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice     "stylus"	"SendCoreEvents"
    InputDevice     "cursor"	"SendCoreEvents"
    InputDevice     "eraser"	"SendCoreEvents"
    InputDevice	    "pad"
    InputDevice    "Synaptics Touchpad"
EndSection


Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
#	Driver		"evdev"
#        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Device"                "/dev/input/mice"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5 7 8"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection


Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection



```

My Xorg.0.log for the restart with evdev enabled:
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
Current Operating System: Linux Craine-Linux 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 10 10:04:49 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "External"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "pad"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 14c0,0020 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 14c0,0017 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 14c0,0020 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 14c0,0020 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 14c0,0020 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 14c0,0020 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 14c0,0020 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 14c0,0020 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 14c0,0020 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 14c0,0020 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0398 card 14c0,0020 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 14c0,0020 rev 01 class 02,00,00 hdr 00
(II) PCI: 06:00:0: chip 1106,3044 card 14c0,0020 rev c0 class 0c,00,10 hdr 00
(II) PCI: 06:04:0: chip 1524,1412 card 4000,0000 rev 10 class 06,07,00 hdr 82
(II) PCI: 06:04:1: chip 1524,0530 card 14c0,0020 rev 01 class 05,01,00 hdr 80
(II) PCI: 06:04:2: chip 1524,0550 card 14c0,0020 rev 01 class 08,05,01 hdr 80
(II) PCI: 06:04:4: chip 1524,0551 card 14c0,0020 rev 01 class 05,01,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd2100000 - 0xd21fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xd2200000 - 0xd22fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:3), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,10), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00004000 - 0x00004fff (0x1000) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd20fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:4:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 7 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]

(--) PCI:*(1:0:0) nVidia Corporation G70 [GeForce Go 7600] rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24, I/O @ 0x2000/7
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
	[0] -1	0	0xd2001000 - 0xd20010ff (0x100) MX[B]
	[1] -1	0	0xd2001c00 - 0xd2001cff (0x100) MX[B]
	[2] -1	0	0xfabff800 - 0xfabfffff (0x800) MX[B]
	[3] -1	0	0xd2200000 - 0xd2200fff (0x1000) MX[B]
	[4] -1	0	0xd2100000 - 0xd2100fff (0x1000) MX[B]
	[5] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[6] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[7] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ff80 - 0x0000ffff (0x80) IX[B]
	[11] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[12] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd2001800 - 0xd200187f (0x80) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2001000 - 0xd20010ff (0x100) MX[B]
	[1] -1	0	0xd2001c00 - 0xd2001cff (0x100) MX[B]
	[2] -1	0	0xfabff800 - 0xfabfffff (0x800) MX[B]
	[3] -1	0	0xd2200000 - 0xd2200fff (0x1000) MX[B]
	[4] -1	0	0xd2100000 - 0xd2100fff (0x1000) MX[B]
	[5] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[6] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[7] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[8] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ff80 - 0x0000ffff (0x80) IX[B]
	[11] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[12] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[13] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[19] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[20] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[21] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[22] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2001800 - 0xd200187f (0x80) MX[B]
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
	[4] -1	0	0xd2001000 - 0xd20010ff (0x100) MX[B]
	[5] -1	0	0xd2001c00 - 0xd2001cff (0x100) MX[B]
	[6] -1	0	0xfabff800 - 0xfabfffff (0x800) MX[B]
	[7] -1	0	0xd2200000 - 0xd2200fff (0x1000) MX[B]
	[8] -1	0	0xd2100000 - 0xd2100fff (0x1000) MX[B]
	[9] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[10] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd2001800 - 0xd200187f (0x80) MX[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ff80 - 0x0000ffff (0x80) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.7.9-8 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2001000 - 0xd20010ff (0x100) MX[B]
	[5] -1	0	0xd2001c00 - 0xd2001cff (0x100) MX[B]
	[6] -1	0	0xfabff800 - 0xfabfffff (0x800) MX[B]
	[7] -1	0	0xd2200000 - 0xd2200fff (0x1000) MX[B]
	[8] -1	0	0xd2100000 - 0xd2100fff (0x1000) MX[B]
	[9] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[10] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd2001800 - 0xd200187f (0x80) MX[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ff80 - 0x0000ffff (0x80) IX[B]
	[18] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2001000 - 0xd20010ff (0x100) MX[B]
	[5] -1	0	0xd2001c00 - 0xd2001cff (0x100) MX[B]
	[6] -1	0	0xfabff800 - 0xfabfffff (0x800) MX[B]
	[7] -1	0	0xd2200000 - 0xd2200fff (0x1000) MX[B]
	[8] -1	0	0xd2100000 - 0xd2100fff (0x1000) MX[B]
	[9] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[10] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd2001800 - 0xd200187f (0x80) MX[B]
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ffff (0x80) IX[B]
	[21] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "NvAGP" "0"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: NULL, DFP: nvidia-auto-select +0+0; CRT: nvidia-auto-select +0+0, DFP: NULL; CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +640+1200; "
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0, CRT"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): Use of AGP disabled per request
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7600 (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.15.55
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7600 at PCI:1:0:0:
(--) NVIDIA(0):     DELL 2407WFP (CRT-0)
(--) NVIDIA(0):     CPT (DFP-0)
(--) NVIDIA(0): DELL 2407WFP (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): CPT (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): CPT (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT, DFP-0" converted to "CRT-0,
(II) NVIDIA(0):     DFP-0".
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:NULL,DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:NULL"
(II) NVIDIA(0):    
(II) NVIDIA(0):     "CRT:nvidia-auto-select+0+0,DFP:nvidia-auto-select+640+1200"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 2000
(WW) NVIDIA(0): Cannot find size of first mode for DELL 2407WFP (CRT-0);
(WW) NVIDIA(0):     cannot compute DPI from DELL 2407WFP (CRT-0)'s EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2001000 - 0xd20010ff (0x100) MX[B]
	[5] -1	0	0xd2001c00 - 0xd2001cff (0x100) MX[B]
	[6] -1	0	0xfabff800 - 0xfabfffff (0x800) MX[B]
	[7] -1	0	0xd2200000 - 0xd2200fff (0x1000) MX[B]
	[8] -1	0	0xd2100000 - 0xd2100fff (0x1000) MX[B]
	[9] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[10] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[11] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd2001800 - 0xd200187f (0x80) MX[B]
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ffff (0x80) IX[B]
	[21] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "CRT:NULL,DFP:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Generic Keyboard: always reports core events
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
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(EE) ioctl EVIOCGBIT 0 failed: Inappropriate ioctl for device
(EE) Configured Mouse: cannot load bits
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Configured Mouse"
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) stylus: reading USB link
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) cursor: reading USB link
(**) Option "BaudRate" "9600"
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) eraser: reading USB link
(**) Option "BaudRate" "9600"
(**) pad: always reports core events
(**) pad device is /dev/input/wacom
(**) pad is in relative mode
(**) WACOM: suppress value is 2
(**) Option "USB" "on"
(**) pad: reading USB link
(**) Option "BaudRate" "9600"
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 22 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "HorizEdgeScroll" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
(II) evaluating device (pad)
(II) XINPUT: Adding extended input device "pad" (type: Wacom Pad)
(II) evaluating device (eraser)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) evaluating device (cursor)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) evaluating device (stylus)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
pad Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Graphire4 tablet speed=9600 maxX=16704 maxY=12064 maxZ=511 resX=2032 resY=2032  tilt=enabled
(==) Wacom device "pad" top X=0 top Y=0 bottom X=16704 bottom Y=12064
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=16704 bottom Y=12064
(==) Wacom device "cursor" top X=0 top Y=0 bottom X=16704 bottom Y=12064
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=16704 bottom Y=12064
SetClientVersion: 0 9
```

I've tried googling everything I can come up with, but I've come up empty. Even if you don't know the solution, any kind of diagnostic/troubleshooting help would be great. Thanks.

---

### Post by Ecna on 2008-09-10
I tried adding Option "CorePointer" to no avail. Below is the InputDevice section with the CorePointer option that doesn't work:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
#        Driver          "mouse"
	Driver		"evdev"
#        Option          "Protocol"              "evdev"
#        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Device"                "/dev/input/mice"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5 7 8"
	Option		"CorePointer"
EndSection
```

---

