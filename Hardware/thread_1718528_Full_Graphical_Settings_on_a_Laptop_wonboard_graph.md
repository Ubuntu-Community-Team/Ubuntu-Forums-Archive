---
title: "Full Graphical Settings on a Laptop w/onboard graphics"
date: 2011-03-31
forum: Hardware
---

### Post by trackmagic on 2011-03-31
I have a Dell Inspirion 800m with onboard graphics. When i try to enable the full visual effects in Ubuntu 10.10 it says it can't do it. A friend of mine says that it is because I have on-board graphics.

I have run 3D games in Windows XP without too many issues so I imagine my laptop would not have issues running all the Ubuntu visuals.

Is there a way to force full visual effects on?

---

### Post by Yellow Pasque on 2011-03-31
It depends on your GPU and whether the driver is loaded correctly. Post /var/log/Xorg.0.log (use code tags or pastebin).

---

### Post by trackmagic on 2011-04-01
This is  big file, but here it is:

[    18.180] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.180] X Protocol Version 11, Revision 0
[    18.180] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    18.180] Current Operating System: Linux ben-Inspiron-700m 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    18.180] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=498e3651-6e12-4c2b-9855-247f34b10f22 ro quiet splash
[    18.180] Build Date: 09 January 2011  12:14:58PM
[    18.180] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.180] Current version of pixman: 0.18.4
[    18.180] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    18.180] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.180] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 31 20:05:07 2011
[    18.256] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.354] (==) No Layout section.  Using the first Screen section.
[    18.354] (==) No screen section available. Using defaults.
[    18.354] (**) |-->Screen "Default Screen Section" (0)
[    18.354] (**) |   |-->Monitor "<default monitor>"
[    18.354] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.354] (==) Automatically adding devices
[    18.354] (==) Automatically enabling devices
[    18.355] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.355] 	Entry deleted from font path.
[    18.355] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.355] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.355] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.355] (II) Loader magic: 0x81f9b00
[    18.355] (II) Module ABI versions:
[    18.355] 	X.Org ANSI C Emulation: 0.4
[    18.355] 	X.Org Video Driver: 8.0
[    18.355] 	X.Org XInput driver : 11.0
[    18.355] 	X.Org Server Extension : 4.0
[    18.356] (--) PCI:*(0:0:2:0) 8086:3582:1028:018d rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
[    18.356] (--) PCI: (0:0:2:1) 8086:3582:1028:018d rev 2, Mem @ 0xf0000000/134217728, 0xe0080000/524288
[    18.356] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.356] (II) LoadModule: "extmod"
[    18.410] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.410] (II) Module extmod: vendor="X.Org Foundation"
[    18.410] 	compiled for 1.9.0, module version = 1.0.0
[    18.410] 	Module class: X.Org Server Extension
[    18.410] 	ABI class: X.Org Server Extension, version 4.0
[    18.410] (II) Loading extension MIT-SCREEN-SAVER
[    18.410] (II) Loading extension XFree86-VidModeExtension
[    18.410] (II) Loading extension XFree86-DGA
[    18.410] (II) Loading extension DPMS
[    18.410] (II) Loading extension XVideo
[    18.410] (II) Loading extension XVideo-MotionCompensation
[    18.410] (II) Loading extension X-Resource
[    18.410] (II) LoadModule: "dbe"
[    18.410] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.410] (II) Module dbe: vendor="X.Org Foundation"
[    18.410] 	compiled for 1.9.0, module version = 1.0.0
[    18.410] 	Module class: X.Org Server Extension
[    18.410] 	ABI class: X.Org Server Extension, version 4.0
[    18.410] (II) Loading extension DOUBLE-BUFFER
[    18.410] (II) LoadModule: "glx"
[    18.410] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.411] (II) Module glx: vendor="X.Org Foundation"
[    18.411] 	compiled for 1.9.0, module version = 1.0.0
[    18.411] 	ABI class: X.Org Server Extension, version 4.0
[    18.411] (==) AIGLX enabled
[    18.411] (II) Loading extension GLX
[    18.411] (II) LoadModule: "record"
[    18.411] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.411] (II) Module record: vendor="X.Org Foundation"
[    18.411] 	compiled for 1.9.0, module version = 1.13.0
[    18.411] 	Module class: X.Org Server Extension
[    18.411] 	ABI class: X.Org Server Extension, version 4.0
[    18.411] (II) Loading extension RECORD
[    18.411] (II) LoadModule: "dri"
[    18.411] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.411] (II) Module dri: vendor="X.Org Foundation"
[    18.411] 	compiled for 1.9.0, module version = 1.0.0
[    18.411] 	ABI class: X.Org Server Extension, version 4.0
[    18.411] (II) Loading extension XFree86-DRI
[    18.411] (II) LoadModule: "dri2"
[    18.411] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.412] (II) Module dri2: vendor="X.Org Foundation"
[    18.412] 	compiled for 1.9.0, module version = 1.2.0
[    18.412] 	ABI class: X.Org Server Extension, version 4.0
[    18.412] (II) Loading extension DRI2
[    18.412] (==) Matched vesa as autoconfigured driver 0
[    18.412] (==) Matched fbdev as autoconfigured driver 1
[    18.412] (==) Assigned the driver to the xf86ConfigLayout
[    18.412] (II) LoadModule: "vesa"
[    18.412] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.412] (II) Module vesa: vendor="X.Org Foundation"
[    18.412] 	compiled for 1.8.99.905, module version = 2.3.0
[    18.412] 	Module class: X.Org Video Driver
[    18.412] 	ABI class: X.Org Video Driver, version 8.0
[    18.412] (II) LoadModule: "fbdev"
[    18.412] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.412] (II) Module fbdev: vendor="X.Org Foundation"
[    18.412] 	compiled for 1.8.99.905, module version = 0.4.2
[    18.412] 	ABI class: X.Org Video Driver, version 8.0
[    18.412] (II) VESA: driver for VESA chipsets: vesa
[    18.412] (II) FBDEV: driver for framebuffer: fbdev
[    18.413] (++) using VT number 7

[    18.413] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    18.413] (WW) Falling back to old probe method for vesa
[    18.413] (II) Loading sub module "fbdevhw"
[    18.413] (II) LoadModule: "fbdevhw"
[    18.413] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.413] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.413] 	compiled for 1.9.0, module version = 0.0.2
[    18.413] 	ABI class: X.Org Video Driver, version 8.0
[    18.413] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    18.413] (II) FBDEV(0): using default device
[    18.413] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.413] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    18.413] (==) FBDEV(0): RGB weight 888
[    18.413] (==) FBDEV(0): Default visual is TrueColor
[    18.413] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.413] (II) FBDEV(0): hardware: inteldrmfb (video memory: 4000kB)
[    18.413] (II) FBDEV(0): checking modes against framebuffer device...
[    18.413] (II) FBDEV(0): checking modes against monitor...
[    18.413] (--) FBDEV(0): Virtual size is 1280x800 (pitch 1280)
[    18.413] (**) FBDEV(0):  Built-in mode "current"
[    18.413] (==) FBDEV(0): DPI set to (96, 96)
[    18.413] (II) Loading sub module "fb"
[    18.413] (II) LoadModule: "fb"
[    18.414] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.414] (II) Module fb: vendor="X.Org Foundation"
[    18.414] 	compiled for 1.9.0, module version = 1.0.0
[    18.414] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.414] (**) FBDEV(0): using shadow framebuffer
[    18.414] (II) Loading sub module "shadow"
[    18.414] (II) LoadModule: "shadow"
[    18.414] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    18.414] (II) Module shadow: vendor="X.Org Foundation"
[    18.414] 	compiled for 1.9.0, module version = 1.1.0
[    18.414] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.414] (==) Depth 24 pixmap format is 32 bpp
[    18.800] (==) FBDEV(0): Backing store disabled
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.800] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.801] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.802] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.803] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    18.806] (==) FBDEV(0): DPMS enabled
[    18.806] (==) RandR enabled
[    18.806] (II) Initializing built-in extension Generic Event Extension
[    18.806] (II) Initializing built-in extension SHAPE
[    18.806] (II) Initializing built-in extension MIT-SHM
[    18.806] (II) Initializing built-in extension XInputExtension
[    18.806] (II) Initializing built-in extension XTEST
[    18.806] (II) Initializing built-in extension BIG-REQUESTS
[    18.806] (II) Initializing built-in extension SYNC
[    18.806] (II) Initializing built-in extension XKEYBOARD
[    18.806] (II) Initializing built-in extension XC-MISC
[    18.806] (II) Initializing built-in extension SECURITY
[    18.806] (II) Initializing built-in extension XINERAMA
[    18.806] (II) Initializing built-in extension XFIXES
[    18.806] (II) Initializing built-in extension RENDER
[    18.806] (II) Initializing built-in extension RANDR
[    18.806] (II) Initializing built-in extension COMPOSITE
[    18.806] (II) Initializing built-in extension DAMAGE
[    18.806] (II) Initializing built-in extension GESTURE
[    18.824] (II) AIGLX: Screen 0 is not DRI2 capable
[    18.824] (II) AIGLX: Screen 0 is not DRI capable
[    18.827] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    18.827] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    18.872] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.886] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.889] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.889] (II) LoadModule: "evdev"
[    18.889] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.889] (II) Module evdev: vendor="X.Org Foundation"
[    18.889] 	compiled for 1.9.0, module version = 2.3.2
[    18.889] 	Module class: X.Org XInput Driver
[    18.889] 	ABI class: X.Org XInput driver, version 11.0
[    18.889] (**) Power Button: always reports core events
[    18.889] (**) Power Button: Device: "/dev/input/event2"
[    18.890] (II) Power Button: Found keys
[    18.890] (II) Power Button: Configuring as keyboard
[    18.890] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.890] (**) Option "xkb_rules" "evdev"
[    18.890] (**) Option "xkb_model" "pc105"
[    18.890] (**) Option "xkb_layout" "us"
[    18.890] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    18.890] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.890] (**) Video Bus: always reports core events
[    18.890] (**) Video Bus: Device: "/dev/input/event4"
[    18.891] (II) Video Bus: Found keys
[    18.891] (II) Video Bus: Configuring as keyboard
[    18.891] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.891] (**) Option "xkb_rules" "evdev"
[    18.891] (**) Option "xkb_model" "pc105"
[    18.891] (**) Option "xkb_layout" "us"
[    18.892] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.892] (II) No input driver/identifier specified (ignoring)
[    18.892] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.892] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.892] (**) Sleep Button: always reports core events
[    18.892] (**) Sleep Button: Device: "/dev/input/event1"
[    18.892] (II) Sleep Button: Found keys
[    18.892] (II) Sleep Button: Configuring as keyboard
[    18.892] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    18.892] (**) Option "xkb_rules" "evdev"
[    18.892] (**) Option "xkb_model" "pc105"
[    18.892] (**) Option "xkb_layout" "us"
[    18.897] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.897] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.897] (**) AT Translated Set 2 keyboard: always reports core events
[    18.897] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.897] (II) AT Translated Set 2 keyboard: Found keys
[    18.897] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.897] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.897] (**) Option "xkb_rules" "evdev"
[    18.897] (**) Option "xkb_model" "pc105"
[    18.897] (**) Option "xkb_layout" "us"
[    18.897] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    18.897] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.897] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.897] (II) LoadModule: "synaptics"
[    18.898] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.898] (II) Module synaptics: vendor="X.Org Foundation"
[    18.898] 	compiled for 1.9.0, module version = 1.2.2
[    18.898] 	Module class: X.Org XInput Driver
[    18.898] 	ABI class: X.Org XInput driver, version 11.0
[    18.898] (II) Synaptics touchpad driver version 1.2.2
[    18.898] (**) Option "Device" "/dev/input/event5"
[    18.898] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    18.898] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    18.898] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.898] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    18.898] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.898] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.898] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.898] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.898] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.898] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    18.898] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.898] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.898] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.899] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.899] (II) No input driver/identifier specified (ignoring)
[  4824.934] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse1)
[  4824.934] (II) No input driver/identifier specified (ignoring)
[  4824.936] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event6)
[  4824.936] (**) Logitech Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[  4824.936] (**) Logitech Optical USB Mouse: always reports core events
[  4824.936] (**) Logitech Optical USB Mouse: Device: "/dev/input/event6"
[  4824.936] (II) Logitech Optical USB Mouse: Found 3 mouse buttons
[  4824.936] (II) Logitech Optical USB Mouse: Found scroll wheel(s)
[  4824.936] (II) Logitech Optical USB Mouse: Found relative axes
[  4824.936] (II) Logitech Optical USB Mouse: Found x and y relative axes
[  4824.936] (II) Logitech Optical USB Mouse: Configuring as mouse
[  4824.936] (**) Logitech Optical USB Mouse: YAxisMapping: buttons 4 and 5
[  4824.936] (**) Logitech Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4824.936] (II) XINPUT: Adding extended input device "Logitech Optical USB Mouse" (type: MOUSE)
[  4824.937] (II) Logitech Optical USB Mouse: initialized for relative axes.

---

### Post by Yellow Pasque on 2011-04-01
Ok, so the wrong driver is loading..
What GPU does this thing have (*because google sure isn't telling me)?
```
lspci
```

---

### Post by trackmagic on 2011-04-01
When I type "lspci" in the terminal it says this:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I assume that it is the Intel one it lists: Intel Corporation 82801 Mobile PCI Bridge

---

### Post by Yellow Pasque on 2011-04-01
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Oh, Ubuntu and other distros stopped shipping the i810 driver, so you're kind of stuck without desktop effects unless you go back to Lucid or find a PPA with the appropriate bits for legacy intel GPU's.

---

### Post by trackmagic on 2011-04-01
Ok, Thanks for looking at this with me anyways.

---

