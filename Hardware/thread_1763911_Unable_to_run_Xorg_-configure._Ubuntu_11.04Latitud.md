---
title: "Unable to run Xorg -configure. Ubuntu 11.04/Latitude E6520/Intel HD Log included."
date: 2011-05-21
forum: Hardware
---

### Post by genezkool323 on 2011-05-21
Hello,

I just received a laptop for work where I will be doing some Ruby coding. It is a fairly recent Dell laptop, the Latitude E6520. Now Ubuntu 11.04 installed incredibly well onto it. Everything is running wonderfully. All wifi needed was a broadcom install.

My one issue is that I will be docking and undocking my laptop at work. The docking works fairly well with a few bugs. Although X or GDM (I'm not too sure about these things. Not as linux strong as I'd like to be) seems to pick up the native resolutions there are some times when after undocking or attempting to solely use the external monitor where the screen just bugs out and flickers and the only way I can reclaim the system is by doing an Alt + Ctrl + F1 and restarting the server with "sudo service gdm start/stop".

I figured that I might have to do some adjustments to my xorg.conf Lo and behold, I do not have one! After shutting down X I tried to do a "sudo Xorg -configure" to attempt to create a barebones conf file because I have NO idea how to make one from scratch. This is when I am given the "Number of created screens does not match number of detected devices. Configuration failed." (full code given below) Now I figured maybe I set up Ubuntu wrong, so I went on to the LiveUSB and found the same problem from that fresh image so I guess this is some incompatibility with my video controller.

After doing some research I have found that I have a Sandybridge chip with integrated graphics. From what I understand this is a fairly recent chip and the drivers are not perfect. In any case does anybody know if there is some way I can get a nice working xorg.conf file so that hopefully my docking trouble may get fixed?

Thanks! Look forward to being on the forums.

```
[  3063.463] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  3063.477] X Protocol Version 11, Revision 0
[  3063.482] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  3063.484] Current Operating System: Linux odutta-Latitude-E6520 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[  3063.485] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b19348b5-3cb5-4407-9112-14cb11d89151 ro quiet splash vt.handoff=7
[  3063.487] Build Date: 19 April 2011  03:33:17PM
[  3063.488] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[  3063.489] Current version of pixman: 0.20.2
[  3063.490] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3063.492] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3063.496] (++) Log file: "fail", Time: Fri May 20 22:22:23 2011
[  3063.497] (II) Loader magic: 0x81ffde0
[  3063.497] (II) Module ABI versions:
[  3063.497] 	X.Org ANSI C Emulation: 0.4
[  3063.497] 	X.Org Video Driver: 10.0
[  3063.497] 	X.Org XInput driver : 12.3
[  3063.497] 	X.Org Server Extension : 5.0
[  3063.497] (--) PCI:*(0:0:2:0) 8086:0126:1028:0494 rev 9, Mem @ 0xe1400000/4194304, 0xd0000000/268435456, I/O @ 0x00004000/64
[  3063.499] List of video drivers:
[  3063.500] 	vmware
[  3063.501] 	s3virge
[  3063.502] 	sisusb
[  3063.503] 	intel
[  3063.504] 	ati
[  3063.505] 	rendition
[  3063.506] 	qxl
[  3063.507] 	trident
[  3063.508] 	chips
[  3063.509] 	tdfx
[  3063.510] 	nouveau
[  3063.510] 	siliconmotion
[  3063.511] 	apm
[  3063.512] 	sis
[  3063.513] 	mga
[  3063.514] 	openchrome
[  3063.514] 	cirrus
[  3063.515] 	neomagic
[  3063.516] 	tseng
[  3063.516] 	radeon
[  3063.517] 	ark
[  3063.518] 	vmwlegacy
[  3063.518] 	r128
[  3063.519] 	ztv
[  3063.520] 	voodoo
[  3063.520] 	mach64
[  3063.521] 	savage
[  3063.521] 	i740
[  3063.522] 	geode
[  3063.522] 	i128
[  3063.523] 	s3
[  3063.523] 	fbdev
[  3063.523] 	vesa
[  3063.524] (II) LoadModule: "vmware"
[  3063.524] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[  3063.525] (II) Module vmware: vendor="X.Org Foundation"
[  3063.525] 	compiled for 1.10.0, module version = 11.0.3
[  3063.526] 	Module class: X.Org Video Driver
[  3063.526] 	ABI class: X.Org Video Driver, version 10.0
[  3063.526] (II) LoadModule: "vmwgfx"
[  3063.526] (WW) Warning, couldn't open module vmwgfx
[  3063.526] (II) UnloadModule: "vmwgfx"
[  3063.526] (II) Unloading vmwgfx
[  3063.527] (EE) Failed to load module "vmwgfx" (module does not exist, 0)
[  3063.527] (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
[  3063.527] (II) vmware: Using vmwlegacy driver everything is fine.
[  3063.528] (II) LoadModule: "vmwlegacy"
[  3063.528] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[  3063.528] (II) Module vmwlegacy: vendor="X.Org Foundation"
[  3063.529] 	compiled for 1.10.0, module version = 11.0.3
[  3063.529] 	Module class: X.Org Video Driver
[  3063.529] 	ABI class: X.Org Video Driver, version 10.0
[  3063.529] (II) LoadModule: "s3virge"
[  3063.529] (II) Loading /usr/lib/xorg/modules/drivers/s3virge_drv.so
[  3063.529] (II) Module s3virge: vendor="X.Org Foundation"
[  3063.530] 	compiled for 1.10.0, module version = 1.10.4
[  3063.530] 	Module class: X.Org Video Driver
[  3063.530] 	ABI class: X.Org Video Driver, version 10.0
[  3063.530] (II) LoadModule: "sisusb"
[  3063.530] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[  3063.531] (II) Module sisusb: vendor="X.Org Foundation"
[  3063.531] 	compiled for 1.10.0, module version = 0.9.4
[  3063.531] 	Module class: X.Org Video Driver
[  3063.531] 	ABI class: X.Org Video Driver, version 10.0
[  3063.531] (II) LoadModule: "intel"
[  3063.531] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  3063.532] (II) Module intel: vendor="X.Org Foundation"
[  3063.532] 	compiled for 1.10.1, module version = 2.14.0
[  3063.533] 	Module class: X.Org Video Driver
[  3063.533] 	ABI class: X.Org Video Driver, version 10.0
[  3063.533] (II) LoadModule: "ati"
[  3063.533] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  3063.533] (II) Module ati: vendor="X.Org Foundation"
[  3063.534] 	compiled for 1.10.0, module version = 6.14.0
[  3063.534] 	Module class: X.Org Video Driver
[  3063.534] 	ABI class: X.Org Video Driver, version 10.0
[  3063.534] (II) LoadModule: "rendition"
[  3063.534] (II) Loading /usr/lib/xorg/modules/drivers/rendition_drv.so
[  3063.535] (II) Module rendition: vendor="X.Org Foundation"
[  3063.535] 	compiled for 1.10.0, module version = 4.2.4
[  3063.536] 	Module class: X.Org Video Driver
[  3063.536] 	ABI class: X.Org Video Driver, version 10.0
[  3063.536] (II) LoadModule: "qxl"
[  3063.536] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[  3063.536] (II) Module qxl: vendor="X.Org Foundation"
[  3063.537] 	compiled for 1.10.0, module version = 0.0.0
[  3063.537] 	Module class: X.Org Video Driver
[  3063.537] 	ABI class: X.Org Video Driver, version 10.0
[  3063.537] (II) LoadModule: "trident"
[  3063.537] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[  3063.538] (II) Module trident: vendor="X.Org Foundation"
[  3063.538] 	compiled for 1.10.0, module version = 1.3.4
[  3063.539] 	Module class: X.Org Video Driver
[  3063.539] 	ABI class: X.Org Video Driver, version 10.0
[  3063.539] (II) LoadModule: "chips"
[  3063.539] (II) Loading /usr/lib/xorg/modules/drivers/chips_drv.so
[  3063.540] (II) Module chips: vendor="X.Org Foundation"
[  3063.540] 	compiled for 1.10.0, module version = 1.2.3
[  3063.541] 	Module class: X.Org Video Driver
[  3063.541] 	ABI class: X.Org Video Driver, version 10.0
[  3063.541] (II) LoadModule: "tdfx"
[  3063.541] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[  3063.541] (II) Module tdfx: vendor="X.Org Foundation"
[  3063.542] 	compiled for 1.10.0, module version = 1.4.3
[  3063.543] 	Module class: X.Org Video Driver
[  3063.543] 	ABI class: X.Org Video Driver, version 10.0
[  3063.543] (II) LoadModule: "nouveau"
[  3063.543] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  3063.543] (II) Module nouveau: vendor="X.Org Foundation"
[  3063.544] 	compiled for 1.10.0, module version = 0.0.16
[  3063.545] 	Module class: X.Org Video Driver
[  3063.545] 	ABI class: X.Org Video Driver, version 10.0
[  3063.545] (II) LoadModule: "siliconmotion"
[  3063.545] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[  3063.545] (II) Module siliconmotion: vendor="X.Org Foundation"
[  3063.546] 	compiled for 1.10.0, module version = 1.7.4
[  3063.547] 	Module class: X.Org Video Driver
[  3063.547] 	ABI class: X.Org Video Driver, version 10.0
[  3063.547] (II) LoadModule: "apm"
[  3063.547] (II) Loading /usr/lib/xorg/modules/drivers/apm_drv.so
[  3063.548] (II) Module apm: vendor="X.Org Foundation"
[  3063.548] 	compiled for 1.10.0, module version = 1.2.3
[  3063.549] 	Module class: X.Org Video Driver
[  3063.549] 	ABI class: X.Org Video Driver, version 10.0
[  3063.549] (II) LoadModule: "sis"
[  3063.549] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[  3063.550] (II) Module sis: vendor="X.Org Foundation"
[  3063.550] 	compiled for 1.10.0, module version = 0.10.3
[  3063.551] 	Module class: X.Org Video Driver
[  3063.551] 	ABI class: X.Org Video Driver, version 10.0
[  3063.551] (II) LoadModule: "mga"
[  3063.551] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[  3063.552] (II) Module mga: vendor="X.Org Foundation"
[  3063.553] 	compiled for 1.10.0, module version = 1.4.13
[  3063.553] 	Module class: X.Org Video Driver
[  3063.553] 	ABI class: X.Org Video Driver, version 10.0
[  3063.553] (II) LoadModule: "openchrome"
[  3063.553] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[  3063.554] (II) Module openchrome: vendor="http://openchrome.org/"
[  3063.555] 	compiled for 1.10.0, module version = 0.2.904
[  3063.555] 	Module class: X.Org Video Driver
[  3063.555] 	ABI class: X.Org Video Driver, version 10.0
[  3063.555] (II) LoadModule: "cirrus"
[  3063.556] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[  3063.556] (II) Module cirrus: vendor="X.Org Foundation"
[  3063.557] 	compiled for 1.10.0, module version = 1.3.2
[  3063.558] 	Module class: X.Org Video Driver
[  3063.558] 	ABI class: X.Org Video Driver, version 10.0
[  3063.558] (II) LoadModule: "neomagic"
[  3063.558] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[  3063.558] (II) Module neomagic: vendor="X.Org Foundation"
[  3063.559] 	compiled for 1.10.0, module version = 1.2.5
[  3063.560] 	Module class: X.Org Video Driver
[  3063.560] 	ABI class: X.Org Video Driver, version 10.0
[  3063.560] (II) LoadModule: "tseng"
[  3063.560] (II) Loading /usr/lib/xorg/modules/drivers/tseng_drv.so
[  3063.560] (II) Module tseng: vendor="X.Org Foundation"
[  3063.561] 	compiled for 1.10.0, module version = 1.1.0
[  3063.562] 	Module class: X.Org Video Driver
[  3063.562] 	ABI class: X.Org Video Driver, version 10.0
[  3063.562] (II) LoadModule: "radeon"
[  3063.562] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  3063.563] (II) Module radeon: vendor="X.Org Foundation"
[  3063.563] 	compiled for 1.10.0, module version = 6.14.0
[  3063.564] 	Module class: X.Org Video Driver
[  3063.564] 	ABI class: X.Org Video Driver, version 10.0
[  3063.564] (II) LoadModule: "ark"
[  3063.564] (II) Loading /usr/lib/xorg/modules/drivers/ark_drv.so
[  3063.565] (II) Module ark: vendor="X.Org Foundation"
[  3063.565] 	compiled for 1.10.0, module version = 0.7.3
[  3063.566] 	Module class: X.Org Video Driver
[  3063.566] 	ABI class: X.Org Video Driver, version 10.0
[  3063.566] (II) LoadModule: "vmwlegacy"
[  3063.566] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[  3063.567] (II) Module vmwlegacy: vendor="X.Org Foundation"
[  3063.568] 	compiled for 1.10.0, module version = 11.0.3
[  3063.568] 	Module class: X.Org Video Driver
[  3063.568] 	ABI class: X.Org Video Driver, version 10.0
[  3063.568] (II) UnloadModule: "vmwlegacy"
[  3063.568] (II) Unloading vmwlegacy
[  3063.569] (II) Failed to load module "vmwlegacy" (already loaded, -1074807912)
[  3063.570] (II) LoadModule: "r128"
[  3063.570] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[  3063.570] (II) Module r128: vendor="X.Org Foundation"
[  3063.571] 	compiled for 1.10.0, module version = 6.8.1
[  3063.572] 	Module class: X.Org Video Driver
[  3063.572] 	ABI class: X.Org Video Driver, version 10.0
[  3063.572] (II) LoadModule: "ztv"
[  3063.572] (II) Loading /usr/lib/xorg/modules/drivers/ztv_drv.so
[  3063.573] (II) Module ztv: vendor="X.Org Foundation"
[  3063.573] 	compiled for 1.10.0, module version = 0.0.1
[  3063.574] 	ABI class: X.Org Video Driver, version 10.0
[  3063.574] (II) LoadModule: "voodoo"
[  3063.574] (II) Loading /usr/lib/xorg/modules/drivers/voodoo_drv.so
[  3063.575] (II) Module voodoo: vendor="X.Org Foundation"
[  3063.575] 	compiled for 1.10.0, module version = 1.1.0
[  3063.576] 	Module class: X.Org Video Driver
[  3063.576] 	ABI class: X.Org Video Driver, version 10.0
[  3063.576] (II) LoadModule: "mach64"
[  3063.576] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[  3063.577] (II) Module mach64: vendor="X.Org Foundation"
[  3063.577] 	compiled for 1.10.0, module version = 6.8.2
[  3063.578] 	Module class: X.Org Video Driver
[  3063.578] 	ABI class: X.Org Video Driver, version 10.0
[  3063.578] (II) LoadModule: "savage"
[  3063.578] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[  3063.579] (II) Module savage: vendor="X.Org Foundation"
[  3063.580] 	compiled for 1.10.0, module version = 2.3.2
[  3063.580] 	Module class: X.Org Video Driver
[  3063.580] 	ABI class: X.Org Video Driver, version 10.0
[  3063.580] (II) LoadModule: "i740"
[  3063.580] (II) Loading /usr/lib/xorg/modules/drivers/i740_drv.so
[  3063.581] (II) Module i740: vendor="X.Org Foundation"
[  3063.582] 	compiled for 1.10.0, module version = 1.3.2
[  3063.582] 	Module class: X.Org Video Driver
[  3063.582] 	ABI class: X.Org Video Driver, version 10.0
[  3063.582] (II) LoadModule: "geode"
[  3063.583] (II) Loading /usr/lib/xorg/modules/drivers/geode_drv.so
[  3063.583] (II) Module geode: vendor="X.Org Foundation"
[  3063.584] 	compiled for 1.10.0, module version = 2.11.12
[  3063.585] 	Module class: X.Org Video Driver
[  3063.585] 	ABI class: X.Org Video Driver, version 10.0
[  3063.585] (II) LoadModule: "i128"
[  3063.585] (II) Loading /usr/lib/xorg/modules/drivers/i128_drv.so
[  3063.585] (II) Module i128: vendor="X.Org Foundation"
[  3063.586] 	compiled for 1.10.0, module version = 1.3.4
[  3063.587] 	Module class: X.Org Video Driver
[  3063.587] 	ABI class: X.Org Video Driver, version 10.0
[  3063.587] (II) LoadModule: "s3"
[  3063.587] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[  3063.588] (II) Module s3: vendor="X.Org Foundation"
[  3063.588] 	compiled for 1.10.0, module version = 0.6.3
[  3063.589] 	Module class: X.Org Video Driver
[  3063.589] 	ABI class: X.Org Video Driver, version 10.0
[  3063.589] (II) LoadModule: "fbdev"
[  3063.589] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3063.590] (II) Module fbdev: vendor="X.Org Foundation"
[  3063.590] 	compiled for 1.10.0, module version = 0.4.2
[  3063.591] 	ABI class: X.Org Video Driver, version 10.0
[  3063.591] (II) LoadModule: "vesa"
[  3063.591] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3063.592] (II) Module vesa: vendor="X.Org Foundation"
[  3063.592] 	compiled for 1.10.0, module version = 2.3.0
[  3063.593] 	Module class: X.Org Video Driver
[  3063.593] 	ABI class: X.Org Video Driver, version 10.0
[  3063.593] (WW) Falling back to old probe method for s3virge
[  3063.594] (WW) Falling back to old probe method for sisusb
[  3063.594] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[  3063.600] (WW) Falling back to old probe method for trident
[  3063.600] (WW) Falling back to old probe method for siliconmotion
[  3063.601] (WW) Falling back to old probe method for apm
[  3063.602] (WW) Falling back to old probe method for sis
[  3063.602] (WW) Falling back to old probe method for cirrus
[  3063.603] (II) Loading sub module "cirrus_laguna"
[  3063.603] (II) LoadModule: "cirrus_laguna"
[  3063.603] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[  3063.604] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[  3063.604] 	compiled for 1.10.0, module version = 1.0.0
[  3063.605] 	ABI class: X.Org Video Driver, version 10.0
[  3063.605] (II) Loading sub module "cirrus_alpine"
[  3063.605] (II) LoadModule: "cirrus_alpine"
[  3063.605] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[  3063.606] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[  3063.606] 	compiled for 1.10.0, module version = 1.0.0
[  3063.607] 	ABI class: X.Org Video Driver, version 10.0
[  3063.607] (WW) Falling back to old probe method for neomagic
[  3063.608] (WW) Falling back to old probe method for tseng
[  3063.608] (WW) Falling back to old probe method for ark
[  3063.609] (WW) Falling back to old probe method for z4l
[  3063.609] (II) z4l driver for Video4Linux
[  3063.610] (WW) Falling back to old probe method for voodoo
[  3063.611] (WW) Falling back to old probe method for i740
[  3063.611] (WW) Falling back to old probe method for i128
[  3063.612] (WW) Falling back to old probe method for s3
[  3063.612] (II) FBDEV: driver for framebuffer: fbdev
[  3063.613] (II) VESA: driver for VESA chipsets: vesa
[  3063.615] (++) Using config file: "/home/oliver/xorg.conf.new"
[  3063.617] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3063.620] (==) ServerLayout "X.org Configured"
[  3063.622] (**) |-->Screen "Screen0" (0)
[  3063.624] (**) |   |-->Monitor "Monitor0"
[  3063.625] (**) |   |-->Device "Card0"
[  3063.625] (**) |-->Screen "Screen1" (1)
[  3063.626] (**) |   |-->Monitor "Monitor1"
[  3063.626] (**) |   |-->Device "Card1"
[  3063.627] (**) |-->Screen "Screen2" (2)
[  3063.627] (**) |   |-->Monitor "Monitor2"
[  3063.628] (**) |   |-->Device "Card2"
[  3063.628] (**) |-->Input Device "Mouse0"
[  3063.629] (**) |-->Input Device "Keyboard0"
[  3063.629] (==) Automatically adding devices
[  3063.630] (==) Automatically enabling devices
[  3063.631] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3063.631] 	Entry deleted from font path.
[  3063.632] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3063.632] 	Entry deleted from font path.
[  3063.633] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3063.633] 	Entry deleted from font path.
[  3063.634] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3063.634] 	Entry deleted from font path.
[  3063.635] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3063.635] 	Entry deleted from font path.
[  3063.636] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3063.636] 	Entry deleted from font path.
[  3063.637] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3063.637] 	Entry deleted from font path.
[  3063.638] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3063.638] 	Entry deleted from font path.
[  3063.639] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3063.639] 	Entry deleted from font path.
[  3063.640] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3063.641] 	Entry deleted from font path.
[  3063.641] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  3063.646] (**) ModulePath set to "/usr/lib/xorg/modules"
[  3063.647] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  3063.648] (WW) Disabling Mouse0
[  3063.648] (WW) Disabling Keyboard0
[  3063.650] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  3063.651] (WW) Falling back to old probe method for fbdev
[  3063.652] (II) Loading sub module "fbdevhw"
[  3063.652] (II) LoadModule: "fbdevhw"
[  3063.652] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3063.652] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3063.653] 	compiled for 1.10.1, module version = 0.0.2
[  3063.654] 	ABI class: X.Org Video Driver, version 10.0
[  3063.654] (WW) Falling back to old probe method for vesa
[  3063.654] Number of created screens does not match number of detected devices.
  Configuration failed.
```

---

### Post by genezkool323 on 2011-05-21
Well if it adds any more info, I discovered that under 10.10 the problem does not occur, however I already reimaged back to 11.04 because the gfx were considerably more sluggish under 10.10.

Does anyone know if there is a useful wiki that might discuss Sandybridge issues under Ubuntu?

---

### Post by helioft on 2011-05-23
Hello,

I have the exactly same issue. I just received my brand new Latitude 6320. I do also feel that the graphic interface goes much faster and smooth with ubuntu 11.04 than with the one given by dell. 

My issue is that when the second monitor is connected, and I disconnect the laptops one, it gets everything black. I cant neither find config files.

Do you have also any issues when turning off the pc? mine gets stucked mostly every time...

---

### Post by BingleBug on 2011-05-26
I'm in the same boat. I just received a Dell Latitude E6520 with the following specs:

Intel® Core™ i7-2620M (2.70GHz, 4M cache) with Turbo BoostTechnology 2.0 

nVidia® NVS™ 4200M 512MB DDR3 Discrete Graphics for Dual Core

I installed 11.04 Alternate (AMD64 - guided, encrypted LVM). After CD eject the machine went to restart and just hung for over 15 minutes. I powered off, then back on. Went through and installed some of the new drivers (one for wireless, the other for the nVidia card), then went through the Update Manager for the rest of the fixes.

Went to reboot the machine and it's been sitting here for over 20 minutes. The Ubuntu logo is showing and 2 of the 5 dots are red and have been that way for the 20 minutes.

I guess now the fin begins!

---

### Post by BingleBug on 2011-05-31
In addition to the above, now I'm getting:

"error: no video mode activated"

It's unclear as to the source of this error message. Though it may have something to do with installing the nVidia driver on the system. Which also corresponds with the error message that I don't have the hardware to run Unity.

Looking into: 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

BB

---

### Post by genezkool323 on 2011-06-02
helioft: I do not have any trouble when shutting the PC down. I don't know what to tell you on that front. But yes, 11.04 graphics seem much faster than 10.10.

BingleBug: I do not think I have the same issue as you. My issue seems to lie with GNOME or Ubuntu's compatibility with my video card. The nVidia seems to be a bit more supported than my Intel HD.

I think I have heard from some people knowledgeable with Sandybridge say that we probably will have to wait for the next major distro of our preferred Linux OSes before we get full support.

Hopefully.

---

### Post by aa-hcl on 2011-06-04
Hi,

I have got my new 6520 Dell laptop last week and installed 11.04 on it, keeping Windows 7. (need Win7 to be able to check the ntfs partition where I keep my files).

Laptop configuration: i7 2720 2.2GHz (quad), video card Nvidia 4200, 8Gb RAM.

What works:
- back-lit keyboard - but I guess this is a BIOS thing, nothing to do with linux
- screen OK
- generally all working fine, including stepping in CPU frequency, did not check TURBO regime yet, 

PROBLEMS:

1. I want to have touchpad AND the stick recognised separately, currently it is the same device

2. Touchpad is still recognised as a simple mouse, would prefer touchpad functions, but still keep the stick!

3. multi-monitor did not work well at all


Can any one advise anything on these issues? 


Many thanks!

---

### Post by genezkool323 on 2011-06-27
1. The touchpad and stick are also recognized together on my end.
2 and 3. Same boat, and I think we will be waiting for the next big release.

---

### Post by pcowdogg on 2011-07-12
Hopefully this is the answer

Background
 Apparently there is a new technology called Optimus that allows the OS...err I mean Windows to turn the grafx card on or off as needed. Dell has supported this technology and the default value is on via the Bios settings. EVEN though there are drivers to support the newer grafx cards for linux they do not support *nix systems to use the Optimus power saving features. poo

The Fix
1] press F12 as your computer starts up, go to bios settings, display and turn off optimus, save and restart. 2] (I assume you have drivers installed now, if not, do so) and then do the nvidia-xconfig command.
3] You are golden son!

Resource:
[http://ubuntuforums.org/archive/index.php/t-1726575.html](http://ubuntuforums.org/archive/index.php/t-1726575.html)

---

### Post by dave2001 on 2011-10-04
This is an issue with 11.04. I have 11.04 on a Dell Dimension desktop and a Thinkpad T60 laptop, and they both return the same error message when attempting to use 
~$ sudo Xorg -configure

However, you can get it *sort of* work by doing the following:
Boot and hold shift, this should bring you to the grub boot menu. Choose recovery mode. This gives you the recovery menu. Choose command line prompt. Now enter

sudo Xorg -configure

This should generate an xorg.conf.new file in your root's home folder. You can edit this file to have the settings you desire, and copy it to:  /etc/X11/xorg.conf

---

