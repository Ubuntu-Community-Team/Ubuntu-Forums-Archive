---
title: "Black screen whit mouse on startup after instalation"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by TrueAncalagon on 2009-06-18
In the last 3 days I had formated my pc almost 5 times and installed ubuntu and kubuntu whitout a solution to this problem. Ubutu bott is perfect, no errors no messages of problems, but a reach the "desktop" whitr a black screen (working monitor, just black screen) whit a perfect mouse. The mouse work well, I can move it but I can't hace the right click. No pannels, non windows, non background wallpapper, only blackscreen. Formating and reinstalling don't help, I had tried Kubuntu and Ubuntu 9.04, same thing. The cds are perfect. Don't know what to do;

- black screen
- working mouse
- formating and reinstalling don't help
- start whit rescue mode and run xfix or dpkg reconfigure don't help or find errors

---

### Post by dstew on 2009-06-18
What are the specifications of your PC? Processor, memory size, display graphics adapter especially. Are you having this problem with an installed hard disk Ubuntu system, or with the Live CD?

---

### Post by TrueAncalagon on 2009-06-18
I'm working on DuoCore E6400, 4GB RAM, nVidia GTX285. This nvidia work whitout problems on linux, I had tested for almost 3 weeks before formating my HDD. Is this what is called "black screen of death"? From terminal, I had tried to install the nvidia last driver but nothings change at all. The livecd of ubuntu and kubuntu are running whitout problems. But when the instalation is done, I can't get over this screen.

This is the tail of dmesg:
```
[    5.874576] usbhid: v2.6:USB HID core driver
[    9.018509] udev: starting version 141
[    9.130948] parport_pc 00:07: reported by Plug and Play ACPI
[    9.130992] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.158202] Linux agpgart interface v0.103
[    9.160084] cfg80211: Calling CRDA to update world regulatory domain
[    9.362327] iTCO_vendor_support: vendor-support=0
[    9.415315] cfg80211: World regulatory domain updated:
[    9.415318] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.415320] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.415322] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.415324] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.415326] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.415328] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.421448] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.421704] iTCO_wdt: Found a ICH10R TCO device (Version=2, TCOBASE=0x0860)
[    9.421782] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.436779] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.449233] ppdev: user-space parallel port driver
[    9.735312] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[    9.735318] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[    9.735361] usbcore: registered new interface driver rt2500usb
[    9.932674] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.932745] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.965929] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   10.100067] phy1: Selected rate control algorithm 'pid'
[   10.126561] Registered led device: rt73usb-phy1:radio
[   10.126579] Registered led device: rt73usb-phy1:assoc
[   10.126596] Registered led device: rt73usb-phy1:quality
[   10.127039] usbcore: registered new interface driver rt73usb
[   10.220654] lp0: using parport0 (interrupt-driven).
[   10.284346] Adding 979924k swap on /dev/sda6.  Priority:-1 extents:1 across:979924k
[   10.814927] EXT4 FS on sda5, internal journal on sda5:8
[   11.557656] EXT4-fs: barriers enabled
[   11.569268] kjournald2 starting.  Commit interval 5 seconds
[   11.569464] EXT4 FS on sda7, internal journal on sda7:8
[   11.569466] EXT4-fs: delayed allocation enabled
[   11.569467] EXT4-fs: file extents enabled
[   11.569842] EXT4-fs: mballoc enabled
[   11.569845] EXT4-fs: mounted filesystem with ordered data mode.
[   12.065406] type=1505 audit(1245267632.712:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2053
[   12.106373] type=1505 audit(1245267632.753:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2057
[   12.106455] type=1505 audit(1245267632.753:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2057
[   12.106490] type=1505 audit(1245267632.753:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2057
[   12.106522] type=1505 audit(1245267632.753:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2057
[   12.221321] type=1505 audit(1245267632.869:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2062
[   12.221464] type=1505 audit(1245267632.869:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2062
[   12.245770] type=1505 audit(1245267632.893:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2066
[   13.532393] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.532396] Bluetooth: BNEP filters: protocol multicast
[   13.552853] Bridge firewalling registered

```

and my xorg.conf
```
ection "Device"
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
```

---

### Post by dstew on 2009-06-18
It is possible the ext4 file system is responsible. Some programs in some hardware situations will not work properly with ext4. [http://www.h-online.com/open/Possible-data-loss-in-Ext4--/news/112821](http://www.h-online.com/open/Possible-data-loss-in-Ext4--/news/112821)

---

### Post by TrueAncalagon on 2009-06-18
Hm... very strange. I had allways used ext4 from the first time that I had installed ubuntu 9.04....  look at this.. this is the log of X lunched wqhit startx

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux otacon-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 18 21:03:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce GTX 285 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
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
	compiled for 1.6.0, module version = 1.0.0
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) No matches found for this device in /usr/share/xserver-xorg/pci
(==) Registering 'vesa' as fallback
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 98.0
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: GT200 Board - 08910052
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
............
..........
............. I had deleted this part whit only resolution of monitors
...........
..........
(II) VESA(0): Total Memory: 224 64KB banks (14336kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1680x1050" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1680x1050" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(--) VESA(0): Virtual size is 1280x720 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x720"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 14336 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 98.0
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: GT200 Board - 08910052
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): virtual address = 0xb6a1a000,
	physical address = 0xfb000000, size = 14680064
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "it"
(**) AT Translated Set 2 keyboard: xkb_layout: "it"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device HID 062a:0000
(**) HID 062a:0000: always reports core events
(**) HID 062a:0000: Device: "/dev/input/event4"
(II) HID 062a:0000: Found 5 mouse buttons
(II) HID 062a:0000: Found x and y relative axes
(II) HID 062a:0000: Configuring as mouse
(**) HID 062a:0000: YAxisMapping: buttons 4 and 5
(**) HID 062a:0000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 062a:0000" (type: MOUSE)
(**) HID 062a:0000: (accel) keeping acceleration scheme 1
(**) HID 062a:0000: (accel) filter chain progression: 2.00
(**) HID 062a:0000: (accel) filter stage 0: 20.00 ms
(**) HID 062a:0000: (accel) set acceleration profile 0
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) HID 062a:0000: Close
(II) UnloadModule: "evdev"

Backtrace:
0: /usr/bin/X11/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X11/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb80a4400]
3: /usr/lib/xorg/modules//libshadow.so(shadowRemove+0x4e) [0xb7839eee]
4: /usr/lib/xorg/modules//libshadow.so [0xb783a3a4]
5: /usr/bin/X11/X [0x80c6a07]
6: /usr/bin/X11/X [0x811289c]
7: /usr/bin/X11/X [0x811ec9c]
8: /usr/bin/X11/X [0x81254fc]
9: /usr/bin/X11/X [0x80cf45e]
10: /usr/lib/xorg/modules/drivers//vesa_drv.so [0xb79c9bc2]
11: /usr/bin/X11/X [0x80c76db]
12: /usr/bin/X11/X [0x816272b]
13: /usr/bin/X11/X [0x80e1958]
14: /usr/bin/X11/X [0x80cc073]
15: /usr/bin/X11/X [0x814bb35]
16: /usr/bin/X11/X [0x817cd5c]
17: /usr/bin/X11/X [0x814589b]
18: /usr/lib/xorg/modules/extensions//libglx.so [0xb7a1c21a]
19: /usr/bin/X11/X(main+0x44c) [0x807237c]
20: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c79775]
21: /usr/bin/X11/X [0x80717a1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
```

The xorg.conf isn't strange? There is no mention of my nvidia...hm

---

### Post by dstew on 2009-06-18
I don't understand what is happening. It seems it is using the VESA driver. Maybe the VESA driver can't handle your display. It seems to be struggling to come up with appropriate values. What happens if you plug in a different display? I can't help you with the backtrace, I am not sure what it means.

I thought since you recently formatted the drive, maybe that somehow is producing errors. Could there be bad sectors?

---

### Post by TrueAncalagon on 2009-06-19
Incredible, I can't believe it. I had formated the HDD, all the HDD, destroing the partitions too and I had used EXT3. Ubutnu work.  Don't know, I had used EXT4 for almost 6 months whitout problems, untill now.

So, the problem was EXT4... can't believe

---

### Post by dstew on 2009-06-19
Ext4 is generally well behaved with the basic Ubuntu software. However, some third-party software, including some drivers, might cause the problem. Perhaps the graphics driver was to blame. Anyway, ext3 should work fine. The performance advantages of ext4 are small.

---

