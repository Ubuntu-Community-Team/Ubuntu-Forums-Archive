---
title: "Black screen after white glowing ubuntu symbol"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by stalf on 2009-10-30
It happened through 3 different ways:

1. Boot from live cd, selected install. I got a glowing ubuntu symbol, then lots of text (with no apparent error) and then black screen.

2. Boot from live cd, selected test ubuntu. Same glowing symbol, same black screen.

3. Then I switched to safe graphics mode, through which I got to install it. After installation, the grub showed up and the boot went ok. So I decided to enable compiz effects, which I couldn't. After some thinking, I found out it was happening because of the safe mode, so I changed the name of the /etc/X11/xorg.conf file hoping it would rebuild it with my card configuration and rebooted. Got to the grub, selected Ubuntu, got the glowing symbol and then, black screen again.

The black screen seems to be functional, as when I press (not hold) the power button on the laptop it behaves as it should, turning off the computer. On situations 1 and 2, it even got back to the glowing white symbol and asked me to remove the live cd from the tray.

Just don't know what else to do... When I had the chance to boot (before changing the name of the xorg.conf), I noticed I had no restricted drivers available.

Do you guys have any clue on how could I solve it?

P.S.: 8.10 works very well, recognizing my hardware on the live cd. I haven't tested 9.04.

---

### Post by shadowlands on 2009-10-30
I just loaded up an  update and now my ubuntu symbol is white and my mouse froze.

---

### Post by raven01 on 2009-10-31
seems like this has been a big issue lately. im having it as well. i hope they fix this soon

---

### Post by stalf on 2009-10-31
Has anyone came up with a solution?
I tried adding vga=791 to the ubuntu boot option on the grub, but didn't work, and also tried changing my xorg.conf file to use intel as the video driver, which also didn't work..

Any suggestions?

---

### Post by mikerz343 on 2009-11-01
Same problem here. I'm on a Dell Studio 15 laptop.

---

### Post by stalf on 2009-11-02
So, hasn't anyone came up with a solution?

---

### Post by jwang on 2009-11-02
what's in Xorg.0.log?

If it's Intel graphic card, you could try to disable KMS, see below the link:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

This enables me to have correct resolution on my laptop.

---

### Post by ryansinn on 2009-11-03
I have the same problem with attempting to install 9.10 -- I had the issue with Beta, RC and now the actual Release.

I'm running an NVIDIA GeForce 9600GT

---

### Post by raven01 on 2009-11-03
dont feel to bad. its the same issue i have. i just got my new netbook and havent tried it on here yet.. but on the desktop my video mode is not supported or something. i think the generic video driver is not loading properly and it cant see the card. unfortunatly no one has a solid fix for this yet. i hope a new iso will come out soon

---

### Post by stalf on 2009-11-07
> **jwang said:**
> what's in Xorg.0.log?

If it's Intel graphic card, you could try to disable KMS, see below the link:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

This enables me to have correct resolution on my laptop.

Here is what was on Xorg.0.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux scrooge 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=ec2aa5e4-d985-4e96-9277-f0998cf2403c ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 30 22:43:30 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27a2:103c:30b2 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd4200000/524288, 0xc0000000/268435456, 0xd4300000/262144, I/O @ 0x00001800/8
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
(EE) open /dev/fb0: No such file or directory
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
(II) intel(0): Output TV1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output TV1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output TV1 disconnected
(WW) intel(0): Unable to find initial modes
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) intel(0): No modes.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by Earl_Maroon on 2009-11-07
Is the Ubuntu logo meant to glow? The logo I get is completely static. Boot is also quite slow compared to what I was expecting/got with 9.04.

---

### Post by afdoughty on 2009-11-07
Me too. I had the previous vertion running very smooth for many months on my Dell Laptop X200. 

Upgraded and now the "Black screen of Death" after the glowing ubuntu symbol happens randomly. Some times boot up is fine, sometimes not. 

Have noticed that the screen resolution of the boot up screen is not matched to screen and there is a lot of flickering of the screen.

Can someone let me know if a solution has been found or point to the "downgrade" process I should follow to get back to the stable version I had for this laptop before.

Thanks

---

### Post by stalf on 2009-11-11
So, has anyone found a way through this?

---

### Post by douginmaryland on 2009-11-14
This looks promising but I haven't tried it yet.
[http://ubuntuforums.org/showthread.php?t=1311148](http://ubuntuforums.org/showthread.php?t=1311148)

---

### Post by ntom-taylor on 2009-11-28
> 
1. Boot from live cd, selected install. I got a glowing ubuntu symbol, then lots of text (with no apparent error) and then black screen.

2. Boot from live cd, selected test ubuntu. Same glowing symbol, same black screen.


Same for me, please fix . .
This is worse than the vista release... at least that could be installed ! 
Can't release 9.10 only to have loads of people on the forums about black screen during installation.

---

### Post by Dearhell on 2009-11-29
I also have a NVIDIA 9600 GT, when I boot into the cd and select the install option, the screen goes black and nothing happens.

I fixed it selecting "save graphics mode" pressing f4 on the initial installation screen.

---

### Post by afdoughty on 2009-12-15
Just installed Linux Mint via Unetbootin on a USB stick. Much better install than Ubuntu Jaunty. The wireless worked straight off, no font or screen smearing issues, no tweaks of drivers. Almost a completely perfect install first time. Dropbox for linux also perfect install . Very impressed and recommend Linux Mint for all Dell X200 users out there. 

A

---

### Post by gamerteck on 2009-12-15
I was able to fix the exact same issue with my Nvidia 6200 by following the instructions here
> [http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553)

---

