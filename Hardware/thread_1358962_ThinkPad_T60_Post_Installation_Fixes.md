---
title: "ThinkPad T60 Post Installation Fixes"
date: 2009-12-19
forum: Hardware
---

### Post by kwanbis on 2009-12-19
Hello everybody. I'm trying to migrate for the 5th time to Linux, and leave Windows in the past.

The problem is that there is always something not properly working.

I have Ubuntu 9.10 installed on my ThinkPad T60.

I normally have the T60 connected to a Samsung 2343nwx, and i only use the ThinkPad LCD when i need to leave the house.

The T60 video card is INTEL 945GM based.

The T60 screen is 1400x1050 NOT wide.

The 2343nwx is 2048x1152 wide.

I want Ubuntu to use 1400x1050 resolution when i'm using the T60 LCD, and 2048x1152 when using the 2343nwx.

But the only option i see is 1024x768.

I tried to follow this steps, [http://ubuntuforums.org/showthread.php?p=8441312#post8441312](http://ubuntuforums.org/showthread.php?p=8441312#post8441312) , but i only managed to get the monitor all gray, with a metalic "texture", and my only option was to restart:

1) ~$ cvt 2048 1152
# 2048x1152 59.90 Hz (CVT 2.36M9) hsync: 71.58 kHz; pclk: 197.00 MHz
Modeline "2048x1152_60.00" 197.00 2048 2184 2400 2752 1152 1155 1160 1195 -hsync +vsync

2) ~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
2048x1152 59.9 +
1024x768 60.0*
800x600 60.3 56.2
640x480 60.0
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 287mm x 215mm
1400x1050 60.0 + 85.0 74.8 70.0 60.0 50.0
1280x1024 85.0 75.0 60.0
1280x960 85.0 60.0
1360x768 59.8
1152x864 100.0 85.1 85.0 75.0 75.0 70.0 60.0
1024x768 85.0* 75.0 70.1 60.0
832x624 74.6
800x600 85.1 72.2 75.0 60.3 56.2
640x480 85.0 72.8 75.0 60.0 59.9
720x400 85.0
640x400 85.1
640x350 85.1
0x0 0.0
DVI1 disconnected (normal left inverted right x axis y axis)

3) xrandr --newmode "2048x1152_60.00" 197.00 2048 2184 2400 2752 1152 1155 1160 1195 -hsync +vsync

4) xrandr --addmode VGA1 2048x1152_60.00

5) xrandr --output VGA1 --mode 2048x1152_60.00 --output LVDS1 --off

I get the monitor to go all gray, with a metallic "texture" and i need to reestart.


I also tried to add HorizSync and VertRefresh to the xorg.conf file, following this [http://ubuntuforums.org/showthread.php?p=8302145](http://ubuntuforums.org/showthread.php?p=8302145) but no luck, i only see 1024x768.

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    30-75
        VertRefresh  61.0
	VendorName   "Samsung"
	ModelName    "2343nwx"
EndSection

Anybody with any idea? I don't want to go back to Windows 7, but i have spend the whole saturday trying to make this work, with no luck, and a 23" monitor at 1024x768 looks really awfull.

Thanks.

---

### Post by kwanbis on 2009-12-19
This is my /etc/X11/xorg.conf (still 1024x768)

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "dri2"
	Load  "record"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    30.0 - 75.0
	VertRefresh  56.0 - 61.0
	VendorName   "Samsung"
	ModelName    "2343nwx"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by ibuclaw on 2009-12-20
Where did you get that xorg.conf file from?
I don't think you wrote it yourself - and it probably won't help resolve your issue that it is overly complex / complicated.

The simplest methods are always the best - as I always say. :)

Can you rename your xorg.conf file:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```
and reboot and post the output of the following inside [NOPARSE]```
 
```[/NOPARSE] tags.

```
lspci -v
```
```
cat /var/log/Xorg.0.log
```
```
xrandr -q
```
This will help people see what is happening / going wrong and a produce a relevant fix for it.

Regards
Iain

---

### Post by kwanbis on 2009-12-20
> **tinivole said:**
> Where did you get that xorg.conf file from?
Basically by doing this

```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo /etc/init.d/gdm start ; exit
```

following advise from here: [http://ubuntuforums.org/showthread.php?p=8302145](http://ubuntuforums.org/showthread.php?p=8302145)

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   2048x1152      59.9 +
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        60.0  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 287mm x 215mm
   1400x1050      60.0 +   85.0     74.8     70.0     60.0     50.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0*    75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     60.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
   0x0             0.0  
DVI1 disconnected (normal left inverted right x axis y axis)

```


```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Lenovo Device 2017
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Lenovo Device 201a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ee100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at ee200000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Lenovo Device 201a
	Flags: fast devsel
	Memory at ee180000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Lenovo Device 2010
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: ee000000-ee0fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: 00000000e4000000-00000000e40fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
	I/O behind bridge: 00005000-00006fff
	Memory behind bridge: e8000000-e9ffffff
	Prefetchable memory behind bridge: 00000000e4100000-00000000e41fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=13, sec-latency=0
	I/O behind bridge: 00007000-00008fff
	Memory behind bridge: ea000000-ebffffff
	Prefetchable memory behind bridge: 00000000e4200000-00000000e42fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Lenovo Device 2011
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Lenovo Device 200a
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Lenovo Device 200a
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Lenovo Device 200a
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Lenovo Device 200a
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Lenovo Device 200b
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at ee444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00009000-0000cfff
	Memory behind bridge: e4300000-e7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e3ffffff
	Capabilities: [50] Subsystem: Lenovo Device 2013

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Lenovo Device 2009
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo Device 200c
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Lenovo Device 200d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at ee444400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Lenovo Device 200f
	Flags: medium devsel, IRQ 11
	I/O ports at 18e0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
	Subsystem: Lenovo Device 2001
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 2000 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 2e-c3-c4-ff-ff-58-15-00
	Kernel driver in use: e1000e
	Kernel modules: e1000e

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
	Subsystem: IBM Device 058a
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at edf00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
	Subsystem: Lenovo Device 2012
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: e0000000-e3fff000 (prefetchable)
	Memory window 1: c0000000-c3fff000
	I/O window 0: 00009000-000090ff
	I/O window 1: 00009400-000094ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
```

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntia 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=9988e635-de4c-40c0-bcdb-dbc262d30fdf ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 20 12:29:43 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27a2:17aa:201a Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xee100000/524288, 0xd0000000/268435456, 0xee200000/262144, I/O @ 0x00001800/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output DVI1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): EDID vendor "SAM", prod id 1139
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "2048x1152"x0.0  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): Output VGA1 connected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output DVI1 disconnected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA1 using initial mode 1024x768
(II) intel(0): Output LVDS1 using initial mode 1024x768
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (510, 290) mm
(**) intel(0): DPI set to (50, 67)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 287 x 215
(II) config/hal: Adding input device ThinkPad Extra Buttons
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) ThinkPad Extra Buttons: always reports core events
(**) ThinkPad Extra Buttons: Device: "/dev/input/event10"
(II) ThinkPad Extra Buttons: Found keys
(II) ThinkPad Extra Buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) Logitech USB Receiver: Adding scrollwheel support
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event9"
(II) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
(II) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
(**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
(**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
(II) config/hal: Adding input device Microsoft Comfort Curve Keyboard 2000
(**) Microsoft Comfort Curve Keyboard 2000: always reports core events
(**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event8"
(II) Microsoft Comfort Curve Keyboard 2000: Found keys
(II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event12"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) Logitech USB Receiver: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) config/hal: Adding input device TPPS/2 IBM TrackPoint
(**) TPPS/2 IBM TrackPoint: always reports core events
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event13"
(II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
(II) TPPS/2 IBM TrackPoint: Found x and y relative axes
(II) TPPS/2 IBM TrackPoint: Configuring as mouse
(**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
(**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
(**) TPPS/2 IBM TrackPoint: (accel) keeping acceleration scheme 1
(**) TPPS/2 IBM TrackPoint: (accel) filter chain progression: 2.00
(**) TPPS/2 IBM TrackPoint: (accel) filter stage 0: 20.00 ms
(**) TPPS/2 IBM TrackPoint: (accel) set acceleration profile 0
(II) TPPS/2 IBM TrackPoint: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): Manufacturer: SAM  Model: 473  Serial#: 1297691187
(II) intel(0): Year: 2009  Week: 8
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite  SyncOnGreen
(II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 156.8 MHz   Image Size:  510 x 287 mm
(II) intel(0): h_active: 2048  h_sync: 2096  h_sync_end 2128 h_blank_end 2208 h_border: 0
(II) intel(0): v_active: 1152  v_sync: 1155  v_sync_end 1160 v_blanking: 1185 v_border: 0
(II) intel(0): Ranges: V min: 56 V max: 60 Hz, H min: 30 H max: 81 kHz, PixClock max 160 MHz
(II) intel(0): Monitor name: SyncMaster
(II) intel(0): Serial No: H9NS203704
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004c2d73043332594d
(II) intel(0): 	081301030e331d782aee91a3544c9926
(II) intel(0): 	0f50542308008180814081009500b300
(II) intel(0): 	0101010101013b3d00a0808021403020
(II) intel(0): 	3500fe1f1100001a000000fd00383c1e
(II) intel(0): 	5110000a202020202020000000fc0053
(II) intel(0): 	796e634d61737465720a2020000000ff
(II) intel(0): 	0048394e533230333730340a20200012
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "2048x1152"x59.9  156.75  2048 2096 2128 2208  1152 1155 1160 1185 +hsync -vsync (71.0 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LEN  Model: 4022  Serial#: 0
(II) intel(0): Year: 2007  Week: 15
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.610 redY: 0.330   greenX: 0.300 greenY: 0.530
(II) intel(0): blueX: 0.150 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 640x480@60Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 108.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 90.0 MHz   Image Size:  287 x 215 mm
(II) intel(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) intel(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  LTD141EN9B
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae224000000000
(II) intel(0): 	0f110103801d1578ea6f959c544c8726
(II) intel(0): 	21505421080081800101010101010101
(II) intel(0): 	010101010101302a7820511a10403070
(II) intel(0): 	13001fd71000001825237820511a1040
(II) intel(0): 	307013001fd7100000180000000f0090
(II) intel(0): 	43329043280f010030649055000000fe
(II) intel(0): 	004c5444313431454e39420a20200052
(II) intel(0): EDID vendor "LEN", prod id 16418
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x0.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1400x1050"x60.0  108.00  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1400x1050"x85.0  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) intel(0): Modeline "1400x1050"x50.0   89.97  1400 1448 1560 1688  1050 1051 1054 1066 -hsync -vsync (53.3 kHz)
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "0x0"x0.0    0.00  0 0 0 0  0 0 0 0 (0.0 kHz)
(II) intel(0): EDID for output DVI1
```

**One thing i wonder, could this problem be relate to the internal monitor still stuck at 1024x768? Cause i always tried to fix the external monitor issue first.**

Thanks for the help.

---

### Post by ibuclaw on 2009-12-21
Try something like this for the xorg.conf file.
```

Section "Device"
    Identifier    "LVDS1"
    Driver        "intel"
    BusID         "PCI:0:2:0"
EndSection

Section "Device"
    Identifier    "VGA1"
    Driver        "intel"
    BusID         "PCI:0:2:0"
    Screen        1
EndSection

Section "Monitor"
    Identifier    "Laptop LCD"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "External Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Internal Screen"
    Device        "LVDS1"
    Monitor       "Laptop LCD"
    DefaultDepth  24
    SubSection "Display"
        Depth         24
        Modes         "1400x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier    "External Screen"
    Device        "VGA1"
    Monitor       "External Monitor"
    DefaultDepth  24
    SubSection "Display"
        Depth         24
        Modes         "2048x1152"
    EndSubSection
EndSection

```
Then you should be able to switch between monitors using the designated Fn key combination.

Regards
Iain

---

### Post by kwanbis on 2009-12-21
I would be trying this later on.

In the meantime, i had installed grandr on my box.

Gandr showed me the correct resolutions, but trying to make the external moonitor 2048x1152 resulted on a black screen, with the mouse cursor very small(probably the rightresolution), butunusable.

So i turned of the machine, unplugged the monitor andrestarted, andmy T60 LCD is now at the correct resoltion.

Problem is that if i connect the external monitor the computer is unusable.

I assume grandr modifies the xorg.conf file, and was wondering ifi should delete/rename itandsee what happens.

---

### Post by kwanbis on 2009-12-22
> **tinivole said:**
> Try something like this for the xorg.conf file.
I tried, and ubuntu would boot and it would get a black screen with a white strip.

One thing to clear, is that without connecting to the external monitor, i'm getting 1400x1050.

I also found this 2 links:

[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950#External_display_with_XRandR](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_950#External_display_with_XRandR)

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

which i'm trying to interpret, and do.

---

