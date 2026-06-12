---
title: "Xorg crashes configuring..."
date: 2010-01-30
forum: Hardware
---

### Post by ownaginatious on 2010-01-30
Hey guys,

I'm actually running Debian (Testing, kernel 2.6.32-trunk-686) , but it's so similar to Ubuntu that I thought maybe someone here could help.

Anyway, I've installed KDE 4.3 from the Debian repositories, but I can't seem to create an Xorg.conf file (one doesn't exist in my X11 folder). The GUI can start, but it's in super-low-resolution-unaccelerated mode right now.

When I try to run the following in the terminal:

```
Xorg -configure
```

I'm given an error about a segmentation fault. Here is the complete log it created:

```


X.Org X Server 1.7.4
Release Date: 2010-01-08
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32-trunk-686 i686 Debian
Current Operating System: Linux NINTENDO-90 2.6.32-trunk-686 #1 SMP Sun Jan 10 06:32:16 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-trunk-686 root=UUID=8f127748-8674-4c6b-96ca-503672ba35a1 ro quiet
Build Date: 20 January 2010  10:52:55PM
xorg-server 2:1.7.4-2 (bgoglin@debian.org) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 30 21:47:59 2010
(II) Loader magic: 0x81e7680
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:8108:1025:0244 Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller rev 7, Mem @ 0xb0080000/524288, 0xc0000000/268435456, 0xb0000000/262144, I/O @ 0x00001800/8
List of video drivers:
	voodoo
	i740
	openchrome
	trident
	siliconmotion
	i128
	chips
	neomagic
	ark
	nv
	tdfx
	sis
	rendition
	mach64
	cirrus
	intel
	s3
	s3virge
	sisusb
	radeon
	radeonhd
	ati
	apm
	tseng
	v4l
	mga
	vmware
	savage
	r128
	fbdev
	vesa
(II) LoadModule: "voodoo"
(II) Loading /usr/lib/xorg/modules/drivers/voodoo_drv.so
(II) Module voodoo: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "i740"
(II) Loading /usr/lib/xorg/modules/drivers/i740_drv.so
(II) Module i740: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.3.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.7.3.902, module version = 0.2.904
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.3.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "siliconmotion"
(II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.7.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "i128"
(II) Loading /usr/lib/xorg/modules/drivers/i128_drv.so
(II) Module i128: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.3.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "chips"
(II) Loading /usr/lib/xorg/modules/drivers/chips_drv.so
(II) Module chips: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.2.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "neomagic"
(II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.2.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "ark"
(II) Loading /usr/lib/xorg/modules/drivers/ark_drv.so
(II) Module ark: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.7.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 2.1.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.4.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.10.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "rendition"
(II) Loading /usr/lib/xorg/modules/drivers/rendition_drv.so
(II) Module rendition: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 4.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 6.8.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "cirrus"
(II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.3.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "s3"
(II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "s3virge"
(II) Loading /usr/lib/xorg/modules/drivers/s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.10.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "sisusb"
(II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.9.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 6.12.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers/radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.7.3.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 6.12.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "apm"
(II) Loading /usr/lib/xorg/modules/drivers/apm_drv.so
(II) Module apm: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.2.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "tseng"
(II) Loading /usr/lib/xorg/modules/drivers/tseng_drv.so
(II) Module tseng: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.1.1
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.4.11
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vmware"
(II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
(II) Module vmware: vendor="X.Org Foundation"
	compiled for 1.7.4, module version = 10.16.9
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 2.3.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 6.8.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.4, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for voodoo
(WW) Falling back to old probe method for i740
(WW) Falling back to old probe method for trident
(WW) Falling back to old probe method for siliconmotion
(WW) Falling back to old probe method for i128
(WW) Falling back to old probe method for neomagic
(WW) Falling back to old probe method for ark
(WW) Falling back to old probe method for sis
(WW) Falling back to old probe method for cirrus
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"
(II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
(II) Module cirrus_laguna: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"
(II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 1.7.3.902, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(WW) Falling back to old probe method for s3
(WW) Falling back to old probe method for s3virge
(WW) Falling back to old probe method for sisusb
(WW) Falling back to old probe method for apm
(WW) Falling back to old probe method for tseng
(WW) Falling back to old probe method for v4l
(II) v4l driver for Video4Linux
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(++) Using config file: "/home/dillon/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
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
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(EE) open /dev/fb0: No such file or directory
(WW) Falling back to old probe method for fbdev

Backtrace:
0: Xorg (xorg_backtrace+0x3b) [0x80e68cb]
1: Xorg (0x8048000+0x60ad5) [0x80a8ad5]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb785c40c]
3: Xorg (InitOutput+0x1da) [0x80b7c6a]
4: Xorg (0x8048000+0x1e79b) [0x806679b]
5: /lib/i686/cmov/libc.so.6 (__libc_start_main+0xe5) [0xb7576b55]
6: Xorg (0x8048000+0x1e541) [0x8066541]
Segmentation fault at address (nil)

Fatal server error:
Caught signal 11 (Segmentation fault). Server aborting


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

If it helps, the computer I'm trying to install this on is an Acer AspireOne with Intel GMA 500 integrated graphics.

Any help would be greatly appreciated.

Thanks!

---

