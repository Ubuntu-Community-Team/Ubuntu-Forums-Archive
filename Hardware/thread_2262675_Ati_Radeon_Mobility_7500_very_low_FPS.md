---
title: "Ati Radeon Mobility 7500 very low FPS"
date: 2015-01-26
forum: Hardware
---

### Post by fedbriz91 on 2015-01-26
Hi, i have installed Xubuntu 14.04 in a old laptop with Pentium 4 2.4ghz, 2gb ram, ati radeon mobility 7500. 
I think there is a problem with driver "radeon", cause with glxgears it can do only 20-30 fps.I see peoples do more than 1000 fps with the same PC in ubuntu 10.10.

```
admin@pc:~$ glxgearsRunning synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
148 frames in 5.0 seconds = 29.567 FPS
128 frames in 5.0 seconds = 25.418 FPS
153 frames in 5.0 seconds = 30.403 FPS
156 frames in 5.0 seconds = 31.182 FPS
147 frames in 5.0 seconds = 29.352 FPS
152 frames in 5.0 seconds = 30.320 FPS
163 frames in 5.0 seconds = 32.504 FPS
144 frames in 5.0 seconds = 28.707 FPS

```


```
admin@pc:~$ dmesg | egrep 'drm|radeon'[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=8222457a-13e0-4137-b50a-029ca93e6613 ro radeon.dpm=0
[    8.197476] [drm] Initialized drm 1.1.0 20060810
[    9.646576] [drm] radeon kernel modesetting enabled.
[    9.646687] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    9.726615] [drm] initializing kernel modesetting (RV200 0x1002:0x4C57 0x1043:0x1622).
[    9.726659] [drm] register mmio base: 0xEF000000
[    9.726662] [drm] register mmio size: 65536
[    9.726909] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[    9.726936] radeon 0000:01:00.0: GTT: 64M 0xF8000000 - 0xFBFFFFFF
[    9.726947] radeon 0000:01:00.0: VRAM: 128M 0x00000000F0000000 - 0x00000000F7FFFFFF (32M used)
[    9.726971] [drm] Detected VRAM RAM=128M, BAR=128M
[    9.726974] [drm] RAM width 64bits DDR
[    9.743908] [drm] radeon: 32M of VRAM memory ready
[    9.743913] [drm] radeon: 64M of GTT memory ready.
[    9.746863] radeon 0000:01:00.0: WB disabled
[    9.746880] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000f8000000 and cpu addr 0xf840c000
[    9.746886] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    9.746888] [drm] Driver supports precise vblank timestamp query.
[    9.746909] [drm] radeon: irq initialized.
[    9.746940] [drm] Loading R100 Microcode
[    9.847432] [drm] radeon: ring at 0x00000000F8001000
[    9.847465] [drm] ring test succeeded in 1 usecs
[    9.847809] [drm] ib test succeeded in 0 usecs
[    9.977481] [drm] Panel ID String: Samsung LTN150P1-L02    
[    9.977491] [drm] Panel Size 1400x1050
[    9.988618] [drm] No TV DAC info found in BIOS
[   10.011763] [drm] radeon legacy LVDS backlight initialized
[   10.011775] [drm] Radeon Display Connectors
[   10.011778] [drm] Connector 0:
[   10.011782] [drm]   VGA-1
[   10.011786] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   10.011788] [drm]   Encoders:
[   10.011791] [drm]     CRT1: INTERNAL_DAC1
[   10.011794] [drm] Connector 1:
[   10.011796] [drm]   LVDS-1
[   10.011798] [drm]   Encoders:
[   10.011800] [drm]     LCD1: INTERNAL_LVDS
[   10.011802] [drm] Connector 2:
[   10.011805] [drm]   SVIDEO-1
[   10.011807] [drm]   Encoders:
[   10.011809] [drm]     TV1: INTERNAL_DAC2
[   10.507258] [drm] fb mappable at 0xF0040000
[   10.507266] [drm] vram apper at 0xF0000000
[   10.507269] [drm] size 1478656
[   10.507271] [drm] fb depth is 8
[   10.507273] [drm]    pitch is 1408
[   10.511474] fbcon: radeondrmfb (fb0) is primary device
[   10.591278] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   10.591280] radeon 0000:01:00.0: registered panic notifier
[   10.737351] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0



```

```
admin@pc:~$ lspci | grep VGA01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV200/M7 [Mobility Radeon 7500]
admin@pc:~$ sudo lshw -c display | grep driver
[sudo] password for admin: 
       configuration: driver=radeon latency=64 mingnt=8



```

What is the problem ? thanks in advance for help

---

### Post by ajgreeny on 2015-01-26
Firstly I think you can ignore the FPS figures from glxgears going back to 10.10 in comparison with today's later versions of Ubuntu's figures.  Note the first line of the output from your glxgears which says that it is:-
```
Running synchronized to the vertical refresh.  The framerate should be approximately the same as the monitor refresh rate.
```and whilst 30FPS is quite slow, you don't say what monitor you have.  The computer itself is obviously of low spec by today's standards; what about the monitor?

It is also worth saying that glxgears was never intended to be a proper benchmark utility; glxgears is just a basic test to see if 3D is working or not, not a benchmark.

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

I could go on, but will leave you to search for yourself and figure out if it matters or not to you what figure glxgears gives you as long as the display is good enough for the purposes for which you use it.

---

### Post by Mark Phelps on 2015-01-27
> I see peoples do more than 1000 fps with the same PC in ubuntu 10.10.That's most likely because, back then, the fglrx restrticted driver may have worked on those PCs.  Today, you are relegated to the default Radeon driver -- which may not perform as well as the older fglrx driver.

---

### Post by fedbriz91 on 2015-01-30
> **ajgreeny said:**
> Firstly I think you can ignore the FPS figures from glxgears going back to 10.10 in comparison with today's later versions of Ubuntu's figures. Note the first line of the output from your glxgears which says that it is:-
```
Running synchronized to the vertical refresh.  The framerate should be approximately the same as the monitor refresh rate.
```and whilst 30FPS is quite slow, you don't say what monitor you have. The computer itself is obviously of low spec by today's standards; what about the monitor?

It is also worth saying that glxgears was never intended to be a proper benchmark utility; glxgears is just a basic test to see if 3D is working or not, not a benchmark.

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

I could go on, but will leave you to search for yourself and figure out if it matters or not to you what figure glxgears gives you as long as the display is good enough for the purposes for which you use it.

The monitor of my laptop is a 60hz in 1400x1050px (4/3),



> **Mark Phelps said:**
> That's most likely because, back then, the fglrx restrticted driver may have worked on those PCs.  Today, you are relegated to the default Radeon driver -- which may not perform as well as the older fglrx driver.


how can install the old fglrx restricted driver ?

---

### Post by Yellow Pasque on 2015-01-30
There's nothing concerning in the dmesg. Perhaps you could share your /var/log/Xorg.0.log

> **fedbriz91 said:**
> how can install the old fglrx restricted driver ?

You can't. The fglrx/Catalyst driver never supported this card, and even if it did, it wouldn't work on any modern, supported version of Ubuntu. I have no idea why someone would even mention it...

---

### Post by fedbriz91 on 2015-02-01
this is my xorg log
```

X.Org X Server 1.15.1Release Date: 2014-04-13
[    19.274] X Protocol Version 11, Revision 0
[    19.274] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    19.274] Current Operating System: Linux Xub 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686
[    19.274] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=8222457a-13e0-4137-b50a-029ca93e6613 ro radeon.dpm=0
[    19.274] Build Date: 10 December 2014  06:16:10PM
[    19.274] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support)
[    19.274] Current version of pixman: 0.30.2
[    19.274]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    19.274] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.274] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  1 15:37:16 2015
[    19.286] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.287] (==) No Layout section.  Using the first Screen section.
[    19.287] (==) No screen section available. Using defaults.
[    19.287] (**) |-->Screen "Default Screen Section" (0)
[    19.287] (**) |   |-->Monitor "<default monitor>"
[    19.287] (==) No monitor specified for screen "Default Screen Section".



```

---

### Post by Yellow Pasque on 2015-02-02
^That is only the first few lines of the log file...
Also, is there a reason you turn off DPM with radeon.dpm=0?

---

### Post by fedbriz91 on 2015-02-06
Oh, im sorry, this is complete.

Yeah i try to deactive DPM, but now i restore default settings. cause the problem persist 
```

[    17.554] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    17.554] X Protocol Version 11, Revision 0
[    17.554] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    17.554] Current Operating System: Linux Xub 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686
[    17.554] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=8222457a-13e0-4137-b50a-029ca93e6613 ro
[    17.554] Build Date: 10 December 2014  06:16:10PM
[    17.554] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    17.554] Current version of pixman: 0.30.2
[    17.554] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.554] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.554] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  6 17:27:50 2015
[    17.560] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.560] (==) No Layout section.  Using the first Screen section.
[    17.560] (==) No screen section available. Using defaults.
[    17.560] (**) |-->Screen "Default Screen Section" (0)
[    17.560] (**) |   |-->Monitor "<default monitor>"
[    17.561] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.561] (==) Automatically adding devices
[    17.561] (==) Automatically enabling devices
[    17.561] (==) Automatically adding GPU devices
[    17.561] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.561] 	Entry deleted from font path.
[    17.561] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.561] 	Entry deleted from font path.
[    17.561] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.561] 	Entry deleted from font path.
[    17.561] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.561] 	Entry deleted from font path.
[    17.561] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.561] 	Entry deleted from font path.
[    17.561] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    17.561] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.561] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.561] (II) Loader magic: 0xb77436c0
[    17.561] (II) Module ABI versions:
[    17.561] 	X.Org ANSI C Emulation: 0.4
[    17.561] 	X.Org Video Driver: 15.0
[    17.561] 	X.Org XInput driver : 20.0
[    17.561] 	X.Org Server Extension : 8.0
[    17.562] (II) xfree86: Adding drm device (/dev/dri/card0)
[    17.575] (--) PCI:*(0:1:0:0) 1002:4c57:1043:1622 rev 0, Mem @ 0xf0000000/134217728, 0xef000000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
[    17.575] Initializing built-in extension Generic Event Extension
[    17.575] Initializing built-in extension SHAPE
[    17.575] Initializing built-in extension MIT-SHM
[    17.575] Initializing built-in extension XInputExtension
[    17.575] Initializing built-in extension XTEST
[    17.575] Initializing built-in extension BIG-REQUESTS
[    17.575] Initializing built-in extension SYNC
[    17.575] Initializing built-in extension XKEYBOARD
[    17.575] Initializing built-in extension XC-MISC
[    17.575] Initializing built-in extension SECURITY
[    17.575] Initializing built-in extension XINERAMA
[    17.575] Initializing built-in extension XFIXES
[    17.575] Initializing built-in extension RENDER
[    17.576] Initializing built-in extension RANDR
[    17.576] Initializing built-in extension COMPOSITE
[    17.576] Initializing built-in extension DAMAGE
[    17.576] Initializing built-in extension MIT-SCREEN-SAVER
[    17.576] Initializing built-in extension DOUBLE-BUFFER
[    17.576] Initializing built-in extension RECORD
[    17.576] Initializing built-in extension DPMS
[    17.576] Initializing built-in extension Present
[    17.576] Initializing built-in extension DRI3
[    17.576] Initializing built-in extension X-Resource
[    17.576] Initializing built-in extension XVideo
[    17.576] Initializing built-in extension XVideo-MotionCompensation
[    17.576] Initializing built-in extension SELinux
[    17.576] Initializing built-in extension XFree86-VidModeExtension
[    17.576] Initializing built-in extension XFree86-DGA
[    17.576] Initializing built-in extension XFree86-DRI
[    17.576] Initializing built-in extension DRI2
[    17.576] (II) LoadModule: "glx"
[    17.580] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.613] (II) Module glx: vendor="X.Org Foundation"
[    17.614] 	compiled for 1.15.1, module version = 1.0.0
[    17.614] 	ABI class: X.Org Server Extension, version 8.0
[    17.614] (==) AIGLX enabled
[    17.614] Loading extension GLX
[    17.614] (==) Matched fglrx as autoconfigured driver 0
[    17.614] (==) Matched ati as autoconfigured driver 1
[    17.614] (==) Matched fglrx as autoconfigured driver 2
[    17.614] (==) Matched ati as autoconfigured driver 3
[    17.614] (==) Matched modesetting as autoconfigured driver 4
[    17.614] (==) Matched fbdev as autoconfigured driver 5
[    17.614] (==) Matched vesa as autoconfigured driver 6
[    17.614] (==) Assigned the driver to the xf86ConfigLayout
[    17.614] (II) LoadModule: "fglrx"
[    17.617] (WW) Warning, couldn't open module fglrx
[    17.618] (II) UnloadModule: "fglrx"
[    17.618] (II) Unloading fglrx
[    17.618] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.618] (II) LoadModule: "ati"
[    17.618] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.618] (II) Module ati: vendor="X.Org Foundation"
[    17.618] 	compiled for 1.15.1, module version = 7.3.0
[    17.618] 	Module class: X.Org Video Driver
[    17.618] 	ABI class: X.Org Video Driver, version 15.0
[    17.618] (II) LoadModule: "radeon"
[    17.619] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.643] (II) Module radeon: vendor="X.Org Foundation"
[    17.643] 	compiled for 1.15.1, module version = 7.3.0
[    17.643] 	Module class: X.Org Video Driver
[    17.643] 	ABI class: X.Org Video Driver, version 15.0
[    17.643] (II) LoadModule: "modesetting"
[    17.644] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.645] (II) Module modesetting: vendor="X.Org Foundation"
[    17.645] 	compiled for 1.15.0, module version = 0.8.1
[    17.645] 	Module class: X.Org Video Driver
[    17.645] 	ABI class: X.Org Video Driver, version 15.0
[    17.645] (II) LoadModule: "fbdev"
[    17.645] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.645] (II) Module fbdev: vendor="X.Org Foundation"
[    17.645] 	compiled for 1.15.0, module version = 0.4.4
[    17.645] 	Module class: X.Org Video Driver
[    17.645] 	ABI class: X.Org Video Driver, version 15.0
[    17.645] (II) LoadModule: "vesa"
[    17.653] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.653] (II) Module vesa: vendor="X.Org Foundation"
[    17.653] 	compiled for 1.15.0, module version = 2.3.3
[    17.653] 	Module class: X.Org Video Driver
[    17.653] 	ABI class: X.Org Video Driver, version 15.0
[    17.653] (==) Matched fglrx as autoconfigured driver 0
[    17.653] (==) Matched ati as autoconfigured driver 1
[    17.653] (==) Matched fglrx as autoconfigured driver 2
[    17.653] (==) Matched ati as autoconfigured driver 3
[    17.653] (==) Matched modesetting as autoconfigured driver 4
[    17.653] (==) Matched fbdev as autoconfigured driver 5
[    17.653] (==) Matched vesa as autoconfigured driver 6
[    17.653] (==) Assigned the driver to the xf86ConfigLayout
[    17.653] (II) LoadModule: "fglrx"
[    17.661] (WW) Warning, couldn't open module fglrx
[    17.661] (II) UnloadModule: "fglrx"
[    17.661] (II) Unloading fglrx
[    17.661] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.665] (II) LoadModule: "ati"
[    17.665] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.665] (II) Module ati: vendor="X.Org Foundation"
[    17.665] 	compiled for 1.15.1, module version = 7.3.0
[    17.665] 	Module class: X.Org Video Driver
[    17.665] 	ABI class: X.Org Video Driver, version 15.0
[    17.665] (II) LoadModule: "modesetting"
[    17.671] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.671] (II) Module modesetting: vendor="X.Org Foundation"
[    17.671] 	compiled for 1.15.0, module version = 0.8.1
[    17.671] 	Module class: X.Org Video Driver
[    17.671] 	ABI class: X.Org Video Driver, version 15.0
[    17.671] (II) UnloadModule: "modesetting"
[    17.671] (II) Unloading modesetting
[    17.671] (II) Failed to load module "modesetting" (already loaded, 0)
[    17.671] (II) LoadModule: "fbdev"
[    17.673] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.673] (II) Module fbdev: vendor="X.Org Foundation"
[    17.673] 	compiled for 1.15.0, module version = 0.4.4
[    17.673] 	Module class: X.Org Video Driver
[    17.673] 	ABI class: X.Org Video Driver, version 15.0
[    17.673] (II) UnloadModule: "fbdev"
[    17.673] (II) Unloading fbdev
[    17.673] (II) Failed to load module "fbdev" (already loaded, 0)
[    17.673] (II) LoadModule: "vesa"
[    17.673] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.673] (II) Module vesa: vendor="X.Org Foundation"
[    17.673] 	compiled for 1.15.0, module version = 2.3.3
[    17.674] 	Module class: X.Org Video Driver
[    17.674] 	ABI class: X.Org Video Driver, version 15.0
[    17.674] (II) UnloadModule: "vesa"
[    17.674] (II) Unloading vesa
[    17.674] (II) Failed to load module "vesa" (already loaded, 0)
[    17.674] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
	HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII
[    17.761] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    17.761] (II) FBDEV: driver for framebuffer: fbdev
[    17.761] (II) VESA: driver for VESA chipsets: vesa
[    17.761] (++) using VT number 7


[    17.761] (II) [KMS] Kernel modesetting enabled.
[    17.762] (WW) Falling back to old probe method for modesetting
[    17.762] (WW) Falling back to old probe method for fbdev
[    17.762] (II) Loading sub module "fbdevhw"
[    17.762] (II) LoadModule: "fbdevhw"
[    17.762] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.763] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.763] 	compiled for 1.15.1, module version = 0.0.2
[    17.763] 	ABI class: X.Org Video Driver, version 15.0
[    17.763] (WW) Falling back to old probe method for vesa
[    17.763] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    17.763] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    17.763] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.763] (==) RADEON(0): Default visual is TrueColor
[    17.763] (==) RADEON(0): RGB weight 888
[    17.763] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.763] (--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
[    17.763] (II) Loading sub module "dri2"
[    17.763] (II) LoadModule: "dri2"
[    17.763] (II) Module "dri2" already built-in
[    17.763] (II) Loading sub module "exa"
[    17.763] (II) LoadModule: "exa"
[    17.764] (II) Loading /usr/lib/xorg/modules/libexa.so
[    17.764] (II) Module exa: vendor="X.Org Foundation"
[    17.764] 	compiled for 1.15.1, module version = 2.6.0
[    17.764] 	ABI class: X.Org Video Driver, version 15.0
[    17.764] (II) RADEON(0): KMS Color Tiling: disabled
[    17.764] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    17.764] (II) RADEON(0): KMS Pageflipping: enabled
[    17.764] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    17.791] (II) RADEON(0): Output VGA-0 has no monitor section
[    17.791] (II) RADEON(0): Output LVDS has no monitor section
[    17.820] (II) RADEON(0): Output S-video has no monitor section
[    17.846] (II) RADEON(0): EDID for output VGA-0
[    17.846] (II) RADEON(0): EDID for output LVDS
[    17.846] (II) RADEON(0): Printing probed modes for output LVDS
[    17.846] (II) RADEON(0): Modeline "1400x1050"x60.8  108.00  1400 34208 34320 1672  1050 1050 1053 1063 (64.6 kHz eP)
[    17.846] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[    17.846] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[    17.846] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[    17.846] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    17.847] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    17.847] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.847] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    17.847] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.847] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    17.847] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    17.847] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    17.871] (II) RADEON(0): EDID for output S-video
[    17.871] (II) RADEON(0): Output VGA-0 disconnected
[    17.871] (II) RADEON(0): Output LVDS connected
[    17.871] (II) RADEON(0): Output S-video disconnected
[    17.871] (II) RADEON(0): Using exact sizes for initial modes
[    17.871] (II) RADEON(0): Output LVDS using initial mode 1400x1050
[    17.871] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.871] (II) RADEON(0): mem size init: gart size :3dff000 vram size: s:2000000 visible:1e57000
[    17.871] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    17.871] (==) RADEON(0): DPI set to (96, 96)
[    17.871] (II) Loading sub module "fb"
[    17.871] (II) LoadModule: "fb"
[    17.875] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.877] (II) Module fb: vendor="X.Org Foundation"
[    17.877] 	compiled for 1.15.1, module version = 1.0.0
[    17.877] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.877] (II) Loading sub module "ramdac"
[    17.877] (II) LoadModule: "ramdac"
[    17.877] (II) Module "ramdac" already built-in
[    17.877] (II) UnloadModule: "modesetting"
[    17.877] (II) Unloading modesetting
[    17.877] (II) UnloadModule: "fbdev"
[    17.877] (II) Unloading fbdev
[    17.877] (II) UnloadSubModule: "fbdevhw"
[    17.877] (II) Unloading fbdevhw
[    17.877] (II) UnloadModule: "vesa"
[    17.877] (II) Unloading vesa
[    17.878] (--) Depth 24 pixmap format is 32 bpp
[    17.878] (II) RADEON(0): [DRI2] Setup complete
[    17.878] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    17.878] (II) RADEON(0): [DRI2]   VDPAU driver: radeon
[    17.878] (II) RADEON(0): Front buffer size: 5776K
[    17.878] (II) RADEON(0): VRAM usage limit set to 22734K
[    17.878] (==) RADEON(0): Backing store enabled
[    17.878] (II) RADEON(0): Direct rendering enabled
[    17.878] (II) RADEON(0): Render acceleration enabled for R100 type cards.
[    17.878] (II) EXA(0): Driver allocated offscreen pixmaps
[    17.878] (II) EXA(0): Driver registered support for the following operations:
[    17.879] (II)         Solid
[    17.879] (II)         Copy
[    17.879] (II)         Composite (RENDER acceleration)
[    17.879] (II)         UploadToScreen
[    17.879] (II)         DownloadFromScreen
[    17.879] (II) RADEON(0): Acceleration enabled
[    17.879] (==) RADEON(0): DPMS enabled
[    17.879] (==) RADEON(0): Silken mouse enabled
[    17.879] (II) RADEON(0): Set up textured video
[    17.879] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    17.879] (II) RADEON(0): [XvMC] Extension initialized.
[    17.879] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.879] (--) RandR disabled
[    17.993] (II) SELinux: Disabled on system
[    18.031] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.031] (II) AIGLX: enabled GLX_ARB_create_context
[    18.031] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    18.031] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    18.031] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.031] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.031] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    18.031] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    18.031] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.031] (II) AIGLX: Loaded and initialized radeon
[    18.031] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.165] (II) RADEON(0): Setting screen physical size to 370 x 277
[    18.196] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.211] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.214] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.214] (II) LoadModule: "evdev"
[    18.215] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.219] (II) Module evdev: vendor="X.Org Foundation"
[    18.219] 	compiled for 1.15.0, module version = 2.8.2
[    18.219] 	Module class: X.Org XInput Driver
[    18.219] 	ABI class: X.Org XInput driver, version 20.0
[    18.220] (II) Using input driver 'evdev' for 'Power Button'
[    18.220] (**) Power Button: always reports core events
[    18.220] (**) evdev: Power Button: Device: "/dev/input/event2"
[    18.220] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.220] (--) evdev: Power Button: Found keys
[    18.220] (II) evdev: Power Button: Configuring as keyboard
[    18.220] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.220] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.220] (**) Option "xkb_rules" "evdev"
[    18.220] (**) Option "xkb_model" "pc105"
[    18.220] (**) Option "xkb_layout" "it"
[    18.227] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    18.229] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    18.229] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.229] (II) Using input driver 'evdev' for 'Video Bus'
[    18.229] (**) Video Bus: always reports core events
[    18.229] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    18.230] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.230] (--) evdev: Video Bus: Found keys
[    18.230] (II) evdev: Video Bus: Configuring as keyboard
[    18.230] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input12/event5"
[    18.230] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.230] (**) Option "xkb_rules" "evdev"
[    18.230] (**) Option "xkb_model" "pc105"
[    18.230] (**) Option "xkb_layout" "it"
[    18.232] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    18.232] (II) No input driver specified, ignoring this device.
[    18.232] (II) This device may have been added with another device file.
[    18.232] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    18.233] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.233] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.233] (**) Sleep Button: always reports core events
[    18.233] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[    18.233] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    18.233] (--) evdev: Sleep Button: Found keys
[    18.233] (II) evdev: Sleep Button: Configuring as keyboard
[    18.233] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[    18.233] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    18.233] (**) Option "xkb_rules" "evdev"
[    18.233] (**) Option "xkb_model" "pc105"
[    18.233] (**) Option "xkb_layout" "it"
[    18.234] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[    18.234] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    18.234] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event6)
[    18.235] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    18.235] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[    18.235] (**) Asus Laptop extra buttons: always reports core events
[    18.235] (**) evdev: Asus Laptop extra buttons: Device: "/dev/input/event6"
[    18.235] (--) evdev: Asus Laptop extra buttons: Vendor 0 Product 0
[    18.235] (--) evdev: Asus Laptop extra buttons: Found keys
[    18.235] (II) evdev: Asus Laptop extra buttons: Configuring as keyboard
[    18.235] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input13/event6"
[    18.235] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD, id 9)
[    18.235] (**) Option "xkb_rules" "evdev"
[    18.235] (**) Option "xkb_model" "pc105"
[    18.235] (**) Option "xkb_layout" "it"
[    18.236] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.236] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.236] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.236] (**) AT Translated Set 2 keyboard: always reports core events
[    18.236] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.236] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.236] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.236] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.237] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    18.237] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    18.237] (**) Option "xkb_rules" "evdev"
[    18.237] (**) Option "xkb_model" "pc105"
[    18.237] (**) Option "xkb_layout" "it"
[    18.238] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    18.238] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.238] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.238] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    18.238] (II) LoadModule: "synaptics"
[    18.239] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.239] (II) Module synaptics: vendor="X.Org Foundation"
[    18.239] 	compiled for 1.15.0, module version = 1.7.4
[    18.239] 	Module class: X.Org XInput Driver
[    18.239] 	ABI class: X.Org XInput driver, version 20.0
[    18.239] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.239] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.239] (**) Option "Device" "/dev/input/event4"
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 85)
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 94)
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    18.240] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.240] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.240] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event4"
[    18.240] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    18.240] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.240] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    18.240] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    18.240] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.241] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.241] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.241] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.241] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.241] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.241] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"



```

---

### Post by Yellow Pasque on 2015-02-07
I don't see anything out of the ordinary in the logs. About the only idea I's have is to try disabling SwapBuffersWait. You probably don't have an /etc/X11/xorg.conf file, but you can create one that looks like this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Option "SwapBuffersWait" false
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by fedbriz91 on 2015-02-15
> **Temüjin said:**
> I don't see anything out of the ordinary in the logs. About the only idea I's have is to try disabling SwapBuffersWait. You probably don't have an /etc/X11/xorg.conf file, but you can create one that looks like this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Option "SwapBuffersWait" false
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

mmmh yeah !
 now is a bit improved. now i have 70 fps.... can i disabling something else to improve more than now ?

---

### Post by Yellow Pasque on 2015-02-15
I don't know any other magic incantations. It's a long shot, but you could try the 'nomodeset' paramater to turn off KMS. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

