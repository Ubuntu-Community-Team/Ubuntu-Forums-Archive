---
title: "Intel 965 Graphics not working on Ubuntu 7.04"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by Enyo on 2007-05-27
Hey, 

I can not get X working on my new notebook.

Ubuntu 7.04
Samsung Q45 Notebook
Intel 965 Express Graphics

lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 3

00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f0704000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: f0300000-f03fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f02fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0704400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 0000000088000000-000000008bffffff
	Capabilities: [50] Subsystem: Gammagraphx, Inc. Unknown device 0000

00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18e0 [size=16]
	I/O ports at 18d0 [size=16]
	Capabilities: [70] Power Management version 3

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: medium devsel, IRQ 19
	Memory at 8c000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4353 (rev 15)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

04:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at f0400000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001

04:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09) (prog-if 10 [OHCI])
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f0401000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2

04:09.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at f0401800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

04:09.3 System peripheral: Ricoh Co Ltd Unknown device 0843
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at f0401c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

04:09.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: medium devsel, IRQ 22
	Memory at f0402000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

04:09.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 04)
	Subsystem: Samsung Electronics Co Ltd Unknown device c510
	Flags: medium devsel, IRQ 22
	Memory at f0402400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2


```

xorg.conf

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Intel i965"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i965"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600" "640x480"
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

```

Xorg Log:

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux river 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 27 15:16:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel i965"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
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
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card 144d,c510 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a02 card 144d,c510 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a03 card 144d,c510 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2834 card 144d,c510 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 144d,c510 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 144d,c510 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 144d,c510 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 144d,c510 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 144d,c510 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 144d,c510 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 144d,c510 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 144d,c510 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2828 card 144d,c510 rev 03 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 144d,c510 rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 8086,4222 card 8086,1001 rev 02 class 02,80,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,4353 card 144d,c510 rev 15 class 02,00,00 hdr 00
(II) PCI: 04:09:0: chip 1180,0476 card 3000,0000 rev b4 class 06,07,00 hdr 82
(II) PCI: 04:09:1: chip 1180,0552 card 144d,c510 rev 09 class 0c,00,10 hdr 80
(II) PCI: 04:09:2: chip 1180,0822 card 144d,c510 rev 18 class 08,05,00 hdr 80
(II) PCI: 04:09:3: chip 1180,0843 card 144d,c510 rev 00 class 08,80,00 hdr 80
(II) PCI: 04:09:4: chip 1180,0592 card 144d,c510 rev 09 class 08,80,00 hdr 80
(II) PCI: 04:09:5: chip 1180,0852 card 144d,c510 rev 04 class 08,80,00 hdr 80
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
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf0300000 - 0xf03fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf0200000 - 0xf02fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,8), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf0400000 - 0xf04fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (4:9:0), (4,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x8bffffff (0x4000000) MX[B]
(--) PCI:*(0:2:0) Intel Corporation Mobile Integrated Graphics Controller rev 3, Mem @ 0xf0000000/20, 0xd0000000/28, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile Integrated Graphics Controller rev 3, Mem @ 0xf0100000/20
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
	[0] -1	0	0xf0402400 - 0xf04024ff (0x100) MX[B]
	[1] -1	0	0xf0402000 - 0xf04020ff (0x100) MX[B]
	[2] -1	0	0xf0401c00 - 0xf0401cff (0x100) MX[B]
	[3] -1	0	0xf0401800 - 0xf04018ff (0x100) MX[B]
	[4] -1	0	0xf0401000 - 0xf04017ff (0x800) MX[B]
	[5] -1	0	0xf0200000 - 0xf0203fff (0x4000) MX[B]
	[6] -1	0	0xf0300000 - 0xf0300fff (0x1000) MX[B]
	[7] -1	0	0x8c000000 - 0x8c0000ff (0x100) MX[B]
	[8] -1	0	0xf0704400 - 0xf07047ff (0x400) MX[B]
	[9] -1	0	0xf0500000 - 0xf0503fff (0x4000) MX[B]
	[10] -1	0	0xf0704000 - 0xf07043ff (0x400) MX[B]
	[11] -1	0	0xf0100000 - 0xf01fffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf00fffff (0x100000) MX[B](B)
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[16] -1	0	0x000018d0 - 0x000018df (0x10) IX[B]
	[17] -1	0	0x000018e0 - 0x000018ef (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[23] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0402400 - 0xf04024ff (0x100) MX[B]
	[1] -1	0	0xf0402000 - 0xf04020ff (0x100) MX[B]
	[2] -1	0	0xf0401c00 - 0xf0401cff (0x100) MX[B]
	[3] -1	0	0xf0401800 - 0xf04018ff (0x100) MX[B]
	[4] -1	0	0xf0401000 - 0xf04017ff (0x800) MX[B]
	[5] -1	0	0xf0200000 - 0xf0203fff (0x4000) MX[B]
	[6] -1	0	0xf0300000 - 0xf0300fff (0x1000) MX[B]
	[7] -1	0	0x8c000000 - 0x8c0000ff (0x100) MX[B]
	[8] -1	0	0xf0704400 - 0xf07047ff (0x400) MX[B]
	[9] -1	0	0xf0500000 - 0xf0503fff (0x4000) MX[B]
	[10] -1	0	0xf0704000 - 0xf07043ff (0x400) MX[B]
	[11] -1	0	0xf0100000 - 0xf01fffff (0x100000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf0000000 - 0xf00fffff (0x100000) MX[B](B)
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[16] -1	0	0x000018d0 - 0x000018df (0x10) IX[B]
	[17] -1	0	0x000018e0 - 0x000018ef (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[23] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xf0402400 - 0xf04024ff (0x100) MX[B]
	[5] -1	0	0xf0402000 - 0xf04020ff (0x100) MX[B]
	[6] -1	0	0xf0401c00 - 0xf0401cff (0x100) MX[B]
	[7] -1	0	0xf0401800 - 0xf04018ff (0x100) MX[B]
	[8] -1	0	0xf0401000 - 0xf04017ff (0x800) MX[B]
	[9] -1	0	0xf0200000 - 0xf0203fff (0x4000) MX[B]
	[10] -1	0	0xf0300000 - 0xf0300fff (0x1000) MX[B]
	[11] -1	0	0x8c000000 - 0x8c0000ff (0x100) MX[B]
	[12] -1	0	0xf0704400 - 0xf07047ff (0x400) MX[B]
	[13] -1	0	0xf0500000 - 0xf0503fff (0x4000) MX[B]
	[14] -1	0	0xf0704000 - 0xf07043ff (0x400) MX[B]
	[15] -1	0	0xf0100000 - 0xf01fffff (0x100000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf0000000 - 0xf00fffff (0x100000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[21] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[22] -1	0	0x000018d0 - 0x000018df (0x10) IX[B]
	[23] -1	0	0x000018e0 - 0x000018ef (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000018a0 - 0x000018bf (0x20) IX[B]
	[29] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[30] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[31] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[32] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[33] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
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
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

I have read through a lot of bugs on Launchpad and see that the xserver-xorg-video-i810 is not listed as supporting the i945 (despite the availability of servers from Intel).

Anyone have any suggestions or information?

---

### Post by tgalati4 on 2007-05-27
The Intel i945 and i965 are the VIIV graphics chipsets.  These are two different chipsets that Intel has promoted heavily.  I'm not aware of Linux support on the i965, but I did get Dapper to work on an AOpen (Windows Media Center) i945 box with a dual-core 2.8 GHz processor.  Dapper ran super fast, and no problems with the desktop.  I didn't play with video rendering--I was using the Dapper to troubleshoot the Windows Media installation.  

I can't comment on i965 support.  I imagine that it will be supported, since Intel has been good about chipset support.  Did  you send an email to Samsung support?  What did they say?

Do you have stickers on your machine that say "Designed for Windows Vista"  or perhaps "Locked into Windows Vista"

---

### Post by digitaldoug on 2007-06-13
I have the same message from the x-server with the gma x3100 chip in my HP6500t notebook.
I suspect the ubuntu "i810" driver is too old.  The Intel web site says it was updated in May 2007.
I cannot install 7.04 because X does not work.

---

### Post by DidYouReadGuyDebord on 2007-06-13
I have a desktop version of the 965g. It works with a recent kernel and recent xorg.
Kernel: 2.6.21
Xorg intel driver: 2.0.0.1
Try the vesa mode (only 2D) to see if it works better: type this in a console: **sudo dpkg-reconfigure xserver-xorg**
and choose vesa instead of i810.
You can also download a more recent intel driver, version 2.0.0.4 here, that may work with the newest 3100 chipset:
[http://packages.debian.org/experimental/](http://packages.debian.org/experimental/)
You may also need to install the 2.6.22.RC4 or 2.6.22.RC4.mm1 kernel to get the 3100 to work.

---

### Post by Syke on 2007-06-13
I am also trying to get my X3100 working. Using stock 7.04, I can run the "-intel" driver from the repositories and get stable 2D. If I try to access 3D, like desktop effects, the whole machine freezes.

It sounds like we need version 2 of the "-intel" driver, but that driver is only in Gutsy for now (or compile the source code yourself).

---

### Post by DidYouReadGuyDebord on 2007-06-15
I have version 2 of the driver in debian, and I must say that there are lots of problems with 3D: low resolutions only available in the games I tested, and after exiting 3D games, the resolution of the desktop has become unusable, and X has to be killed.
And this chipset has been on sale for 9 months!!!
We should sue Intel: a corporation that makes so many billions of dollars could afford to hire many more software developers. If you are in the US, please try to initiate a class action!

---

### Post by rrranch on 2007-06-15
I have a brand new HP Pavillion DV9500 with the same graphics. I couldn't install ubuntu or fedora but was able to run the live cd for mepis 64bit

---

### Post by rishiamrit on 2007-07-04
Apparently it works in the next version: Gusty gibbon. I upgraded my Fiesty to Gusty alpha (which isnt recommended as the system can easily crash as it is still in making). And now my video resolution etc ect works fine ... so I guess u gotta wait till October to have Gusty gibbon reseased and use it !

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

---

