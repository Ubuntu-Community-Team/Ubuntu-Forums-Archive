---
title: "Booting Problems 11.04"
date: 2011-05-05
forum: Hardware
---

### Post by Missi0n on 2011-05-05
I have freshly installed Xubuntu 11.04 from a live CD

however when i try to boot up in the new opperating system the screen just flickers and stays **black with no change**, i dont even get a **BIOS or grub** coming up, i dont even know how im mean to get into safe mode with out that. 

can anyone help? :confused:

edit:
it's a Sony Vaio PCG-TR3AP
1Ghz processor
512MB ram

---

### Post by drs305 on 2011-05-05
Do you have a blinking cursor in the upper left part of the screen?

Can you get the Grub2 menu to display during boot by holding down the SHIFT key?

Normally if it is a Grub problem you will get either an error message or be left at the "grub" or "grub rescue" prompt. If you are getting a blinking cursor it could be a video problem. The 'flickers' could be as Grub passes control to the initrd.img or kernel.

Let us know about the above.

---

### Post by Yellow Pasque on 2011-05-05
EDIT: Redundant information, beaten to the punch :P

---

### Post by Missi0n on 2011-05-05
Okay, holding down shift has let it boot into recovery mode, how can i get it to boot properly from there?

---

### Post by drs305 on 2011-05-05
> **Missi0n said:**
> Okay, holding down shift has let it boot into recovery mode, how can i get it to boot properly from there?

If what you had was a blinking cursor in the upper left corner of the screen, select the recovery option to boot in safe graphics mode, then try to install a video driver via System, Administration, Additional Drivers (or however it's done on your OS).

If you don't have a 'safe graphics' option, from the Grub2 menu press 'e' to edit the menuentry. Go to the 'linux' line, remove 'quiet splash', add 'nomodeset', then CTRL-x to boot. Then try to add a driver.

---

### Post by Missi0n on 2011-05-05
okay, im in the recovery console, how to i go about installing the driver? sorry im not fully competent in ubuntu

---

### Post by drs305 on 2011-05-05
> **Missi0n said:**
> okay, im in the recovery console, how to i go about installing the driver? sorry im not fully competent in ubuntu

Have you booted to the Desktop or are you still at the Recovery mode options? 

Unfortunately, I am not familiar enough with Xubuntu to tell you how to install the drivers, and I don't have a current Xubuntu VM.

You can do a search of these forums on how to install a video driver on Xubuntu or perhaps someone will come along to help. I'd start searching, and if you can't get an answer you could start a new thread asking that question. If that turns out not to be the solution you could continue to post in this thread seeking another possible solution.

---

### Post by Missi0n on 2011-05-08
when i load up the additional driver application nothing comes up to install :/ how am i meant to install a screen driver without it coming up? :(

---

### Post by Yellow Pasque on 2011-05-08
The driver comes installed..
Post your /var/log/Xorg.0.log

---

### Post by Missi0n on 2011-05-11
**Sorry it's so long, but here it is**
```

[    31.915] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    31.915] X Protocol Version 11, Revision 0
[    31.915] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    31.915] Current Operating System: Linux josh-PCG-TR3AP-UC 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[    31.915] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=92c84c75-047b-4102-a5cf-418365b9e67c ro quiet splash vt.handoff=7
[    31.915] Build Date: 19 April 2011  03:33:17PM
[    31.915] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    31.915] Current version of pixman: 0.20.2
[    31.915] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    31.915] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.916] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 10 23:46:02 2011
[    31.933] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.933] (==) No Layout section.  Using the first Screen section.
[    31.933] (==) No screen section available. Using defaults.
[    31.933] (**) |-->Screen "Default Screen Section" (0)
[    31.933] (**) |   |-->Monitor "<default monitor>"
[    31.934] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    31.934] (==) Automatically adding devices
[    31.934] (==) Automatically enabling devices
[    31.934] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.934] 	Entry deleted from font path.
[    31.934] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.934] 	Entry deleted from font path.
[    31.934] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.934] 	Entry deleted from font path.
[    31.934] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.934] 	Entry deleted from font path.
[    31.934] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.934] 	Entry deleted from font path.
[    31.934] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    31.934] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.934] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.934] (II) Loader magic: 0x81ffde0
[    31.934] (II) Module ABI versions:
[    31.934] 	X.Org ANSI C Emulation: 0.4
[    31.934] 	X.Org Video Driver: 10.0
[    31.934] 	X.Org XInput driver : 12.3
[    31.935] 	X.Org Server Extension : 5.0
[    31.937] (--) PCI:*(0:0:2:0) 8086:3582:104d:8144 rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
[    31.937] (--) PCI: (0:0:2:1) 8086:3582:104d:8144 rev 2, Mem @ 0xf0000000/134217728, 0xe0080000/524288
[    31.937] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    31.937] (II) LoadModule: "extmod"
[    31.957] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    31.958] (II) Module extmod: vendor="X.Org Foundation"
[    31.958] 	compiled for 1.10.1, module version = 1.0.0
[    31.958] 	Module class: X.Org Server Extension
[    31.958] 	ABI class: X.Org Server Extension, version 5.0
[    31.958] (II) Loading extension MIT-SCREEN-SAVER
[    31.958] (II) Loading extension XFree86-VidModeExtension
[    31.958] (II) Loading extension XFree86-DGA
[    31.958] (II) Loading extension DPMS
[    31.958] (II) Loading extension XVideo
[    31.958] (II) Loading extension XVideo-MotionCompensation
[    31.958] (II) Loading extension X-Resource
[    31.958] (II) LoadModule: "dbe"
[    31.959] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    31.959] (II) Module dbe: vendor="X.Org Foundation"
[    31.959] 	compiled for 1.10.1, module version = 1.0.0
[    31.959] 	Module class: X.Org Server Extension
[    31.959] 	ABI class: X.Org Server Extension, version 5.0
[    31.959] (II) Loading extension DOUBLE-BUFFER
[    31.959] (II) LoadModule: "glx"
[    31.960] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    31.960] (II) Module glx: vendor="X.Org Foundation"
[    31.960] 	compiled for 1.10.1, module version = 1.0.0
[    31.960] 	ABI class: X.Org Server Extension, version 5.0
[    31.960] (==) AIGLX enabled
[    31.960] (II) Loading extension GLX
[    31.960] (II) LoadModule: "record"
[    31.961] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    31.961] (II) Module record: vendor="X.Org Foundation"
[    31.961] 	compiled for 1.10.1, module version = 1.13.0
[    31.961] 	Module class: X.Org Server Extension
[    31.961] 	ABI class: X.Org Server Extension, version 5.0
[    31.961] (II) Loading extension RECORD
[    31.961] (II) LoadModule: "dri"
[    31.962] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    31.962] (II) Module dri: vendor="X.Org Foundation"
[    31.962] 	compiled for 1.10.1, module version = 1.0.0
[    31.962] 	ABI class: X.Org Server Extension, version 5.0
[    31.962] (II) Loading extension XFree86-DRI
[    31.962] (II) LoadModule: "dri2"
[    31.963] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.963] (II) Module dri2: vendor="X.Org Foundation"
[    31.963] 	compiled for 1.10.1, module version = 1.2.0
[    31.963] 	ABI class: X.Org Server Extension, version 5.0
[    31.963] (II) Loading extension DRI2
[    31.963] (==) Matched vesa as autoconfigured driver 0
[    31.963] (==) Matched fbdev as autoconfigured driver 1
[    31.963] (==) Assigned the driver to the xf86ConfigLayout
[    31.963] (II) LoadModule: "vesa"
[    31.963] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.971] (II) Module vesa: vendor="X.Org Foundation"
[    31.971] 	compiled for 1.10.0, module version = 2.3.0
[    31.971] 	Module class: X.Org Video Driver
[    31.971] 	ABI class: X.Org Video Driver, version 10.0
[    31.971] (II) LoadModule: "fbdev"
[    31.972] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.972] (II) Module fbdev: vendor="X.Org Foundation"
[    31.972] 	compiled for 1.10.0, module version = 0.4.2
[    31.972] 	ABI class: X.Org Video Driver, version 10.0
[    31.972] (II) VESA: driver for VESA chipsets: vesa
[    31.972] (II) FBDEV: driver for framebuffer: fbdev
[    31.972] (++) using VT number 7

[    31.972] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.972] (WW) Falling back to old probe method for fbdev
[    31.972] (II) Loading sub module "fbdevhw"
[    31.972] (II) LoadModule: "fbdevhw"
[    31.973] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    31.973] (II) Module fbdevhw: vendor="X.Org Foundation"
[    31.973] 	compiled for 1.10.1, module version = 0.0.2
[    31.973] 	ABI class: X.Org Video Driver, version 10.0
[    31.973] (II) Loading sub module "vbe"
[    31.973] (II) LoadModule: "vbe"
[    31.973] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    31.981] (II) Module vbe: vendor="X.Org Foundation"
[    31.981] 	compiled for 1.10.1, module version = 1.1.0
[    31.981] 	ABI class: X.Org Video Driver, version 10.0
[    31.981] (II) Loading sub module "int10"
[    31.981] (II) LoadModule: "int10"
[    31.982] (II) Loading /usr/lib/xorg/modules/libint10.so
[    31.991] (II) Module int10: vendor="X.Org Foundation"
[    31.992] 	compiled for 1.10.1, module version = 1.0.0
[    31.992] 	ABI class: X.Org Video Driver, version 10.0
[    31.992] (II) VESA(0): initializing int10
[    32.002] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    32.002] (II) VESA(0): VESA BIOS detected
[    32.002] (II) VESA(0): VESA VBE Version 3.0
[    32.002] (II) VESA(0): VESA VBE Total Mem: 3904 kB
[    32.002] (II) VESA(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
[    32.003] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    32.003] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    32.003] (II) VESA(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
[    32.003] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    32.047] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    32.047] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    32.047] (==) VESA(0): RGB weight 888
[    32.047] (==) VESA(0): Default visual is TrueColor
[    32.047] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.047] (II) Loading sub module "ddc"
[    32.047] (II) LoadModule: "ddc"
[    32.047] (II) Module "ddc" already built-in
[    32.055] (II) VESA(0): VESA VBE DDC supported
[    32.055] (II) VESA(0): VESA VBE DDC Level none
[    32.055] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    32.063] (II) VESA(0): VESA VBE DDC read failed
[    32.063] (II) VESA(0): VESA VBE PanelID read successfully
[    32.063] (II) VESA(0): PanelID returned panel resolution 1280x768
[    32.063] (II) VESA(0): Searching for matching VESA mode(s):
[    32.072] Mode: 13c (1920x1440)
[    32.072] 	ModeAttributes: 0x9a
[    32.072] 	WinAAttributes: 0x7
[    32.073] 	WinBAttributes: 0x0
[    32.073] 	WinGranularity: 64
[    32.073] 	WinSize: 64
[    32.073] 	WinASegment: 0xa000
[    32.073] 	WinBSegment: 0x0
[    32.073] 	WinFuncPtr: 0xc0006fae
[    32.073] 	BytesPerScanline: 1920
[    32.073] 	XResolution: 1920
[    32.073] 	YResolution: 1440
[    32.073] 	XCharSize: 8
[    32.073] 	YCharSize: 16
[    32.073] 	NumberOfPlanes: 1
[    32.073] 	BitsPerPixel: 8
[    32.073] 	NumberOfBanks: 1
[    32.073] 	MemoryModel: 4
[    32.073] 	BankSize: 0
[    32.073] 	NumberOfImages: 0
[    32.073] 	RedMaskSize: 0
[    32.073] 	RedFieldPosition: 0
[    32.073] 	GreenMaskSize: 0
[    32.073] 	GreenFieldPosition: 0
[    32.073] 	BlueMaskSize: 0
[    32.073] 	BlueFieldPosition: 0
[    32.073] 	RsvdMaskSize: 0
[    32.073] 	RsvdFieldPosition: 0
[    32.073] 	DirectColorModeInfo: 0
[    32.073] 	PhysBasePtr: 0xe8000000
[    32.073] 	LinBytesPerScanLine: 1920
[    32.073] 	BnkNumberOfImagePages: 0
[    32.073] 	LinNumberOfImagePages: 0
[    32.073] 	LinRedMaskSize: 0
[    32.073] 	LinRedFieldPosition: 0
[    32.073] 	LinGreenMaskSize: 0
[    32.073] 	LinGreenFieldPosition: 0
[    32.073] 	LinBlueMaskSize: 0
[    32.073] 	LinBlueFieldPosition: 0
[    32.073] 	LinRsvdMaskSize: 0
[    32.073] 	LinRsvdFieldPosition: 0
[    32.073] 	MaxPixelClock: 230000000
[    32.074] Mode: 14d (1920x1440)
[    32.074] 	ModeAttributes: 0x9a
[    32.074] 	WinAAttributes: 0x7
[    32.074] 	WinBAttributes: 0x0
[    32.074] 	WinGranularity: 64
[    32.074] 	WinSize: 64
[    32.074] 	WinASegment: 0xa000
[    32.074] 	WinBSegment: 0x0
[    32.074] 	WinFuncPtr: 0xc0006fae
[    32.074] 	BytesPerScanline: 3840
[    32.074] 	XResolution: 1920
[    32.074] 	YResolution: 1440
[    32.074] 	XCharSize: 8
[    32.074] 	YCharSize: 16
[    32.074] 	NumberOfPlanes: 1
[    32.074] 	BitsPerPixel: 16
[    32.074] 	NumberOfBanks: 1
[    32.074] 	MemoryModel: 6
[    32.074] 	BankSize: 0
[    32.074] 	NumberOfImages: 0
[    32.074] 	RedMaskSize: 5
[    32.074] 	RedFieldPosition: 11
[    32.074] 	GreenMaskSize: 6
[    32.074] 	GreenFieldPosition: 5
[    32.074] 	BlueMaskSize: 5
[    32.075] 	BlueFieldPosition: 0
[    32.075] 	RsvdMaskSize: 0
[    32.075] 	RsvdFieldPosition: 0
[    32.075] 	DirectColorModeInfo: 0
[    32.075] 	PhysBasePtr: 0xe8000000
[    32.075] 	LinBytesPerScanLine: 3840
[    32.075] 	BnkNumberOfImagePages: 0
[    32.075] 	LinNumberOfImagePages: 0
[    32.075] 	LinRedMaskSize: 5
[    32.075] 	LinRedFieldPosition: 11
[    32.075] 	LinGreenMaskSize: 6
[    32.075] 	LinGreenFieldPosition: 5
[    32.075] 	LinBlueMaskSize: 5
[    32.075] 	LinBlueFieldPosition: 0
[    32.075] 	LinRsvdMaskSize: 0
[    32.075] 	LinRsvdFieldPosition: 0
[    32.075] 	MaxPixelClock: 230000000
[    32.086] Mode: 15c (1920x1440)
[    32.086] 	ModeAttributes: 0x9a
[    32.086] 	WinAAttributes: 0x7
[    32.086] 	WinBAttributes: 0x0
[    32.086] 	WinGranularity: 64
[    32.086] 	WinSize: 64
[    32.086] 	WinASegment: 0xa000
[    32.086] 	WinBSegment: 0x0
[    32.086] 	WinFuncPtr: 0xc0006fae
[    32.086] 	BytesPerScanline: 7680
[    32.086] 	XResolution: 1920
[    32.086] 	YResolution: 1440
[    32.086] 	XCharSize: 8
[    32.086] 	YCharSize: 16
[    32.086] 	NumberOfPlanes: 1
[    32.086] 	BitsPerPixel: 32
[    32.086] 	NumberOfBanks: 1
[    32.086] 	MemoryModel: 6
[    32.086] 	BankSize: 0
[    32.086] 	NumberOfImages: 0
[    32.086] 	RedMaskSize: 8
[    32.086] 	RedFieldPosition: 16
[    32.086] 	GreenMaskSize: 8
[    32.086] 	GreenFieldPosition: 8
[    32.086] 	BlueMaskSize: 8
[    32.086] 	BlueFieldPosition: 0
[    32.086] 	RsvdMaskSize: 8
[    32.086] 	RsvdFieldPosition: 24
[    32.086] 	DirectColorModeInfo: 0
[    32.086] 	PhysBasePtr: 0xe8000000
[    32.086] 	LinBytesPerScanLine: 7680
[    32.086] 	BnkNumberOfImagePages: 0
[    32.086] 	LinNumberOfImagePages: 0
[    32.086] 	LinRedMaskSize: 8
[    32.086] 	LinRedFieldPosition: 16
[    32.086] 	LinGreenMaskSize: 8
[    32.086] 	LinGreenFieldPosition: 8
[    32.086] 	LinBlueMaskSize: 8
[    32.086] 	LinBlueFieldPosition: 0
[    32.086] 	LinRsvdMaskSize: 8
[    32.086] 	LinRsvdFieldPosition: 24
[    32.086] 	MaxPixelClock: 230000000
[    32.087] Mode: 13a (1600x1200)
[    32.087] 	ModeAttributes: 0x9a
[    32.087] 	WinAAttributes: 0x7
[    32.087] 	WinBAttributes: 0x0
[    32.087] 	WinGranularity: 64
[    32.087] 	WinSize: 64
[    32.087] 	WinASegment: 0xa000
[    32.087] 	WinBSegment: 0x0
[    32.087] 	WinFuncPtr: 0xc0006fae
[    32.087] 	BytesPerScanline: 1600
[    32.087] 	XResolution: 1600
[    32.087] 	YResolution: 1200
[    32.087] 	XCharSize: 8
[    32.087] 	YCharSize: 16
[    32.087] 	NumberOfPlanes: 1
[    32.087] 	BitsPerPixel: 8
[    32.087] 	NumberOfBanks: 1
[    32.087] 	MemoryModel: 4
[    32.087] 	BankSize: 0
[    32.088] 	NumberOfImages: 1
[    32.088] 	RedMaskSize: 0
[    32.088] 	RedFieldPosition: 0
[    32.088] 	GreenMaskSize: 0
[    32.088] 	GreenFieldPosition: 0
[    32.088] 	BlueMaskSize: 0
[    32.088] 	BlueFieldPosition: 0
[    32.088] 	RsvdMaskSize: 0
[    32.088] 	RsvdFieldPosition: 0
[    32.088] 	DirectColorModeInfo: 0
[    32.088] 	PhysBasePtr: 0xe8000000
[    32.088] 	LinBytesPerScanLine: 1600
[    32.088] 	BnkNumberOfImagePages: 1
[    32.088] 	LinNumberOfImagePages: 1
[    32.088] 	LinRedMaskSize: 0
[    32.088] 	LinRedFieldPosition: 0
[    32.088] 	LinGreenMaskSize: 0
[    32.088] 	LinGreenFieldPosition: 0
[    32.088] 	LinBlueMaskSize: 0
[    32.088] 	LinBlueFieldPosition: 0
[    32.088] 	LinRsvdMaskSize: 0
[    32.088] 	LinRsvdFieldPosition: 0
[    32.088] 	MaxPixelClock: 230000000
[    32.089] Mode: 14b (1600x1200)
[    32.089] 	ModeAttributes: 0x9a
[    32.089] 	WinAAttributes: 0x7
[    32.089] 	WinBAttributes: 0x0
[    32.089] 	WinGranularity: 64
[    32.089] 	WinSize: 64
[    32.089] 	WinASegment: 0xa000
[    32.089] 	WinBSegment: 0x0
[    32.089] 	WinFuncPtr: 0xc0006fae
[    32.089] 	BytesPerScanline: 3200
[    32.089] 	XResolution: 1600
[    32.089] 	YResolution: 1200
[    32.089] 	XCharSize: 8
[    32.089] 	YCharSize: 16
[    32.089] 	NumberOfPlanes: 1
[    32.089] 	BitsPerPixel: 16
[    32.089] 	NumberOfBanks: 1
[    32.089] 	MemoryModel: 6
[    32.089] 	BankSize: 0
[    32.089] 	NumberOfImages: 0
[    32.089] 	RedMaskSize: 5
[    32.089] 	RedFieldPosition: 11
[    32.089] 	GreenMaskSize: 6
[    32.089] 	GreenFieldPosition: 5
[    32.089] 	BlueMaskSize: 5
[    32.089] 	BlueFieldPosition: 0
[    32.089] 	RsvdMaskSize: 0
[    32.090] 	RsvdFieldPosition: 0
[    32.090] 	DirectColorModeInfo: 0
[    32.090] 	PhysBasePtr: 0xe8000000
[    32.090] 	LinBytesPerScanLine: 3200
[    32.090] 	BnkNumberOfImagePages: 0
[    32.090] 	LinNumberOfImagePages: 0
[    32.090] 	LinRedMaskSize: 5
[    32.090] 	LinRedFieldPosition: 11
[    32.090] 	LinGreenMaskSize: 6
[    32.090] 	LinGreenFieldPosition: 5
[    32.090] 	LinBlueMaskSize: 5
[    32.090] 	LinBlueFieldPosition: 0
[    32.090] 	LinRsvdMaskSize: 0
[    32.090] 	LinRsvdFieldPosition: 0
[    32.090] 	MaxPixelClock: 230000000
[    32.091] Mode: 15a (1600x1200)
[    32.091] 	ModeAttributes: 0x9a
[    32.091] 	WinAAttributes: 0x7
[    32.091] 	WinBAttributes: 0x0
[    32.091] 	WinGranularity: 64
[    32.091] 	WinSize: 64
[    32.091] 	WinASegment: 0xa000
[    32.091] 	WinBSegment: 0x0
[    32.091] 	WinFuncPtr: 0xc0006fae
[    32.091] 	BytesPerScanline: 6400
[    32.091] 	XResolution: 1600
[    32.091] 	YResolution: 1200
[    32.091] 	XCharSize: 8
[    32.091] 	YCharSize: 16
[    32.091] 	NumberOfPlanes: 1
[    32.091] 	BitsPerPixel: 32
[    32.091] 	NumberOfBanks: 1
[    32.091] 	MemoryModel: 6
[    32.091] 	BankSize: 0
[    32.091] 	NumberOfImages: 0
[    32.091] 	RedMaskSize: 8
[    32.091] 	RedFieldPosition: 16
[    32.091] 	GreenMaskSize: 8
[    32.091] 	GreenFieldPosition: 8
[    32.091] 	BlueMaskSize: 8
[    32.091] 	BlueFieldPosition: 0
[    32.091] 	RsvdMaskSize: 8
[    32.091] 	RsvdFieldPosition: 24
[    32.091] 	DirectColorModeInfo: 0
[    32.091] 	PhysBasePtr: 0xe8000000
[    32.091] 	LinBytesPerScanLine: 6400
[    32.091] 	BnkNumberOfImagePages: 0
[    32.091] 	LinNumberOfImagePages: 0
[    32.092] 	LinRedMaskSize: 8
[    32.104] 	LinRedFieldPosition: 16
[    32.104] 	LinGreenMaskSize: 8
[    32.104] 	LinGreenFieldPosition: 8
[    32.104] 	LinBlueMaskSize: 8
[    32.104] 	LinBlueFieldPosition: 0
[    32.104] 	LinRsvdMaskSize: 8
[    32.105] 	LinRsvdFieldPosition: 24
[    32.105] 	MaxPixelClock: 230000000
[    32.106] Mode: 107 (1280x1024)
[    32.106] 	ModeAttributes: 0x9a
[    32.106] 	WinAAttributes: 0x7
[    32.106] 	WinBAttributes: 0x0
[    32.106] 	WinGranularity: 64
[    32.106] 	WinSize: 64
[    32.106] 	WinASegment: 0xa000
[    32.106] 	WinBSegment: 0x0
[    32.106] 	WinFuncPtr: 0xc0006fae
[    32.106] 	BytesPerScanline: 1280
[    32.106] 	XResolution: 1280
[    32.106] 	YResolution: 1024
[    32.106] 	XCharSize: 8
[    32.106] 	YCharSize: 16
[    32.106] 	NumberOfPlanes: 1
[    32.106] 	BitsPerPixel: 8
[    32.106] 	NumberOfBanks: 1
[    32.106] 	MemoryModel: 4
[    32.106] 	BankSize: 0
[    32.106] 	NumberOfImages: 2
[    32.106] 	RedMaskSize: 0
[    32.106] 	RedFieldPosition: 0
[    32.106] 	GreenMaskSize: 0
[    32.106] 	GreenFieldPosition: 0
[    32.106] 	BlueMaskSize: 0
[    32.106] 	BlueFieldPosition: 0
[    32.106] 	RsvdMaskSize: 0
[    32.106] 	RsvdFieldPosition: 0
[    32.106] 	DirectColorModeInfo: 0
[    32.106] 	PhysBasePtr: 0xe8000000
[    32.106] 	LinBytesPerScanLine: 1280
[    32.106] 	BnkNumberOfImagePages: 2
[    32.106] 	LinNumberOfImagePages: 2
[    32.106] 	LinRedMaskSize: 0
[    32.106] 	LinRedFieldPosition: 0
[    32.106] 	LinGreenMaskSize: 0
[    32.106] 	LinGreenFieldPosition: 0
[    32.106] 	LinBlueMaskSize: 0
[    32.106] 	LinBlueFieldPosition: 0
[    32.106] 	LinRsvdMaskSize: 0
[    32.106] 	LinRsvdFieldPosition: 0
[    32.106] 	MaxPixelClock: 230000000
[    32.107] Mode: 11a (1280x1024)
[    32.107] 	ModeAttributes: 0x9a
[    32.107] 	WinAAttributes: 0x7
[    32.107] 	WinBAttributes: 0x0
[    32.107] 	WinGranularity: 64
[    32.107] 	WinSize: 64
[    32.107] 	WinASegment: 0xa000
[    32.114] 	WinBSegment: 0x0
[    32.114] 	WinFuncPtr: 0xc0006fae
[    32.114] 	BytesPerScanline: 2560
[    32.114] 	XResolution: 1280
[    32.114] 	YResolution: 1024
[    32.114] 	XCharSize: 8
[    32.114] 	YCharSize: 16
[    32.114] 	NumberOfPlanes: 1
[    32.114] 	BitsPerPixel: 16
[    32.114] 	NumberOfBanks: 1
[    32.114] 	MemoryModel: 6
[    32.114] 	BankSize: 0
[    32.114] 	NumberOfImages: 0
[    32.114] 	RedMaskSize: 5
[    32.114] 	RedFieldPosition: 11
[    32.114] 	GreenMaskSize: 6
[    32.114] 	GreenFieldPosition: 5
[    32.114] 	BlueMaskSize: 5
[    32.114] 	BlueFieldPosition: 0
[    32.114] 	RsvdMaskSize: 0
[    32.114] 	RsvdFieldPosition: 0
[    32.114] 	DirectColorModeInfo: 0
[    32.114] 	PhysBasePtr: 0xe8000000
[    32.114] 	LinBytesPerScanLine: 2560
[    32.114] 	BnkNumberOfImagePages: 0
[    32.114] 	LinNumberOfImagePages: 0
[    32.114] 	LinRedMaskSize: 5
[    32.114] 	LinRedFieldPosition: 11
[    32.114] 	LinGreenMaskSize: 6
[    32.114] 	LinGreenFieldPosition: 5
[    32.114] 	LinBlueMaskSize: 5
[    32.114] 	LinBlueFieldPosition: 0
[    32.114] 	LinRsvdMaskSize: 0
[    32.114] 	LinRsvdFieldPosition: 0
[    32.114] 	MaxPixelClock: 230000000
[    32.116] Mode: 11b (1280x1024)
[    32.116] 	ModeAttributes: 0x9a
[    32.116] 	WinAAttributes: 0x7
[    32.116] 	WinBAttributes: 0x0
[    32.116] 	WinGranularity: 64
[    32.116] 	WinSize: 64
[    32.116] 	WinASegment: 0xa000
[    32.116] 	WinBSegment: 0x0
[    32.116] 	WinFuncPtr: 0xc0006fae
[    32.116] 	BytesPerScanline: 5120
[    32.116] 	XResolution: 1280
[    32.116] 	YResolution: 1024
[    32.116] 	XCharSize: 8
[    32.116] 	YCharSize: 16
[    32.116] 	NumberOfPlanes: 1
[    32.116] 	BitsPerPixel: 32
[    32.116] 	NumberOfBanks: 1
[    32.116] 	MemoryModel: 6
[    32.116] 	BankSize: 0
[    32.116] 	NumberOfImages: 0
[    32.116] 	RedMaskSize: 8
[    32.116] 	RedFieldPosition: 16
[    32.116] 	GreenMaskSize: 8
[    32.116] 	GreenFieldPosition: 8
[    32.116] 	BlueMaskSize: 8
[    32.116] 	BlueFieldPosition: 0
[    32.116] 	RsvdMaskSize: 8
[    32.116] 	RsvdFieldPosition: 24
[    32.116] 	DirectColorModeInfo: 0
[    32.116] 	PhysBasePtr: 0xe8000000
[    32.116] 	LinBytesPerScanLine: 5120
[    32.116] 	BnkNumberOfImagePages: 0
[    32.116] 	LinNumberOfImagePages: 0
[    32.116] 	LinRedMaskSize: 8
[    32.116] 	LinRedFieldPosition: 16
[    32.116] 	LinGreenMaskSize: 8
[    32.116] 	LinGreenFieldPosition: 8
[    32.116] 	LinBlueMaskSize: 8
[    32.116] 	LinBlueFieldPosition: 0
[    32.116] 	LinRsvdMaskSize: 8
[    32.116] 	LinRsvdFieldPosition: 24
[    32.116] 	MaxPixelClock: 230000000
[    32.117] Mode: 105 (1024x768)
[    32.117] 	ModeAttributes: 0x9b
[    32.117] 	WinAAttributes: 0x7
[    32.117] 	WinBAttributes: 0x0
[    32.117] 	WinGranularity: 64
[    32.117] 	WinSize: 64
[    32.117] 	WinASegment: 0xa000
[    32.117] 	WinBSegment: 0x0
[    32.117] 	WinFuncPtr: 0xc0006fae
[    32.117] 	BytesPerScanline: 1024
[    32.117] 	XResolution: 1024
[    32.117] 	YResolution: 768
[    32.117] 	XCharSize: 8
[    32.117] 	YCharSize: 16
[    32.118] 	NumberOfPlanes: 1
[    32.118] 	BitsPerPixel: 8
[    32.118] 	NumberOfBanks: 1
[    32.118] 	MemoryModel: 4
[    32.118] 	BankSize: 0
[    32.118] 	NumberOfImages: 4
[    32.118] 	RedMaskSize: 0
[    32.118] 	RedFieldPosition: 0
[    32.118] 	GreenMaskSize: 0
[    32.118] 	GreenFieldPosition: 0
[    32.118] 	BlueMaskSize: 0
[    32.118] 	BlueFieldPosition: 0
[    32.118] 	RsvdMaskSize: 0
[    32.118] 	RsvdFieldPosition: 0
[    32.118] 	DirectColorModeInfo: 0
[    32.118] 	PhysBasePtr: 0xe8000000
[    32.118] 	LinBytesPerScanLine: 1024
[    32.118] 	BnkNumberOfImagePages: 4
[    32.118] 	LinNumberOfImagePages: 4
[    32.118] 	LinRedMaskSize: 0
[    32.118] 	LinRedFieldPosition: 0
[    32.118] 	LinGreenMaskSize: 0
[    32.118] 	LinGreenFieldPosition: 0
[    32.118] 	LinBlueMaskSize: 0
[    32.118] 	LinBlueFieldPosition: 0
[    32.118] 	LinRsvdMaskSize: 0
[    32.118] 	LinRsvdFieldPosition: 0
[    32.118] 	MaxPixelClock: 230000000
[    32.119] Mode: 117 (1024x768)
[    32.119] 	ModeAttributes: 0x9b
[    32.119] 	WinAAttributes: 0x7
[    32.119] 	WinBAttributes: 0x0
[    32.119] 	WinGranularity: 64
[    32.119] 	WinSize: 64
[    32.119] 	WinASegment: 0xa000
[    32.119] 	WinBSegment: 0x0
[    32.119] 	WinFuncPtr: 0xc0006fae
[    32.119] 	BytesPerScanline: 2048
[    32.119] 	XResolution: 1024
[    32.119] 	YResolution: 768
[    32.119] 	XCharSize: 8
[    32.119] 	YCharSize: 16
[    32.119] 	NumberOfPlanes: 1
[    32.119] 	BitsPerPixel: 16
[    32.119] 	NumberOfBanks: 1
[    32.119] 	MemoryModel: 6
[    32.119] 	BankSize: 0
[    32.119] 	NumberOfImages: 1
[    32.119] 	RedMaskSize: 5
[    32.119] 	RedFieldPosition: 11
[    32.119] 	GreenMaskSize: 6
[    32.119] 	GreenFieldPosition: 5
[    32.119] 	BlueMaskSize: 5
[    32.119] 	BlueFieldPosition: 0
[    32.119] 	RsvdMaskSize: 0
[    32.119] 	RsvdFieldPosition: 0
[    32.119] 	DirectColorModeInfo: 0
[    32.128] 	PhysBasePtr: 0xe8000000
[    32.128] 	LinBytesPerScanLine: 2048
[    32.128] 	BnkNumberOfImagePages: 1
[    32.128] 	LinNumberOfImagePages: 1
[    32.128] 	LinRedMaskSize: 5
[    32.128] 	LinRedFieldPosition: 11
[    32.128] 	LinGreenMaskSize: 6
[    32.128] 	LinGreenFieldPosition: 5
[    32.128] 	LinBlueMaskSize: 5
[    32.128] 	LinBlueFieldPosition: 0
[    32.128] 	LinRsvdMaskSize: 0
[    32.128] 	LinRsvdFieldPosition: 0
[    32.128] 	MaxPixelClock: 230000000
[    32.129] *Mode: 118 (1024x768)
[    32.129] 	ModeAttributes: 0x9b
[    32.129] 	WinAAttributes: 0x7
[    32.129] 	WinBAttributes: 0x0
[    32.129] 	WinGranularity: 64
[    32.129] 	WinSize: 64
[    32.129] 	WinASegment: 0xa000
[    32.129] 	WinBSegment: 0x0
[    32.129] 	WinFuncPtr: 0xc0006fae
[    32.130] 	BytesPerScanline: 4096
[    32.130] 	XResolution: 1024
[    32.130] 	YResolution: 768
[    32.130] 	XCharSize: 8
[    32.130] 	YCharSize: 16
[    32.130] 	NumberOfPlanes: 1
[    32.130] 	BitsPerPixel: 32
[    32.130] 	NumberOfBanks: 1
[    32.130] 	MemoryModel: 6
[    32.130] 	BankSize: 0
[    32.130] 	NumberOfImages: 0
[    32.130] 	RedMaskSize: 8
[    32.130] 	RedFieldPosition: 16
[    32.130] 	GreenMaskSize: 8
[    32.130] 	GreenFieldPosition: 8
[    32.130] 	BlueMaskSize: 8
[    32.130] 	BlueFieldPosition: 0
[    32.130] 	RsvdMaskSize: 8
[    32.130] 	RsvdFieldPosition: 24
[    32.130] 	DirectColorModeInfo: 0
[    32.130] 	PhysBasePtr: 0xe8000000
[    32.130] 	LinBytesPerScanLine: 4096
[    32.130] 	BnkNumberOfImagePages: 0
[    32.130] 	LinNumberOfImagePages: 0
[    32.130] 	LinRedMaskSize: 8
[    32.130] 	LinRedFieldPosition: 16
[    32.130] 	LinGreenMaskSize: 8
[    32.130] 	LinGreenFieldPosition: 8
[    32.130] 	LinBlueMaskSize: 8
[    32.130] 	LinBlueFieldPosition: 0
[    32.130] 	LinRsvdMaskSize: 8
[    32.130] 	LinRsvdFieldPosition: 24
[    32.130] 	MaxPixelClock: 230000000
[    32.131] *Mode: 112 (640x480)
[    32.131] 	ModeAttributes: 0x9b
[    32.131] 	WinAAttributes: 0x7
[    32.131] 	WinBAttributes: 0x0
[    32.131] 	WinGranularity: 64
[    32.131] 	WinSize: 64
[    32.131] 	WinASegment: 0xa000
[    32.131] 	WinBSegment: 0x0
[    32.131] 	WinFuncPtr: 0xc0006fae
[    32.131] 	BytesPerScanline: 2560
[    32.131] 	XResolution: 640
[    32.131] 	YResolution: 480
[    32.132] 	XCharSize: 8
[    32.137] 	YCharSize: 16
[    32.137] 	NumberOfPlanes: 1
[    32.137] 	BitsPerPixel: 32
[    32.137] 	NumberOfBanks: 1
[    32.137] 	MemoryModel: 6
[    32.137] 	BankSize: 0
[    32.137] 	NumberOfImages: 2
[    32.137] 	RedMaskSize: 8
[    32.137] 	RedFieldPosition: 16
[    32.137] 	GreenMaskSize: 8
[    32.137] 	GreenFieldPosition: 8
[    32.137] 	BlueMaskSize: 8
[    32.137] 	BlueFieldPosition: 0
[    32.137] 	RsvdMaskSize: 8
[    32.137] 	RsvdFieldPosition: 24
[    32.137] 	DirectColorModeInfo: 0
[    32.137] 	PhysBasePtr: 0xe8000000
[    32.137] 	LinBytesPerScanLine: 2560
[    32.137] 	BnkNumberOfImagePages: 2
[    32.137] 	LinNumberOfImagePages: 2
[    32.137] 	LinRedMaskSize: 8
[    32.137] 	LinRedFieldPosition: 16
[    32.137] 	LinGreenMaskSize: 8
[    32.137] 	LinGreenFieldPosition: 8
[    32.137] 	LinBlueMaskSize: 8
[    32.137] 	LinBlueFieldPosition: 0
[    32.137] 	LinRsvdMaskSize: 8
[    32.137] 	LinRsvdFieldPosition: 24
[    32.137] 	MaxPixelClock: 230000000
[    32.138] Mode: 114 (800x600)
[    32.138] 	ModeAttributes: 0x9b
[    32.138] 	WinAAttributes: 0x7
[    32.138] 	WinBAttributes: 0x0
[    32.138] 	WinGranularity: 64
[    32.138] 	WinSize: 64
[    32.138] 	WinASegment: 0xa000
[    32.138] 	WinBSegment: 0x0
[    32.138] 	WinFuncPtr: 0xc0006fae
[    32.138] 	BytesPerScanline: 1600
[    32.138] 	XResolution: 800
[    32.139] 	YResolution: 600
[    32.139] 	XCharSize: 8
[    32.139] 	YCharSize: 16
[    32.139] 	NumberOfPlanes: 1
[    32.139] 	BitsPerPixel: 16
[    32.139] 	NumberOfBanks: 1
[    32.139] 	MemoryModel: 6
[    32.139] 	BankSize: 0
[    32.139] 	NumberOfImages: 3
[    32.139] 	RedMaskSize: 5
[    32.139] 	RedFieldPosition: 11
[    32.139] 	GreenMaskSize: 6
[    32.139] 	GreenFieldPosition: 5
[    32.139] 	BlueMaskSize: 5
[    32.139] 	BlueFieldPosition: 0
[    32.139] 	RsvdMaskSize: 0
[    32.139] 	RsvdFieldPosition: 0
[    32.139] 	DirectColorModeInfo: 0
[    32.139] 	PhysBasePtr: 0xe8000000
[    32.139] 	LinBytesPerScanLine: 1600
[    32.139] 	BnkNumberOfImagePages: 3
[    32.139] 	LinNumberOfImagePages: 3
[    32.139] 	LinRedMaskSize: 5
[    32.139] 	LinRedFieldPosition: 11
[    32.139] 	LinGreenMaskSize: 6
[    32.139] 	LinGreenFieldPosition: 5
[    32.139] 	LinBlueMaskSize: 5
[    32.139] 	LinBlueFieldPosition: 0
[    32.139] 	LinRsvdMaskSize: 0
[    32.139] 	LinRsvdFieldPosition: 0
[    32.139] 	MaxPixelClock: 230000000
[    32.140] *Mode: 115 (800x600)
[    32.140] 	ModeAttributes: 0x9b
[    32.140] 	WinAAttributes: 0x7
[    32.140] 	WinBAttributes: 0x0
[    32.140] 	WinGranularity: 64
[    32.140] 	WinSize: 64
[    32.141] 	WinASegment: 0xa000
[    32.141] 	WinBSegment: 0x0
[    32.141] 	WinFuncPtr: 0xc0006fae
[    32.141] 	BytesPerScanline: 3200
[    32.141] 	XResolution: 800
[    32.141] 	YResolution: 600
[    32.141] 	XCharSize: 8
[    32.141] 	YCharSize: 16
[    32.141] 	NumberOfPlanes: 1
[    32.141] 	BitsPerPixel: 32
[    32.141] 	NumberOfBanks: 1
[    32.141] 	MemoryModel: 6
[    32.141] 	BankSize: 0
[    32.141] 	NumberOfImages: 1
[    32.141] 	RedMaskSize: 8
[    32.141] 	RedFieldPosition: 16
[    32.141] 	GreenMaskSize: 8
[    32.141] 	GreenFieldPosition: 8
[    32.141] 	BlueMaskSize: 8
[    32.141] 	BlueFieldPosition: 0
[    32.141] 	RsvdMaskSize: 8
[    32.141] 	RsvdFieldPosition: 24
[    32.141] 	DirectColorModeInfo: 0
[    32.141] 	PhysBasePtr: 0xe8000000
[    32.141] 	LinBytesPerScanLine: 3200
[    32.141] 	BnkNumberOfImagePages: 1
[    32.141] 	LinNumberOfImagePages: 1
[    32.141] 	LinRedMaskSize: 8
[    32.141] 	LinRedFieldPosition: 16
[    32.141] 	LinGreenMaskSize: 8
[    32.141] 	LinGreenFieldPosition: 8
[    32.141] 	LinBlueMaskSize: 8
[    32.141] 	LinBlueFieldPosition: 0
[    32.141] 	LinRsvdMaskSize: 8
[    32.141] 	LinRsvdFieldPosition: 24
[    32.141] 	MaxPixelClock: 230000000
[    32.142] Mode: 101 (640x480)
[    32.142] 	ModeAttributes: 0x9b
[    32.142] 	WinAAttributes: 0x7
[    32.142] 	WinBAttributes: 0x0
[    32.142] 	WinGranularity: 64
[    32.142] 	WinSize: 64
[    32.142] 	WinASegment: 0xa000
[    32.142] 	WinBSegment: 0x0
[    32.142] 	WinFuncPtr: 0xc0006fae
[    32.142] 	BytesPerScanline: 640
[    32.142] 	XResolution: 640
[    32.142] 	YResolution: 480
[    32.142] 	XCharSize: 8
[    32.142] 	YCharSize: 16
[    32.142] 	NumberOfPlanes: 1
[    32.142] 	BitsPerPixel: 8
[    32.142] 	NumberOfBanks: 1
[    32.142] 	MemoryModel: 4
[    32.142] 	BankSize: 0
[    32.142] 	NumberOfImages: 11
[    32.142] 	RedMaskSize: 0
[    32.142] 	RedFieldPosition: 0
[    32.142] 	GreenMaskSize: 0
[    32.142] 	GreenFieldPosition: 0
[    32.142] 	BlueMaskSize: 0
[    32.142] 	BlueFieldPosition: 0
[    32.142] 	RsvdMaskSize: 0
[    32.142] 	RsvdFieldPosition: 0
[    32.142] 	DirectColorModeInfo: 0
[    32.142] 	PhysBasePtr: 0xe8000000
[    32.142] 	LinBytesPerScanLine: 640
[    32.142] 	BnkNumberOfImagePages: 11
[    32.142] 	LinNumberOfImagePages: 11
[    32.142] 	LinRedMaskSize: 0
[    32.142] 	LinRedFieldPosition: 0
[    32.142] 	LinGreenMaskSize: 0
[    32.142] 	LinGreenFieldPosition: 0
[    32.142] 	LinBlueMaskSize: 0
[    32.142] 	LinBlueFieldPosition: 0
[    32.142] 	LinRsvdMaskSize: 0
[    32.142] 	LinRsvdFieldPosition: 0
[    32.142] 	MaxPixelClock: 230000000
[    32.143] Mode: 103 (800x600)
[    32.143] 	ModeAttributes: 0x9b
[    32.143] 	WinAAttributes: 0x7
[    32.143] 	WinBAttributes: 0x0
[    32.143] 	WinGranularity: 64
[    32.143] 	WinSize: 64
[    32.143] 	WinASegment: 0xa000
[    32.143] 	WinBSegment: 0x0
[    32.143] 	WinFuncPtr: 0xc0006fae
[    32.143] 	BytesPerScanline: 800
[    32.156] 	XResolution: 800
[    32.156] 	YResolution: 600
[    32.156] 	XCharSize: 8
[    32.156] 	YCharSize: 16
[    32.156] 	NumberOfPlanes: 1
[    32.156] 	BitsPerPixel: 8
[    32.156] 	NumberOfBanks: 1
[    32.156] 	MemoryModel: 4
[    32.156] 	BankSize: 0
[    32.156] 	NumberOfImages: 7
[    32.156] 	RedMaskSize: 0
[    32.156] 	RedFieldPosition: 0
[    32.156] 	GreenMaskSize: 0
[    32.156] 	GreenFieldPosition: 0
[    32.156] 	BlueMaskSize: 0
[    32.156] 	BlueFieldPosition: 0
[    32.156] 	RsvdMaskSize: 0
[    32.156] 	RsvdFieldPosition: 0
[    32.156] 	DirectColorModeInfo: 0
[    32.156] 	PhysBasePtr: 0xe8000000
[    32.156] 	LinBytesPerScanLine: 800
[    32.156] 	BnkNumberOfImagePages: 7
[    32.156] 	LinNumberOfImagePages: 7
[    32.156] 	LinRedMaskSize: 0
[    32.156] 	LinRedFieldPosition: 0
[    32.156] 	LinGreenMaskSize: 0
[    32.156] 	LinGreenFieldPosition: 0
[    32.156] 	LinBlueMaskSize: 0
[    32.156] 	LinBlueFieldPosition: 0
[    32.156] 	LinRsvdMaskSize: 0
[    32.156] 	LinRsvdFieldPosition: 0
[    32.156] 	MaxPixelClock: 230000000
[    32.157] Mode: 111 (640x480)
[    32.157] 	ModeAttributes: 0x9b
[    32.157] 	WinAAttributes: 0x7
[    32.157] 	WinBAttributes: 0x0
[    32.157] 	WinGranularity: 64
[    32.157] 	WinSize: 64
[    32.157] 	WinASegment: 0xa000
[    32.157] 	WinBSegment: 0x0
[    32.157] 	WinFuncPtr: 0xc0006fae
[    32.157] 	BytesPerScanline: 1280
[    32.157] 	XResolution: 640
[    32.157] 	YResolution: 480
[    32.157] 	XCharSize: 8
[    32.158] 	YCharSize: 16
[    32.158] 	NumberOfPlanes: 1
[    32.158] 	BitsPerPixel: 16
[    32.158] 	NumberOfBanks: 1
[    32.158] 	MemoryModel: 6
[    32.158] 	BankSize: 0
[    32.158] 	NumberOfImages: 5
[    32.158] 	RedMaskSize: 5
[    32.158] 	RedFieldPosition: 11
[    32.158] 	GreenMaskSize: 6
[    32.158] 	GreenFieldPosition: 5
[    32.158] 	BlueMaskSize: 5
[    32.158] 	BlueFieldPosition: 0
[    32.158] 	RsvdMaskSize: 0
[    32.158] 	RsvdFieldPosition: 0
[    32.158] 	DirectColorModeInfo: 0
[    32.158] 	PhysBasePtr: 0xe8000000
[    32.158] 	LinBytesPerScanLine: 1280
[    32.158] 	BnkNumberOfImagePages: 5
[    32.158] 	LinNumberOfImagePages: 5
[    32.158] 	LinRedMaskSize: 5
[    32.158] 	LinRedFieldPosition: 11
[    32.158] 	LinGreenMaskSize: 6
[    32.158] 	LinGreenFieldPosition: 5
[    32.158] 	LinBlueMaskSize: 5
[    32.158] 	LinBlueFieldPosition: 0
[    32.158] 	LinRsvdMaskSize: 0
[    32.158] 	LinRsvdFieldPosition: 0
[    32.158] 	MaxPixelClock: 230000000
[    32.158] 
[    32.158] (II) VESA(0): Total Memory: 61 64KB banks (3904kB)
[    32.158] (II) VESA(0): <default monitor>: Using hsync range of 31.50-47.22 kHz
[    32.158] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-59.77 Hz
[    32.158] (WW) VESA(0): Unable to estimate virtual size
[    32.158] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    32.158] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    32.158] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    32.158] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    32.158] (II) VESA(0): <default monitor>: Using hsync range of 31.50-47.22 kHz
[    32.158] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-59.77 Hz
[    32.158] (WW) VESA(0): Unable to estimate virtual size
[    32.158] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    32.158] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    32.158] (**) VESA(0): *Built-in mode "1024x768"
[    32.159] (**) VESA(0): *Built-in mode "800x600"
[    32.159] (==) VESA(0): DPI set to (96, 96)
[    32.159] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    32.173] (**) VESA(0): Using "Shadow Framebuffer"
[    32.174] (II) Loading sub module "shadow"
[    32.174] (II) LoadModule: "shadow"
[    32.174] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    32.174] (II) Module shadow: vendor="X.Org Foundation"
[    32.174] 	compiled for 1.10.1, module version = 1.1.0
[    32.175] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    32.175] (II) Loading sub module "fb"
[    32.175] (II) LoadModule: "fb"
[    32.175] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.175] (II) Module fb: vendor="X.Org Foundation"
[    32.175] 	compiled for 1.10.1, module version = 1.0.0
[    32.175] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    32.175] (II) UnloadModule: "fbdev"
[    32.175] (II) Unloading fbdev
[    32.175] (II) UnloadModule: "fbdevhw"
[    32.175] (II) Unloading fbdevhw
[    32.175] (==) Depth 24 pixmap format is 32 bpp
[    32.175] (II) Loading sub module "int10"
[    32.175] (II) LoadModule: "int10"
[    32.177] (II) Loading /usr/lib/xorg/modules/libint10.so
[    32.177] (II) Module int10: vendor="X.Org Foundation"
[    32.177] 	compiled for 1.10.1, module version = 1.0.0
[    32.177] 	ABI class: X.Org Video Driver, version 10.0
[    32.177] (II) VESA(0): initializing int10
[    32.189] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    32.190] (II) VESA(0): VESA BIOS detected
[    32.190] (II) VESA(0): VESA VBE Version 3.0
[    32.190] (II) VESA(0): VESA VBE Total Mem: 3904 kB
[    32.190] (II) VESA(0): VESA VBE OEM: Intel(r)852MG/852MGE/855MG/855MGE Graphics Chip Accelerated VGA BIOS
[    32.190] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    32.190] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    32.190] (II) VESA(0): VESA VBE OEM Product: Intel(r)852MG/852MGE/855MG/855MGE Graphics Controller
[    32.190] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    32.191] (II) VESA(0): virtual address = 0xb6f18000,
	physical address = 0xe8000000, size = 3997696
[    32.334] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    32.671] (==) VESA(0): Default visual is TrueColor
[    32.671] (==) VESA(0): Backing store disabled
[    32.671] (==) VESA(0): DPMS enabled
[    32.671] (==) RandR enabled
[    32.671] (II) Initializing built-in extension Generic Event Extension
[    32.671] (II) Initializing built-in extension SHAPE
[    32.671] (II) Initializing built-in extension MIT-SHM
[    32.671] (II) Initializing built-in extension XInputExtension
[    32.671] (II) Initializing built-in extension XTEST
[    32.671] (II) Initializing built-in extension BIG-REQUESTS
[    32.671] (II) Initializing built-in extension SYNC
[    32.671] (II) Initializing built-in extension XKEYBOARD
[    32.671] (II) Initializing built-in extension XC-MISC
[    32.671] (II) Initializing built-in extension SECURITY
[    32.671] (II) Initializing built-in extension XINERAMA
[    32.671] (II) Initializing built-in extension XFIXES
[    32.671] (II) Initializing built-in extension RENDER
[    32.671] (II) Initializing built-in extension RANDR
[    32.671] (II) Initializing built-in extension COMPOSITE
[    32.671] (II) Initializing built-in extension DAMAGE
[    32.672] (II) Initializing built-in extension GESTURE
[    32.762] (II) AIGLX: Screen 0 is not DRI2 capable
[    32.762] (II) AIGLX: Screen 0 is not DRI capable
[    32.762] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    32.809] (II) AIGLX: Loaded and initialized swrast
[    32.809] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    32.926] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    33.126] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.126] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.126] (II) LoadModule: "evdev"
[    33.155] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.156] (II) Module evdev: vendor="X.Org Foundation"
[    33.156] 	compiled for 1.10.0.902, module version = 2.6.0
[    33.156] 	Module class: X.Org XInput Driver
[    33.156] 	ABI class: X.Org XInput driver, version 12.3
[    33.156] (II) Using input driver 'evdev' for 'Power Button'
[    33.156] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.157] (**) Power Button: always reports core events
[    33.157] (**) Power Button: Device: "/dev/input/event1"
[    33.157] (--) Power Button: Found keys
[    33.157] (II) Power Button: Configuring as keyboard
[    33.157] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    33.157] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.157] (**) Option "xkb_rules" "evdev"
[    33.157] (**) Option "xkb_model" "pc105"
[    33.157] (**) Option "xkb_layout" "gb"
[    33.202] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    33.218] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    33.218] (II) No input driver/identifier specified (ignoring)
[    33.274] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    33.274] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.274] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.274] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.275] (**) AT Translated Set 2 keyboard: always reports core events
[    33.275] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    33.284] (--) AT Translated Set 2 keyboard: Found keys
[    33.284] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    33.284] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    33.284] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    33.284] (**) Option "xkb_rules" "evdev"
[    33.284] (**) Option "xkb_model" "pc105"
[    33.284] (**) Option "xkb_layout" "gb"
[    34.318] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event5)
[    34.318] (II) No input driver/identifier specified (ignoring)
[    34.389] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
[    34.389] (II) No input driver/identifier specified (ignoring)
[    34.412] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event4)
[    34.412] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    34.412] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[    34.412] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.413] (**) Sony Vaio Keys: always reports core events
[    34.413] (**) Sony Vaio Keys: Device: "/dev/input/event4"
[    34.413] (--) Sony Vaio Keys: Found keys
[    34.413] (II) Sony Vaio Keys: Configuring as keyboard
[    34.413] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/SNY6001:00/input/input4/event4"
[    34.413] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
[    34.413] (**) Option "xkb_rules" "evdev"
[    34.413] (**) Option "xkb_model" "pc105"
[    34.413] (**) Option "xkb_layout" "gb"
[    34.464] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    34.464] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    34.464] (II) Using input driver 'evdev' for 'Video Bus'
[    34.464] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.464] (**) Video Bus: always reports core events
[    34.464] (**) Video Bus: Device: "/dev/input/event3"
[    34.464] (--) Video Bus: Found keys
[    34.464] (II) Video Bus: Configuring as keyboard
[    34.464] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input3/event3"
[    34.464] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    34.464] (**) Option "xkb_rules" "evdev"
[    34.464] (**) Option "xkb_model" "pc105"
[    34.464] (**) Option "xkb_layout" "gb"
[    34.511] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
[    34.512] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    34.512] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    34.512] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    34.512] (**) PS/2 Mouse: always reports core events
[    34.512] (**) PS/2 Mouse: Device: "/dev/input/event6"
[    34.512] (--) PS/2 Mouse: Found 3 mouse buttons
[    34.512] (--) PS/2 Mouse: Found relative axes
[    34.512] (--) PS/2 Mouse: Found x and y relative axes
[    34.512] (II) PS/2 Mouse: Configuring as mouse
[    34.512] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    34.512] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    34.512] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    34.512] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    34.512] (II) PS/2 Mouse: initialized for relative axes.
[    34.513] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    34.513] (**) PS/2 Mouse: (accel) acceleration profile 0
[    34.513] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    34.513] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    34.516] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    34.516] (II) No input driver/identifier specified (ignoring)
[    34.713] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    34.714] (II) No input driver/identifier specified (ignoring)
[    34.717] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
[    34.717] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    34.717] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    34.717] (II) LoadModule: "synaptics"
[    34.718] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    34.718] (II) Module synaptics: vendor="X.Org Foundation"
[    34.718] 	compiled for 1.10.0.902, module version = 1.3.99
[    34.718] 	Module class: X.Org XInput Driver
[    34.718] 	ABI class: X.Org XInput driver, version 12.3
[    34.718] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    34.718] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    34.718] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    34.719] (**) Option "Device" "/dev/input/event7"
[    34.719] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    34.719] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    34.719] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    34.719] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    34.719] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    34.719] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    34.719] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    34.719] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    34.719] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    34.719] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    34.719] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    34.719] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    34.719] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    34.720] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    34.720] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    34.720] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    34.720] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    34.720] (--) AlpsPS/2 ALPS GlidePoint: touchpad found

```

---

### Post by Missi0n on 2011-05-15
can you see any problems in my Xorg.0.log?

---

### Post by drs305 on 2011-05-15
In the past several days it's become apparent there is a problem somewhere in the video transition. Forum member *MAFoElffen* has provided an excellent troubleshooting thread. I wouldn't be surprised if his work will help you:

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by Yellow Pasque on 2011-05-15
Yeah, you have an old intel IGP and Ubuntu has gone with the VESA driver for max compatibility with those chips. There are better solutions, but I don't know what the best course of action is off the top of my head and I'm too drunk to do your googling..

---

### Post by Missi0n on 2011-05-15
> **drs305 said:**
> In the past several days it's become apparent there is a problem somewhere in the video transition. Forum member *MAFoElffen* has provided an excellent troubleshooting thread. I wouldn't be surprised if his work will help you:

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

I've tried for about an hour to make sense of that, i got as far as temporally "editing" the kernel boot line... but it kept asking me for a password, and whenever i entered mine it told me it was incorrect?

> **Temüjin said:**
> Yeah, you have an old intel IGP and Ubuntu has gone with the VESA driver for max compatibility with those chips. There are better solutions, but I don't know what the best course of action is off the top of my head and I'm too drunk to do your googling..

hahaha, thanks
unfortunately i don't have the faintest on how to or what to google with that information, perhaps when you've slept off the alcohol you could throw me some pointers? :)

---

### Post by drs305 on 2011-05-15
> **Missi0n said:**
> I've tried for about an hour to make sense of that, i got as far as temporally "editing" the kernel boot line... but it kept asking me for a password, and whenever i entered mine it told me it was incorrect?


Did you get to the part where you would edit the menuentry's  'linux' line to make the ending look like this? There shouldn't have been any password to at least do this part:
> linux .... ro ** nosplash --verbose text**
Then CTRL-x to boot.

After that, I probably know as much about it as you do.

---

### Post by Missi0n on 2011-05-15
> **drs305 said:**
> Did you get to the part where you would edit the menuentry's  'linux' line to make the ending look like this? There shouldn't have been any password to at least do this part:

Then CTRL-x to boot.

After that, I probably know as much about it as you do.

Yes i got to that part and then gave up

---

### Post by drs305 on 2011-05-15
I understand. If you want to give it one more shot (I promise I'll keep it simple since I got lost in some of it as well):

One of the problems is just grub/linux agreeing to the video mode. If you tell grub at the menu to use one, perhaps you can boot into your normal system (no recovery, no cli, etc):
Change the linux mode to boot at 640x480, which is vga 769. (800x600 is 771, 1024x768 is 773).
Leave off the 'quiet splash vt.handoff=7"
> linux ....  ro vga=769
CTRL-x

If it boots, just open /etc/default/grub and uncomment 640x480 and update-grub. (Or whatever value you want).  

Good luck.

---

### Post by atw208 on 2011-06-29
My buddy just fixed it by going into the bios and turned off "expand screen".

---

### Post by jackbkjack on 2011-07-01
I had the same problem also.But now it solved out.

---

### Post by Missi0n on 2011-07-08
> **jackbkjack said:**
> I had the same problem also.But now it solved out.


how? :confused:

---

### Post by Yellow Pasque on 2011-07-08
Wow, this is one of those threads that I should have gotten back to, but didn't. Well, here's the good link: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

