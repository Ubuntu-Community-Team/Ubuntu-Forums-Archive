---
title: "video=ATI Radeon HD3200/driver=ati-driver-installer-9-1-x86.x86_64 NOT WORKING"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by niskyander2 on 2009-02-11
Just got a new PC (ASUS V3-M3A3200) which has the onboard graphics "ATI Radeon HD3200" and installed "Jaunty Jackalope Alpha 4".
Downloaded the driver "ati-driver-installer-9-1-x86.x86_64.run" from ATI ([http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)).
** ughhh, not working **
After I go through the install & reboot - the system comes up  in low graphics mode until I revert to generic settings.

Xorg.0.log file [INDENT]shows this  error
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVisualsProc
[    0.052024] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.052047] (EE) Failed to load module "glx" (loader failed, 7)
[    0.053327] (EE) module ABI major version (1) doesn't match the server's version (2)
[    0.053363] (EE) Failed to load module "dri" (module requirement mismatch, 0)
3871 3637[/INDENT]

fglrxinfo shows this error
[INDENT]Xlib:  extension "GLX" missing on display ":3.0".
Error: couldn't find RGB GLX visual![/INDENT]

Any ideas?
Thx in advance!!

---

### Post by niskyander2 on 2009-02-12
Any  Suggestions (I am sort of stuck).
Here is entire Xorg.0.log file


[I]This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.5.99.902 (1.6.0 RC 2)
Release Date: 2009-1-30
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux alexander 2.6.28-7-generic #20-Ubuntu SMP Mon Feb 9 15:42:34 UTC 2009 x86_64
Build Date: 11 February 2009  02:47:17AM
xorg-server 2:1.5.99.902-0ubuntu6 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: [    0.000639] (--) probed, [    0.000647] (**) from config file, [    0.000653] (==) default setting,
	[    0.000658] (++) from command line, [    0.000664] (!!) notice, [    0.000669] (II) informational,
	[    0.000674] (WW) warning, [    0.000679] (EE) error, [    0.000684] (NI) not implemented, [    0.000690] (??) unknown.
[    0.000737] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 12 20:41:20 2009
[    0.000776] (==) Using config file: "/etc/X11/xorg.conf"
[    0.000886] (==) ServerLayout "aticonfig Layout"
[    0.000893] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    0.000899] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    0.001066] (**) |   |-->Device "aticonfig-Device[0]-0"
[    0.001086] (==) Automatically adding devices
[    0.001090] (==) Automatically enabling devices
[    0.001110] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.001153] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
[    0.001157] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.001162] (II) Cannot locate a core pointer device.
[    0.001166] (II) Cannot locate a core keyboard device.
[    0.001169] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.001177] (II) Loader magic: 0xb40
[    0.001181] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.001195] (II) Loader running on linux
[    0.001201] (++) using VT number 7

[    0.025636] (--) PCI:*(0@1:5:0) ATI Technologies Inc Radeon HD 3200 Graphics rev 0, Mem @ 0xd0000000/268435456, 0xfbdf0000/65536, 0xfbc00000/1048576, I/O @ 0x0000d000/256
[    0.025812] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.025832] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.026418] (II) "extmod" will be loaded by default.
[    0.026422] (II) "dbe" will be loaded by default.
[    0.026426] (II) "glx" will be loaded by default.
[    0.026430] (II) "record" will be loaded by default.
[    0.026434] (II) "dri" will be loaded by default.
[    0.026438] (II) "dri2" will be loaded by default.
[    0.026443] (II) LoadModule: "extmod"
[    0.026740] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.026888] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.026911] (II) Loading extension MIT-SCREEN-SAVER
[    0.026915] (II) Loading extension XFree86-VidModeExtension
[    0.026919] (II) Loading extension XFree86-DGA
[    0.026923] (II) Loading extension DPMS
[    0.026926] (II) Loading extension XVideo
[    0.026931] (II) Loading extension XVideo-MotionCompensation
[    0.026935] (II) Loading extension X-Resource
[    0.026939] (II) LoadModule: "dbe"
[    0.027134] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.027198] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.027219] (II) Loading extension DOUBLE-BUFFER
[    0.027224] (II) LoadModule: "glx"
[    0.027404] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVisualsProc
[    0.027565] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.027578] (II) UnloadModule: "glx"
[    0.027582] (EE) Failed to load module "glx" (loader failed, 7)
[    0.027589] (II) LoadModule: "record"
[    0.027780] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.027857] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.027879] (II) Loading extension RECORD
[    0.027883] (II) LoadModule: "dri"
[    0.028079] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.028225] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
[    0.028245] (EE) module ABI major version (1) doesn't match the server's version (2)
[    0.028252] (II) UnloadModule: "dri"
[    0.028255] (II) Unloading /usr/lib/xorg/modules/extensions//libdri.so
[    0.028261] (EE) Failed to load module "dri" (module requirement mismatch, 0)
[    0.028268] (II) LoadModule: "dri2"
[    0.028451] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.028530] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.028549] (II) Loading extension DRI2
[    0.028554] (II) LoadModule: "fglrx"
[    0.028661] (II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.032812] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.57.2
	Module class: X.Org Video Driver
[atiddxSetup] X version mismatch - detected X.org 7.1.-1.902, required X.org 7.4.-1.906
[    0.033080] (II) UnloadModule: "fglrx"
[    0.033085] (II) Unloading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.033091] (EE) Failed to load module "fglrx" (module requirement mismatch, 0)
[    0.033113] (EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
[/I]

---

### Post by Sopranosmainman on 2009-02-23
i have the same issue installing from envyng! 

any ideas?

---

### Post by hotani on 2009-03-04
Same vid card here. Works fine with default settings. After installing the proprietary drivers (fglrx), the image is cropped on my screen, cut off on right and bottom. 

Playing videos results in tons of flicker.

---

### Post by shakaran on 2009-03-04
Same for me. Ubuntu go to low-graphics-mode.

My log Xorg.0.log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.902 (1.6.0 RC 2)
Release Date: 2009-1-30
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux otorion 2.6.28-8-generic #26-Ubuntu SMP Wed Feb 25 04:28:54 UTC 2009 i686
Build Date: 18 February 2009  01:41:32AM
xorg-server 2:1.5.99.902-0ubuntu7 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.000889] (--) probed, [    0.000901] (**) from config file, [    0.000909] (==) default setting,
	[    0.000917] (++) from command line, [    0.000925] (!!) notice, [    0.000932] (II) informational,
	[    0.000940] (WW) warning, [    0.000948] (EE) error, [    0.000955] (NI) not implemented, [    0.000963] (??) unknown.
[    0.001030] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  5 04:59:52 2009
[    0.001072] (==) Using config file: "/etc/X11/xorg.conf"
[    0.001210] (==) ServerLayout "aticonfig Layout"
[    0.001220] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    0.001228] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    0.001511] (**) |   |-->Device "aticonfig-Device[0]-0"
[    0.001539] (==) Automatically adding devices
[    0.001546] (==) Automatically enabling devices
[    0.001644] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.001693] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
[    0.001701] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.001708] (II) Cannot locate a core pointer device.
[    0.001715] (II) Cannot locate a core keyboard device.
[    0.001721] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.001732] (II) Loader magic: 0x3bc0
[    0.001739] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.001760] (II) Loader running on linux
[    0.001769] (++) using VT number 7

[    0.067393] (--) PCI:*(0@1:0:0) ATI Technologies Inc M24 [Radeon Mobility X600] rev 0, Mem @ 0xc8000000/0, 0xb8100000/0, I/O @ 0x00003000/0, BIOS @ 0x????????/131072
[    0.069014] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.069048] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.069155] (II) "extmod" will be loaded by default.
[    0.069162] (II) "dbe" will be loaded by default.
[    0.069169] (II) "glx" will be loaded by default.
[    0.069175] (II) "record" will be loaded by default.
[    0.069181] (II) "dri" will be loaded by default.
[    0.069187] (II) "dri2" will be loaded by default.
[    0.069197] (II) LoadModule: "extmod"
[    0.069651] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.069820] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.069850] (II) Loading extension MIT-SCREEN-SAVER
[    0.069857] (II) Loading extension XFree86-VidModeExtension
[    0.069864] (II) Loading extension XFree86-DGA
[    0.069871] (II) Loading extension DPMS
[    0.069896] (II) Loading extension XVideo
[    0.069904] (II) Loading extension XVideo-MotionCompensation
[    0.069910] (II) Loading extension X-Resource
[    0.069917] (II) LoadModule: "dbe"
[    0.070190] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.070264] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.070292] (II) Loading extension DOUBLE-BUFFER
[    0.070299] (II) LoadModule: "glx"
[    0.070570] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: miInitVisualsProc
[    0.070705] (EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
[    0.070715] (II) UnloadModule: "glx"
[    0.070722] (EE) Failed to load module "glx" (loader failed, 7)
[    0.070733] (II) LoadModule: "record"
[    0.071004] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.071081] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.071109] (II) Loading extension RECORD
[    0.071117] (II) LoadModule: "dri"
[    0.071381] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.071538] (II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
[    0.071559] (EE) module ABI major version (1) doesn't match the server's version (2)
[    0.071569] (II) UnloadModule: "dri"
[    0.071575] (II) Unloading /usr/lib/xorg/modules/extensions//libdri.so
[    0.071584] (EE) Failed to load module "dri" (module requirement mismatch, 0)
[    0.071595] (II) LoadModule: "dri2"
[    0.071870] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.071946] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.071971] (II) Loading extension DRI2
[    0.071980] (II) LoadModule: "fglrx"
[    0.072180] (II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.077490] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.57.2
	Module class: X.Org Video Driver
[atiddxSetup] X version mismatch - detected X.org 7.1.-1.902, required X.org 7.4.-1.906
[    0.077869] (II) UnloadModule: "fglrx"
[    0.077876] (II) Unloading /usr/lib/xorg/modules/drivers//fglrx_drv.so
[    0.077885] (EE) Failed to load module "fglrx" (module requirement mismatch, 0)
[    0.077896] (EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by shakaran on 2009-03-04
Yeah! This seems a bug with Xserver version and ABI:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027)

---

