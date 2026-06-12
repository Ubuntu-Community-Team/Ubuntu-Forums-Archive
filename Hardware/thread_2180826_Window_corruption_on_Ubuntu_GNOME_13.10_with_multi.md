---
title: "Window corruption on Ubuntu GNOME 13.10 with multiple Radeon GPU's installed"
date: 2013-10-14
forum: Hardware
---

### Post by CalcProgrammer1 on 2013-10-14
I've got a very confusing problem.  I installed the latest Ubuntu GNOME 13.10 distribution on my desktop as I had previously done on my laptop.  I'm experiencing some issues on the laptop so I wanted to see how it was "supposed" to work by running it on hardware I thought would work.  Nope.  It's happening on the desktop as well.

To start, I first installed it on my laptop:

AMD A10-4600 APU with Radeon HD 7660G (r600) integrated GPU
AMD Radeon HD 7730M (radeonsi) discrete GPU
Single built-in 1080p display connected via LVDS to integrated GPU

I installed glamor (xserver-xorg-glamoregl) and added xorg.conf.d configs to enable glamor acceleration instead of EXA so I could theoretically use DRI PRIME to render games on the 7730M GPU.  At that time the Ubuntu 13.10 repos didn't have glamor support enabled in the xserver-xorg-video-ati/radeon package so I built it from source with that enabled.  The result after installing it was both cards initialized and I was presented with an output sorta like this:

[http://i.imgur.com/tp3Lw2H.jpg](http://i.imgur.com/tp3Lw2H.jpg)

That pic is from my desktop, but my laptop did the same thing.  Then, to try to fix this I reverted all my laptop's packages to Ubuntu repository defaults.  Now the desktop looks fine but the 7730M GPU fails to initialize according to Xorg.0.log and trying to use DRI_PRIME=1 causes an instant X crash.  Anyways, that prompted me to test it out on my desktop, so I installed the same copy of Ubuntu GNOME 13.10 and ran updates so it has the latest packages.

Desktop:

Intel Core i7 930
Radeon HD 5870 (r600) 1GB
Radeon HD 5870 (r600) 2GB Eyefinity x6 edition
3x 1080p display connected to the first 5870

I had been using Debian unstable on this machine just fine, with the second Radeon not in use.  Upon installing Ubuntu GNOME 13.10 I had the same corruption I experienced on my laptop.  I proceeded to copy my xorg.conf.d settings over to enable glamor but the same corruption happens on glamor as well as exa methods.  I tried unplugging two monitors to just have one display, but that doesn't affect anything.  The graphical glitch only seems to affect the window contents - the GNOME UI elements (including full-screen GNOME shell menu) all render smoothly and correctly, as does glxgears' 3D window.  All the 2D parts of windows are absolutely corrupted, appearing to just be blocks of textures that exist somewhere in the card's VRAM (like in that screenshot Firefox is just a mangled version of the desktop background).  Now I looked at the xorg.log and both cards appear to be initializing correctly with glamor and r600.  I noticed that this parallels my laptop's problem in that having two GPU's initialized caused the screen to corrupt, so I tested by physically removing the second GPU card.  Doing so fixes the problem, it boots up and all the textures and windows render correctly.  I tried putting the second card back in and attaching a monitor to it, but that simply causes the corruption on the first card's monitor while the second card's monitor stays on with a black screen.  I presume this is why my laptop is working, that because updating the packages causes the 7730M to not initialize properly the second GPU doesn't exist to cause corruption anymore.

Has anyone seen this issue before?  From my limited amount of testing it appears to occur on machines with two AMD GPU's installed, regardless of monitor count.  If a GPU fails to initialize it doesn't count towards the issue.  If anyone else has multiple AMD cards in their laptop or desktop and runs 13.10, see if you get the same corruption.  It happens for sure on GNOME Shell and appears to affect GNOME fallback/flashback as well in that I got absolutely no screen update loading the non-composited fallback interface.  Clicking around I could tell that the interface was up as I could cause HDD activity clicking where apps would be in the menu, but the screen was frozen other than the cursor on the GDM background screen.

---

### Post by CalcProgrammer1 on 2013-10-15
Ok, more problems!  I reinstalled Ubuntu GNOME 13.10 on my laptop for a fresh copy of everything, which booted up normally to desktop but the 7730M card failed to initialize.  I did an update/dist-upgrade and then restarted gdm.  Now it looks like GLAMOR is being used automatically and radeonsi is detected but X segfaults immediately.  The xorg logs aren't too descriptive about the issue but a curious message appears if I run startx by hand and watch it crash:

```
r600: Unknown chipset 0x9900
```

That chipset ID shows up when it first initializes the card

```
[ 2200.372] (--) RADEON(0): Chipset: "ARUBA" (ChipID = 0x9900)
```

So it thinks the 7660G is an unknown chipset?  wat?....

...

Ok, just did a bit more and figured out that that message is caused by the ARUBA chip autodetecting EXA while the VERDE (7730M radeonsi) chip autodetected glamor.  Apparently mixing the two is bad.  I added a xorg.conf.d entry to force AccelMethod to glamor and now gdm loads.  BUT!  Now the 7730M fails to initialize!  What is going on!?!?!  Can glamor not work simultaneously on two separate dri drivers?  If I don't force glamor the 7660G takes exa and the 7730M takes glamor but it segfaults X, but if I do force glamor the 7660G takes glamor and the 7730M doesn't initialize at all.  Neither lets me use DRI PRIME.  What am I missing!???!??????

Xorg log from first case (not forcing glamor, causes X to segfault):

```

[  2666.684] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[  2666.684] X Protocol Version 11, Revision 0
[  2666.684] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  2666.685] Current Operating System: Linux Adam-dv6z-7000 3.11.0-7-generic #14-Ubuntu SMP Mon Sep 16 18:37:27 UTC 2013 x86_64
[  2666.685] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-7-generic root=UUID=597817be-e352-42d2-9b29-dc62ae89ee6a ro quiet splash vt.handoff=7
[  2666.685] Build Date: 03 October 2013  03:20:13PM
[  2666.685] xorg-server 2:1.14.3-3ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[  2666.685] Current version of pixman: 0.30.2
[  2666.686] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  2666.686] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2666.686] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 14 23:34:53 2013
[  2666.687] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2666.688] (==) No Layout section.  Using the first Screen section.
[  2666.688] (==) No screen section available. Using defaults.
[  2666.688] (**) |-->Screen "Default Screen Section" (0)
[  2666.688] (**) |   |-->Monitor "<default monitor>"
[  2666.689] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  2666.689] (==) Automatically adding devices
[  2666.689] (==) Automatically enabling devices
[  2666.689] (==) Automatically adding GPU devices
[  2666.689] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2666.689] 	Entry deleted from font path.
[  2666.689] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2666.689] 	Entry deleted from font path.
[  2666.689] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2666.689] 	Entry deleted from font path.
[  2666.689] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2666.689] 	Entry deleted from font path.
[  2666.689] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2666.689] 	Entry deleted from font path.
[  2666.689] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  2666.689] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2666.689] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2666.689] (II) Loader magic: 0x7f4264d42d20
[  2666.689] (II) Module ABI versions:
[  2666.689] 	X.Org ANSI C Emulation: 0.4
[  2666.689] 	X.Org Video Driver: 14.1
[  2666.690] 	X.Org XInput driver : 19.1
[  2666.690] 	X.Org Server Extension : 7.0
[  2666.690] (II) xfree86: Adding drm device (/dev/dri/card0)
[  2666.691] (II) xfree86: Adding drm device (/dev/dri/card1)
[  2666.695] (--) PCI:*(0:0:1:0) 1002:9900:103c:1831 rev 0, Mem @ 0xd0000000/268435456, 0xf0400000/262144, I/O @ 0x00004000/256
[  2666.695] (--) PCI: (0:1:0:0) 1002:682f:103c:1831 rev 0, Mem @ 0xe0000000/268435456, 0xf0300000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[  2666.696] (II) Open ACPI successful (/var/run/acpid.socket)
[  2666.696] Initializing built-in extension Generic Event Extension
[  2666.696] Initializing built-in extension SHAPE
[  2666.696] Initializing built-in extension MIT-SHM
[  2666.696] Initializing built-in extension XInputExtension
[  2666.696] Initializing built-in extension XTEST
[  2666.697] Initializing built-in extension BIG-REQUESTS
[  2666.697] Initializing built-in extension SYNC
[  2666.697] Initializing built-in extension XKEYBOARD
[  2666.697] Initializing built-in extension XC-MISC
[  2666.697] Initializing built-in extension SECURITY
[  2666.697] Initializing built-in extension XINERAMA
[  2666.697] Initializing built-in extension XFIXES
[  2666.697] Initializing built-in extension RENDER
[  2666.697] Initializing built-in extension RANDR
[  2666.698] Initializing built-in extension COMPOSITE
[  2666.698] Initializing built-in extension DAMAGE
[  2666.698] Initializing built-in extension MIT-SCREEN-SAVER
[  2666.698] Initializing built-in extension DOUBLE-BUFFER
[  2666.698] Initializing built-in extension RECORD
[  2666.698] Initializing built-in extension DPMS
[  2666.698] Initializing built-in extension X-Resource
[  2666.698] Initializing built-in extension XVideo
[  2666.698] Initializing built-in extension XVideo-MotionCompensation
[  2666.698] Initializing built-in extension SELinux
[  2666.699] Initializing built-in extension XFree86-VidModeExtension
[  2666.699] Initializing built-in extension XFree86-DGA
[  2666.699] Initializing built-in extension XFree86-DRI
[  2666.699] Initializing built-in extension DRI2
[  2666.699] (II) "glx" will be loaded by default.
[  2666.699] (WW) "xmir" is not to be loaded by default. Skipping.
[  2666.699] (II) LoadModule: "dri2"
[  2666.699] (II) Module "dri2" already built-in
[  2666.699] (II) LoadModule: "glamoregl"
[  2666.700] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  2666.705] (II) Module glamoregl: vendor="X.Org Foundation"
[  2666.705] 	compiled for 1.14.2.901, module version = 0.5.1
[  2666.705] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2666.705] (II) LoadModule: "glx"
[  2666.705] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2666.706] (II) Module glx: vendor="X.Org Foundation"
[  2666.706] 	compiled for 1.14.3, module version = 1.0.0
[  2666.706] 	ABI class: X.Org Server Extension, version 7.0
[  2666.706] (==) AIGLX enabled
[  2666.706] Loading extension GLX
[  2666.706] (==) Matched fglrx as autoconfigured driver 0
[  2666.706] (==) Matched ati as autoconfigured driver 1
[  2666.706] (==) Matched fglrx as autoconfigured driver 2
[  2666.706] (==) Matched ati as autoconfigured driver 3
[  2666.706] (==) Matched fglrx as autoconfigured driver 4
[  2666.706] (==) Matched ati as autoconfigured driver 5
[  2666.706] (==) Matched vesa as autoconfigured driver 6
[  2666.706] (==) Matched modesetting as autoconfigured driver 7
[  2666.706] (==) Matched fbdev as autoconfigured driver 8
[  2666.707] (==) Assigned the driver to the xf86ConfigLayout
[  2666.707] (II) LoadModule: "fglrx"
[  2666.708] (WW) Warning, couldn't open module fglrx
[  2666.708] (II) UnloadModule: "fglrx"
[  2666.708] (II) Unloading fglrx
[  2666.708] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  2666.708] (II) LoadModule: "ati"
[  2666.709] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2666.709] (II) Module ati: vendor="X.Org Foundation"
[  2666.709] 	compiled for 1.14.3, module version = 7.2.0
[  2666.709] 	Module class: X.Org Video Driver
[  2666.709] 	ABI class: X.Org Video Driver, version 14.1
[  2666.709] (II) LoadModule: "radeon"
[  2666.710] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  2666.711] (II) Module radeon: vendor="X.Org Foundation"
[  2666.711] 	compiled for 1.14.3, module version = 7.2.0
[  2666.711] 	Module class: X.Org Video Driver
[  2666.711] 	ABI class: X.Org Video Driver, version 14.1
[  2666.711] (II) LoadModule: "vesa"
[  2666.712] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2666.713] (II) Module vesa: vendor="X.Org Foundation"
[  2666.713] 	compiled for 1.14.1, module version = 2.3.2
[  2666.713] 	Module class: X.Org Video Driver
[  2666.713] 	ABI class: X.Org Video Driver, version 14.1
[  2666.713] (II) LoadModule: "modesetting"
[  2666.714] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  2666.714] (II) Module modesetting: vendor="X.Org Foundation"
[  2666.714] 	compiled for 1.14.1, module version = 0.8.0
[  2666.714] 	Module class: X.Org Video Driver
[  2666.714] 	ABI class: X.Org Video Driver, version 14.1
[  2666.714] (II) LoadModule: "fbdev"
[  2666.715] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2666.715] (II) Module fbdev: vendor="X.Org Foundation"
[  2666.715] 	compiled for 1.14.1, module version = 0.4.3
[  2666.715] 	Module class: X.Org Video Driver
[  2666.715] 	ABI class: X.Org Video Driver, version 14.1
[  2666.716] (==) Matched fglrx as autoconfigured driver 0
[  2666.716] (==) Matched ati as autoconfigured driver 1
[  2666.716] (==) Matched fglrx as autoconfigured driver 2
[  2666.716] (==) Matched ati as autoconfigured driver 3
[  2666.716] (==) Matched fglrx as autoconfigured driver 4
[  2666.716] (==) Matched ati as autoconfigured driver 5
[  2666.716] (==) Matched vesa as autoconfigured driver 6
[  2666.716] (==) Matched modesetting as autoconfigured driver 7
[  2666.716] (==) Matched fbdev as autoconfigured driver 8
[  2666.716] (==) Assigned the driver to the xf86ConfigLayout
[  2666.716] (II) LoadModule: "fglrx"
[  2666.717] (WW) Warning, couldn't open module fglrx
[  2666.717] (II) UnloadModule: "fglrx"
[  2666.718] (II) Unloading fglrx
[  2666.718] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  2666.718] (II) LoadModule: "ati"
[  2666.718] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2666.718] (II) Module ati: vendor="X.Org Foundation"
[  2666.718] 	compiled for 1.14.3, module version = 7.2.0
[  2666.719] 	Module class: X.Org Video Driver
[  2666.719] 	ABI class: X.Org Video Driver, version 14.1
[  2666.719] (II) LoadModule: "vesa"
[  2666.720] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2666.720] (II) Module vesa: vendor="X.Org Foundation"
[  2666.720] 	compiled for 1.14.1, module version = 2.3.2
[  2666.720] 	Module class: X.Org Video Driver
[  2666.720] 	ABI class: X.Org Video Driver, version 14.1
[  2666.720] (II) UnloadModule: "vesa"
[  2666.720] (II) Unloading vesa
[  2666.720] (II) Failed to load module "vesa" (already loaded, 0)
[  2666.720] (II) LoadModule: "modesetting"
[  2666.721] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  2666.721] (II) Module modesetting: vendor="X.Org Foundation"
[  2666.721] 	compiled for 1.14.1, module version = 0.8.0
[  2666.721] 	Module class: X.Org Video Driver
[  2666.721] 	ABI class: X.Org Video Driver, version 14.1
[  2666.721] (II) UnloadModule: "modesetting"
[  2666.721] (II) Unloading modesetting
[  2666.721] (II) Failed to load module "modesetting" (already loaded, 0)
[  2666.721] (II) LoadModule: "fbdev"
[  2666.722] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2666.722] (II) Module fbdev: vendor="X.Org Foundation"
[  2666.722] 	compiled for 1.14.1, module version = 0.4.3
[  2666.722] 	Module class: X.Org Video Driver
[  2666.722] 	ABI class: X.Org Video Driver, version 14.1
[  2666.722] (II) UnloadModule: "fbdev"
[  2666.722] (II) Unloading fbdev
[  2666.722] (II) Failed to load module "fbdev" (already loaded, 0)
[  2666.722] (II) RADEON: Driver for ATI Radeon chipsets:
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
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
	KABINI, KABINI, KABINI
[  2666.751] (II) VESA: driver for VESA chipsets: vesa
[  2666.751] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  2666.751] (II) FBDEV: driver for framebuffer: fbdev
[  2666.751] (--) using VT number 7

[  2666.769] (II) [KMS] Kernel modesetting enabled.
[  2666.769] (II) [KMS] Kernel modesetting enabled.
[  2666.769] (WW) Falling back to old probe method for vesa
[  2666.769] (WW) Falling back to old probe method for modesetting
[  2666.769] (WW) Falling back to old probe method for fbdev
[  2666.769] (II) Loading sub module "fbdevhw"
[  2666.769] (II) LoadModule: "fbdevhw"
[  2666.770] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  2666.770] (II) Module fbdevhw: vendor="X.Org Foundation"
[  2666.770] 	compiled for 1.14.3, module version = 0.0.2
[  2666.770] 	ABI class: X.Org Video Driver, version 14.1
[  2666.771] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  2666.771] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  2666.771] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  2666.771] (==) RADEON(0): Default visual is TrueColor
[  2666.771] (==) RADEON(0): RGB weight 888
[  2666.771] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  2666.771] (--) RADEON(0): Chipset: "ARUBA" (ChipID = 0x9900)
[  2666.771] (II) Loading sub module "dri2"
[  2666.771] (II) LoadModule: "dri2"
[  2666.771] (II) Module "dri2" already built-in
[  2666.771] (II) Loading sub module "exa"
[  2666.771] (II) LoadModule: "exa"
[  2666.772] (II) Loading /usr/lib/xorg/modules/libexa.so
[  2666.772] (II) Module exa: vendor="X.Org Foundation"
[  2666.772] 	compiled for 1.14.3, module version = 2.6.0
[  2666.772] 	ABI class: X.Org Video Driver, version 14.1
[  2666.772] (II) RADEON(0): KMS Color Tiling: enabled
[  2666.772] (II) RADEON(0): KMS Color Tiling 2D: enabled
[  2666.772] (II) RADEON(0): KMS Pageflipping: enabled
[  2666.772] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  2666.815] (II) RADEON(0): Output LVDS has no monitor section
[  2666.991] (II) RADEON(0): Output VGA-0 has no monitor section
[  2666.993] (II) RADEON(0): Output HDMI-0 has no monitor section
[  2667.036] (II) RADEON(0): EDID for output LVDS
[  2667.036] (II) RADEON(0): Manufacturer: LGD  Model: 37f  Serial#: 0
[  2667.036] (II) RADEON(0): Year: 2011  Week: 0
[  2667.036] (II) RADEON(0): EDID Version: 1.4
[  2667.036] (II) RADEON(0): Digital Display Input
[  2667.036] (II) RADEON(0): 6 bits per channel
[  2667.036] (II) RADEON(0): Digital interface is undefined
[  2667.036] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[  2667.037] (II) RADEON(0): Gamma: 2.20
[  2667.037] (II) RADEON(0): No DPMS capabilities specified
[  2667.037] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[  2667.037] (II) RADEON(0): First detailed timing is preferred mode
[  2667.037] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[  2667.037] (II) RADEON(0): redX: 0.629 redY: 0.350   greenX: 0.349 greenY: 0.614
[  2667.037] (II) RADEON(0): blueX: 0.154 blueY: 0.112   whiteX: 0.313 whiteY: 0.329
[  2667.037] (II) RADEON(0): Manufacturer's mask: 0
[  2667.037] (II) RADEON(0): Supported detailed timing:
[  2667.037] (II) RADEON(0): clock: 149.0 MHz   Image Size:  344 x 194 mm
[  2667.037] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2040 h_blank_end 2208 h_border: 0
[  2667.037] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1124 v_border: 0
[  2667.037] (II) RADEON(0): Supported detailed timing:
[  2667.037] (II) RADEON(0): clock: 99.3 MHz   Image Size:  344 x 194 mm
[  2667.037] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2040 h_blank_end 2208 h_border: 0
[  2667.037] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1124 v_border: 0
[  2667.037] (II) RADEON(0): Unknown vendor-specific block 2
[  2667.037] (II) RADEON(0): EDID (in hex):
[  2667.037] (II) RADEON(0): 	00ffffffffffff0030e47f0300000000
[  2667.037] (II) RADEON(0): 	00150104902213780225b5a159599d27
[  2667.037] (II) RADEON(0): 	1c505400000001010101010101010101
[  2667.038] (II) RADEON(0): 	010101010101343a802071382c403048
[  2667.038] (II) RADEON(0): 	350058c210000018cd26802071382c40
[  2667.038] (II) RADEON(0): 	3048350058c210000018000000000000
[  2667.038] (II) RADEON(0): 	00000000000000000000000000000002
[  2667.038] (II) RADEON(0): 	000a3dff0a3c7d261d387d00000000aa
[  2667.038] (II) RADEON(0): Printing probed modes for output LVDS
[  2667.038] (II) RADEON(0): Modeline "1920x1080"x60.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  2667.038] (II) RADEON(0): Modeline "1920x1080"x40.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  2667.038] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  2667.038] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[  2667.038] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[  2667.038] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  2667.038] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[  2667.038] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[  2667.038] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  2667.038] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[  2667.038] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[  2667.038] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[  2667.038] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[  2667.038] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[  2667.038] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[  2667.038] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[  2667.211] (II) RADEON(0): EDID for output VGA-0
[  2667.213] (II) RADEON(0): EDID for output HDMI-0
[  2667.213] (II) RADEON(0): Output LVDS connected
[  2667.213] (II) RADEON(0): Output VGA-0 disconnected
[  2667.213] (II) RADEON(0): Output HDMI-0 disconnected
[  2667.213] (II) RADEON(0): Using exact sizes for initial modes
[  2667.213] (II) RADEON(0): Output LVDS using initial mode 1920x1080
[  2667.213] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  2667.214] (II) RADEON(0): mem size init: gart size :1fdde000 vram size: s:20000000 visible:1f7d7000
[  2667.214] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  2667.214] (==) RADEON(0): DPI set to (96, 96)
[  2667.214] (II) Loading sub module "fb"
[  2667.214] (II) LoadModule: "fb"
[  2667.214] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2667.215] (II) Module fb: vendor="X.Org Foundation"
[  2667.215] 	compiled for 1.14.3, module version = 1.0.0
[  2667.215] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2667.215] (II) Loading sub module "ramdac"
[  2667.215] (II) LoadModule: "ramdac"
[  2667.215] (II) Module "ramdac" already built-in
[  2667.215] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[  2667.215] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  2667.215] (==) RADEON(G0): Default visual is TrueColor
[  2667.215] (==) RADEON(G0): RGB weight 888
[  2667.215] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[  2667.215] (--) RADEON(G0): Chipset: "VERDE" (ChipID = 0x682f)
[  2667.216] (II) Loading sub module "dri2"
[  2667.216] (II) LoadModule: "dri2"
[  2667.216] (II) Module "dri2" already built-in
[  2667.216] (II) Loading sub module "glamoregl"
[  2667.216] (II) LoadModule: "glamoregl"
[  2667.216] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  2667.216] (II) Module glamoregl: vendor="X.Org Foundation"
[  2667.217] 	compiled for 1.14.2.901, module version = 0.5.1
[  2667.217] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2667.217] (II) glamor: OpenGL accelerated X.org driver based.
[  2667.275] (II) glamor: EGL version 1.4 (DRI2):
[  2667.319] (II) RADEON(G0): glamor detected, initialising EGL layer.
[  2667.319] (II) RADEON(G0): KMS Color Tiling: disabled
[  2667.319] (II) RADEON(G0): KMS Color Tiling 2D: disabled
[  2667.319] (II) RADEON(G0): KMS Pageflipping: enabled
[  2667.319] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[  2667.320] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  2667.320] (II) RADEON(G0): mem size init: gart size :1fbde000 vram size: s:80000000 visible:7fcc0000
[  2667.320] (==) RADEON(G0): DPI set to (96, 96)
[  2667.320] (II) Loading sub module "fb"
[  2667.320] (II) LoadModule: "fb"
[  2667.320] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2667.320] (II) Module fb: vendor="X.Org Foundation"
[  2667.320] 	compiled for 1.14.3, module version = 1.0.0
[  2667.321] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  2667.321] (II) Loading sub module "ramdac"
[  2667.321] (II) LoadModule: "ramdac"
[  2667.321] (II) Module "ramdac" already built-in
[  2667.321] (II) UnloadModule: "vesa"
[  2667.321] (II) Unloading vesa
[  2667.321] (II) UnloadModule: "modesetting"
[  2667.321] (II) Unloading modesetting
[  2667.321] (II) UnloadModule: "fbdev"
[  2667.321] (II) Unloading fbdev
[  2667.321] (II) UnloadSubModule: "fbdevhw"
[  2667.321] (II) Unloading fbdevhw
[  2667.322] (--) Depth 24 pixmap format is 32 bpp
[  2667.322] (II) RADEON(G0): [DRI2] Setup complete
[  2667.322] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[  2667.322] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[  2667.322] (II) RADEON(G0): Front buffer size: 3072K
[  2667.322] (II) RADEON(G0): VRAM usage limit set to 1881590K
[  2667.323] (==) RADEON(G0): Backing store disabled
[  2667.323] (II) RADEON(G0): Direct rendering enabled
[  2667.708] (II) RADEON(G0): Use GLAMOR acceleration.
[  2667.708] (II) RADEON(G0): Acceleration enabled
[  2667.708] (==) RADEON(G0): DPMS enabled
[  2667.708] (==) RADEON(G0): Silken mouse enabled
[  2667.708] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  2667.709] (II) RADEON(0): [DRI2] Setup complete
[  2667.709] (II) RADEON(0): [DRI2]   DRI driver: r600
[  2667.709] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[  2667.709] (II) RADEON(0): Front buffer size: 8160K
[  2667.709] (II) RADEON(0): VRAM usage limit set to 456937K
[  2667.709] (==) RADEON(0): Backing store disabled
[  2667.709] (II) RADEON(0): Direct rendering enabled
[  2667.709] (II) EXA(0): Driver allocated offscreen pixmaps
[  2667.710] (II) EXA(0): Driver registered support for the following operations:
[  2667.710] (II)         Solid
[  2667.710] (II)         Copy
[  2667.710] (II)         Composite (RENDER acceleration)
[  2667.710] (II)         UploadToScreen
[  2667.710] (II)         DownloadFromScreen
[  2667.710] (II) RADEON(0): Acceleration enabled
[  2667.710] (==) RADEON(0): DPMS enabled
[  2667.710] (==) RADEON(0): Silken mouse enabled
[  2667.710] (II) RADEON(0): Set up textured video
[  2667.710] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  2667.710] (II) RADEON(0): [XvMC] Extension initialized.
[  2667.710] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  2667.711] (--) RandR disabled
[  2667.731] (II) SELinux: Disabled on system
[  2667.736] (EE) AIGLX error: Calling driver entry point failed
[  2667.736] (EE) AIGLX: reverting to software rendering
[  2667.736] (II) AIGLX: Screen 0 is not DRI capable
[  2667.737] (EE) 
[  2667.737] (EE) Backtrace:
[  2667.738] (EE) 0: /usr/bin/X (xorg_backtrace+0x3d) [0x7f4264ac202d]
[  2667.738] (EE) 1: /usr/bin/X (0x7f4264920000+0x1a5d99) [0x7f4264ac5d99]
[  2667.738] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f4263a00000+0xfbb0) [0x7f4263a0fbb0]
[  2667.738] (EE) 3: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (radeon_drm_winsys_create+0xb9) [0x7f425d44f579]
[  2667.738] (EE) 4: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (0x7f425d428000+0x9b79) [0x7f425d431b79]
[  2667.738] (EE) 5: /usr/lib/x86_64-linux-gnu/dri/radeonsi_dri.so (0x7f425d428000+0x22a02) [0x7f425d44aa02]
[  2667.739] (EE) 6: /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so (0x7f425e068000+0xd1bd) [0x7f425e0751bd]
[  2667.739] (EE) 7: /usr/lib/xorg/modules/extensions/libglx.so (0x7f425e960000+0x3ba11) [0x7f425e99ba11]
[  2667.739] (EE) 8: /usr/lib/xorg/modules/extensions/libglx.so (0x7f425e960000+0x3b00a) [0x7f425e99b00a]
[  2667.739] (EE) 9: /usr/bin/X (InitExtensions+0x41) [0x7f42649e6341]
[  2667.739] (EE) 10: /usr/bin/X (0x7f4264920000+0x443a0) [0x7f42649643a0]
[  2667.739] (EE) 11: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f4262621de5]
[  2667.740] (EE) 12: /usr/bin/X (0x7f4264920000+0x448af) [0x7f42649648af]
[  2667.740] (EE) 
[  2667.740] (EE) Segmentation fault at address 0x0
[  2667.740] (EE) 
Fatal server error:
[  2667.740] (EE) Caught signal 11 (Segmentation fault). Server aborting
[  2667.740] (EE) 
[  2667.740] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  2667.741] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2667.741] (EE) 
[  2667.811] (EE) Server terminated with error (1). Closing log file.

```

Xorg log from second case (forcing glamor, causes 7730M to not initialize):

```

[  3109.827] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[  3109.827] X Protocol Version 11, Revision 0
[  3109.828] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[  3109.828] Current Operating System: Linux Adam-dv6z-7000 3.11.0-7-generic #14-Ubuntu SMP Mon Sep 16 18:37:27 UTC 2013 x86_64
[  3109.828] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-7-generic root=UUID=597817be-e352-42d2-9b29-dc62ae89ee6a ro quiet splash vt.handoff=7
[  3109.828] Build Date: 03 October 2013  03:20:13PM
[  3109.828] xorg-server 2:1.14.3-3ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[  3109.828] Current version of pixman: 0.30.2
[  3109.828] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  3109.828] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3109.828] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 14 23:42:16 2013
[  3109.829] (==) Using config directory: "/etc/X11/xorg.conf.d"
[  3109.829] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3109.830] (==) No Layout section.  Using the first Screen section.
[  3109.830] (==) No screen section available. Using defaults.
[  3109.830] (**) |-->Screen "Default Screen Section" (0)
[  3109.830] (**) |   |-->Monitor "<default monitor>"
[  3109.831] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[  3109.831] (**) |   |-->Device "Radeon"
[  3109.831] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  3109.831] (==) Automatically adding devices
[  3109.831] (==) Automatically enabling devices
[  3109.831] (==) Automatically adding GPU devices
[  3109.831] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3109.831] 	Entry deleted from font path.
[  3109.831] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3109.831] 	Entry deleted from font path.
[  3109.831] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3109.831] 	Entry deleted from font path.
[  3109.831] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3109.831] 	Entry deleted from font path.
[  3109.831] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3109.832] 	Entry deleted from font path.
[  3109.832] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[  3109.832] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  3109.832] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3109.832] (II) Loader magic: 0x7f9c69a32d20
[  3109.832] (II) Module ABI versions:
[  3109.832] 	X.Org ANSI C Emulation: 0.4
[  3109.832] 	X.Org Video Driver: 14.1
[  3109.832] 	X.Org XInput driver : 19.1
[  3109.832] 	X.Org Server Extension : 7.0
[  3109.833] (II) xfree86: Adding drm device (/dev/dri/card0)
[  3109.833] (II) xfree86: Adding drm device (/dev/dri/card1)
[  3109.838] (--) PCI:*(0:0:1:0) 1002:9900:103c:1831 rev 0, Mem @ 0xd0000000/268435456, 0xf0400000/262144, I/O @ 0x00004000/256
[  3109.838] (--) PCI: (0:1:0:0) 1002:682f:103c:1831 rev 0, Mem @ 0xe0000000/268435456, 0xf0300000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[  3109.839] (II) Open ACPI successful (/var/run/acpid.socket)
[  3109.839] Initializing built-in extension Generic Event Extension
[  3109.839] Initializing built-in extension SHAPE
[  3109.839] Initializing built-in extension MIT-SHM
[  3109.839] Initializing built-in extension XInputExtension
[  3109.839] Initializing built-in extension XTEST
[  3109.839] Initializing built-in extension BIG-REQUESTS
[  3109.839] Initializing built-in extension SYNC
[  3109.839] Initializing built-in extension XKEYBOARD
[  3109.839] Initializing built-in extension XC-MISC
[  3109.839] Initializing built-in extension SECURITY
[  3109.839] Initializing built-in extension XINERAMA
[  3109.840] Initializing built-in extension XFIXES
[  3109.840] Initializing built-in extension RENDER
[  3109.840] Initializing built-in extension RANDR
[  3109.840] Initializing built-in extension COMPOSITE
[  3109.840] Initializing built-in extension DAMAGE
[  3109.840] Initializing built-in extension MIT-SCREEN-SAVER
[  3109.840] Initializing built-in extension DOUBLE-BUFFER
[  3109.840] Initializing built-in extension RECORD
[  3109.840] Initializing built-in extension DPMS
[  3109.840] Initializing built-in extension X-Resource
[  3109.840] Initializing built-in extension XVideo
[  3109.840] Initializing built-in extension XVideo-MotionCompensation
[  3109.840] Initializing built-in extension SELinux
[  3109.840] Initializing built-in extension XFree86-VidModeExtension
[  3109.840] Initializing built-in extension XFree86-DGA
[  3109.840] Initializing built-in extension XFree86-DRI
[  3109.840] Initializing built-in extension DRI2
[  3109.840] (II) "glx" will be loaded by default.
[  3109.840] (WW) "xmir" is not to be loaded by default. Skipping.
[  3109.840] (II) LoadModule: "dri2"
[  3109.841] (II) Module "dri2" already built-in
[  3109.841] (II) LoadModule: "glamoregl"
[  3109.842] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  3109.846] (II) Module glamoregl: vendor="X.Org Foundation"
[  3109.847] 	compiled for 1.14.2.901, module version = 0.5.1
[  3109.847] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3109.847] (II) LoadModule: "glx"
[  3109.847] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3109.848] (II) Module glx: vendor="X.Org Foundation"
[  3109.848] 	compiled for 1.14.3, module version = 1.0.0
[  3109.848] 	ABI class: X.Org Server Extension, version 7.0
[  3109.848] (==) AIGLX enabled
[  3109.848] Loading extension GLX
[  3109.848] (==) Matched fglrx as autoconfigured driver 0
[  3109.848] (==) Matched ati as autoconfigured driver 1
[  3109.848] (==) Matched fglrx as autoconfigured driver 2
[  3109.848] (==) Matched ati as autoconfigured driver 3
[  3109.848] (==) Matched fglrx as autoconfigured driver 4
[  3109.848] (==) Matched ati as autoconfigured driver 5
[  3109.849] (==) Matched vesa as autoconfigured driver 6
[  3109.849] (==) Matched modesetting as autoconfigured driver 7
[  3109.849] (==) Matched fbdev as autoconfigured driver 8
[  3109.849] (==) Assigned the driver to the xf86ConfigLayout
[  3109.849] (II) LoadModule: "fglrx"
[  3109.850] (WW) Warning, couldn't open module fglrx
[  3109.851] (II) UnloadModule: "fglrx"
[  3109.851] (II) Unloading fglrx
[  3109.851] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  3109.851] (II) LoadModule: "ati"
[  3109.852] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  3109.852] (II) Module ati: vendor="X.Org Foundation"
[  3109.852] 	compiled for 1.14.3, module version = 7.2.0
[  3109.852] 	Module class: X.Org Video Driver
[  3109.852] 	ABI class: X.Org Video Driver, version 14.1
[  3109.852] (II) LoadModule: "radeon"
[  3109.853] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  3109.854] (II) Module radeon: vendor="X.Org Foundation"
[  3109.854] 	compiled for 1.14.3, module version = 7.2.0
[  3109.854] 	Module class: X.Org Video Driver
[  3109.854] 	ABI class: X.Org Video Driver, version 14.1
[  3109.854] (II) LoadModule: "vesa"
[  3109.855] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3109.856] (II) Module vesa: vendor="X.Org Foundation"
[  3109.856] 	compiled for 1.14.1, module version = 2.3.2
[  3109.856] 	Module class: X.Org Video Driver
[  3109.856] 	ABI class: X.Org Video Driver, version 14.1
[  3109.856] (II) LoadModule: "modesetting"
[  3109.857] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3109.857] (II) Module modesetting: vendor="X.Org Foundation"
[  3109.857] 	compiled for 1.14.1, module version = 0.8.0
[  3109.857] 	Module class: X.Org Video Driver
[  3109.857] 	ABI class: X.Org Video Driver, version 14.1
[  3109.857] (II) LoadModule: "fbdev"
[  3109.858] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3109.859] (II) Module fbdev: vendor="X.Org Foundation"
[  3109.859] 	compiled for 1.14.1, module version = 0.4.3
[  3109.859] 	Module class: X.Org Video Driver
[  3109.859] 	ABI class: X.Org Video Driver, version 14.1
[  3109.859] (==) Matched fglrx as autoconfigured driver 0
[  3109.859] (==) Matched ati as autoconfigured driver 1
[  3109.859] (==) Matched fglrx as autoconfigured driver 2
[  3109.859] (==) Matched ati as autoconfigured driver 3
[  3109.859] (==) Matched fglrx as autoconfigured driver 4
[  3109.859] (==) Matched ati as autoconfigured driver 5
[  3109.859] (==) Matched vesa as autoconfigured driver 6
[  3109.859] (==) Matched modesetting as autoconfigured driver 7
[  3109.859] (==) Matched fbdev as autoconfigured driver 8
[  3109.859] (==) Assigned the driver to the xf86ConfigLayout
[  3109.859] (II) LoadModule: "fglrx"
[  3109.861] (WW) Warning, couldn't open module fglrx
[  3109.861] (II) UnloadModule: "fglrx"
[  3109.861] (II) Unloading fglrx
[  3109.861] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  3109.861] (II) LoadModule: "ati"
[  3109.862] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  3109.862] (II) Module ati: vendor="X.Org Foundation"
[  3109.862] 	compiled for 1.14.3, module version = 7.2.0
[  3109.862] 	Module class: X.Org Video Driver
[  3109.862] 	ABI class: X.Org Video Driver, version 14.1
[  3109.862] (II) LoadModule: "vesa"
[  3109.863] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3109.863] (II) Module vesa: vendor="X.Org Foundation"
[  3109.863] 	compiled for 1.14.1, module version = 2.3.2
[  3109.863] 	Module class: X.Org Video Driver
[  3109.863] 	ABI class: X.Org Video Driver, version 14.1
[  3109.863] (II) UnloadModule: "vesa"
[  3109.864] (II) Unloading vesa
[  3109.864] (II) Failed to load module "vesa" (already loaded, 0)
[  3109.864] (II) LoadModule: "modesetting"
[  3109.865] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3109.865] (II) Module modesetting: vendor="X.Org Foundation"
[  3109.865] 	compiled for 1.14.1, module version = 0.8.0
[  3109.865] 	Module class: X.Org Video Driver
[  3109.865] 	ABI class: X.Org Video Driver, version 14.1
[  3109.865] (II) UnloadModule: "modesetting"
[  3109.865] (II) Unloading modesetting
[  3109.865] (II) Failed to load module "modesetting" (already loaded, 0)
[  3109.865] (II) LoadModule: "fbdev"
[  3109.866] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3109.866] (II) Module fbdev: vendor="X.Org Foundation"
[  3109.866] 	compiled for 1.14.1, module version = 0.4.3
[  3109.867] 	Module class: X.Org Video Driver
[  3109.867] 	ABI class: X.Org Video Driver, version 14.1
[  3109.867] (II) UnloadModule: "fbdev"
[  3109.867] (II) Unloading fbdev
[  3109.867] (II) Failed to load module "fbdev" (already loaded, 0)
[  3109.867] (II) RADEON: Driver for ATI Radeon chipsets:
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
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
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
	KABINI, KABINI, KABINI
[  3109.914] (II) VESA: driver for VESA chipsets: vesa
[  3109.914] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  3109.914] (II) FBDEV: driver for framebuffer: fbdev
[  3109.915] (++) using VT number 7

[  3109.932] (II) [KMS] Kernel modesetting enabled.
[  3109.933] (II) [KMS] Kernel modesetting enabled.
[  3109.933] (WW) Falling back to old probe method for vesa
[  3109.933] (WW) Falling back to old probe method for modesetting
[  3109.933] (WW) Falling back to old probe method for fbdev
[  3109.933] (II) Loading sub module "fbdevhw"
[  3109.933] (II) LoadModule: "fbdevhw"
[  3109.934] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3109.934] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3109.934] 	compiled for 1.14.3, module version = 0.0.2
[  3109.934] 	ABI class: X.Org Video Driver, version 14.1
[  3109.935] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  3109.935] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  3109.935] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  3109.935] (==) RADEON(0): Default visual is TrueColor
[  3109.935] (**) RADEON(0): Option "AccelMethod" "glamor"
[  3109.935] (==) RADEON(0): RGB weight 888
[  3109.935] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  3109.935] (--) RADEON(0): Chipset: "ARUBA" (ChipID = 0x9900)
[  3109.935] (II) Loading sub module "dri2"
[  3109.935] (II) LoadModule: "dri2"
[  3109.935] (II) Module "dri2" already built-in
[  3109.936] (II) Loading sub module "glamoregl"
[  3109.936] (II) LoadModule: "glamoregl"
[  3109.937] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  3109.937] (II) Module glamoregl: vendor="X.Org Foundation"
[  3109.937] 	compiled for 1.14.2.901, module version = 0.5.1
[  3109.937] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3109.937] (II) glamor: OpenGL accelerated X.org driver based.
[  3109.998] (II) glamor: EGL version 1.4 (DRI2):
[  3110.005] (II) RADEON(0): glamor detected, initialising EGL layer.
[  3110.005] (II) RADEON(0): KMS Color Tiling: enabled
[  3110.006] (II) RADEON(0): KMS Color Tiling 2D: enabled
[  3110.006] (II) RADEON(0): KMS Pageflipping: enabled
[  3110.006] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  3110.049] (II) RADEON(0): Output LVDS has no monitor section
[  3110.223] (II) RADEON(0): Output VGA-0 has no monitor section
[  3110.225] (II) RADEON(0): Output HDMI-0 has no monitor section
[  3110.268] (II) RADEON(0): EDID for output LVDS
[  3110.268] (II) RADEON(0): Manufacturer: LGD  Model: 37f  Serial#: 0
[  3110.268] (II) RADEON(0): Year: 2011  Week: 0
[  3110.268] (II) RADEON(0): EDID Version: 1.4
[  3110.268] (II) RADEON(0): Digital Display Input
[  3110.269] (II) RADEON(0): 6 bits per channel
[  3110.269] (II) RADEON(0): Digital interface is undefined
[  3110.269] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[  3110.269] (II) RADEON(0): Gamma: 2.20
[  3110.269] (II) RADEON(0): No DPMS capabilities specified
[  3110.269] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[  3110.269] (II) RADEON(0): First detailed timing is preferred mode
[  3110.269] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[  3110.269] (II) RADEON(0): redX: 0.629 redY: 0.350   greenX: 0.349 greenY: 0.614
[  3110.269] (II) RADEON(0): blueX: 0.154 blueY: 0.112   whiteX: 0.313 whiteY: 0.329
[  3110.269] (II) RADEON(0): Manufacturer's mask: 0
[  3110.269] (II) RADEON(0): Supported detailed timing:
[  3110.269] (II) RADEON(0): clock: 149.0 MHz   Image Size:  344 x 194 mm
[  3110.269] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2040 h_blank_end 2208 h_border: 0
[  3110.269] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1124 v_border: 0
[  3110.269] (II) RADEON(0): Supported detailed timing:
[  3110.270] (II) RADEON(0): clock: 99.3 MHz   Image Size:  344 x 194 mm
[  3110.270] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2040 h_blank_end 2208 h_border: 0
[  3110.270] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1124 v_border: 0
[  3110.270] (II) RADEON(0): Unknown vendor-specific block 2
[  3110.270] (II) RADEON(0): EDID (in hex):
[  3110.270] (II) RADEON(0): 	00ffffffffffff0030e47f0300000000
[  3110.270] (II) RADEON(0): 	00150104902213780225b5a159599d27
[  3110.270] (II) RADEON(0): 	1c505400000001010101010101010101
[  3110.270] (II) RADEON(0): 	010101010101343a802071382c403048
[  3110.270] (II) RADEON(0): 	350058c210000018cd26802071382c40
[  3110.270] (II) RADEON(0): 	3048350058c210000018000000000000
[  3110.270] (II) RADEON(0): 	00000000000000000000000000000002
[  3110.270] (II) RADEON(0): 	000a3dff0a3c7d261d387d00000000aa
[  3110.270] (II) RADEON(0): Printing probed modes for output LVDS
[  3110.270] (II) RADEON(0): Modeline "1920x1080"x60.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3110.270] (II) RADEON(0): Modeline "1920x1080"x40.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3110.271] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  3110.271] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[  3110.271] (II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[  3110.271] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  3110.271] (II) RADEON(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[  3110.271] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[  3110.271] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  3110.271] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[  3110.271] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[  3110.271] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[  3110.271] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[  3110.271] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[  3110.271] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[  3110.271] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[  3110.447] (II) RADEON(0): EDID for output VGA-0
[  3110.449] (II) RADEON(0): EDID for output HDMI-0
[  3110.449] (II) RADEON(0): Output LVDS connected
[  3110.449] (II) RADEON(0): Output VGA-0 disconnected
[  3110.449] (II) RADEON(0): Output HDMI-0 disconnected
[  3110.449] (II) RADEON(0): Using exact sizes for initial modes
[  3110.450] (II) RADEON(0): Output LVDS using initial mode 1920x1080
[  3110.450] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  3110.450] (II) RADEON(0): mem size init: gart size :1fdde000 vram size: s:20000000 visible:1f7d7000
[  3110.450] (==) RADEON(0): DPI set to (96, 96)
[  3110.450] (II) Loading sub module "fb"
[  3110.450] (II) LoadModule: "fb"
[  3110.451] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3110.451] (II) Module fb: vendor="X.Org Foundation"
[  3110.451] 	compiled for 1.14.3, module version = 1.0.0
[  3110.451] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3110.451] (II) Loading sub module "ramdac"
[  3110.451] (II) LoadModule: "ramdac"
[  3110.451] (II) Module "ramdac" already built-in
[  3110.451] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[  3110.451] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  3110.451] (==) RADEON(G0): Default visual is TrueColor
[  3110.452] (**) RADEON(G0): Option "AccelMethod" "glamor"
[  3110.452] (==) RADEON(G0): RGB weight 888
[  3110.452] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[  3110.452] (--) RADEON(G0): Chipset: "VERDE" (ChipID = 0x682f)
[  3110.452] (II) Loading sub module "dri2"
[  3110.452] (II) LoadModule: "dri2"
[  3110.452] (II) Module "dri2" already built-in
[  3110.452] (II) Loading sub module "glamoregl"
[  3110.452] (II) LoadModule: "glamoregl"
[  3110.453] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  3110.453] (II) Module glamoregl: vendor="X.Org Foundation"
[  3110.453] 	compiled for 1.14.2.901, module version = 0.5.1
[  3110.453] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3110.453] (II) glamor: OpenGL accelerated X.org driver based.
[  3110.458] (II) glamor: EGL version 1.4 (DRI2):
[  3110.459] (EE) RADEON(G0): Failed to create EGL context
[  3110.459] (EE) RADEON(G0): glamor detected, failed to initialize EGL.
[  3110.459] (II) Loading sub module "shadow"
[  3110.459] (II) LoadModule: "shadow"
[  3110.460] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  3110.460] (II) Module shadow: vendor="X.Org Foundation"
[  3110.460] 	compiled for 1.14.3, module version = 1.1.0
[  3110.460] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3110.460] (II) RADEON(G0): KMS Color Tiling: disabled
[  3110.460] (II) RADEON(G0): KMS Color Tiling 2D: disabled
[  3110.460] (II) RADEON(G0): KMS Pageflipping: enabled
[  3110.460] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[  3110.460] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  3110.460] (II) RADEON(G0): mem size init: gart size :1fbde000 vram size: s:80000000 visible:7fcc0000
[  3110.460] (II) RADEON(G0): EXA: Driver will allow EXA pixmaps in VRAM
[  3110.460] (==) RADEON(G0): DPI set to (96, 96)
[  3110.461] (II) Loading sub module "fb"
[  3110.461] (II) LoadModule: "fb"
[  3110.461] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3110.461] (II) Module fb: vendor="X.Org Foundation"
[  3110.461] 	compiled for 1.14.3, module version = 1.0.0
[  3110.461] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  3110.461] (II) Loading sub module "ramdac"
[  3110.461] (II) LoadModule: "ramdac"
[  3110.461] (II) Module "ramdac" already built-in
[  3110.461] (II) UnloadModule: "vesa"
[  3110.462] (II) Unloading vesa
[  3110.462] (II) UnloadModule: "modesetting"
[  3110.462] (II) Unloading modesetting
[  3110.462] (II) UnloadModule: "fbdev"
[  3110.462] (II) Unloading fbdev
[  3110.462] (II) UnloadSubModule: "fbdevhw"
[  3110.462] (II) Unloading fbdevhw
[  3110.462] (--) Depth 24 pixmap format is 32 bpp
[  3110.463] (II) RADEON(G0): Front buffer size: 3072K
[  3110.463] (II) RADEON(G0): VRAM usage limit set to 1881590K
[  3110.463] (==) RADEON(G0): Backing store disabled
[  3110.463] (WW) RADEON(G0): Direct rendering disabled
[  3110.463] (II) RADEON(G0): Acceleration disabled
[  3110.464] (==) RADEON(G0): DPMS enabled
[  3110.464] (==) RADEON(G0): Silken mouse enabled
[  3110.464] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  3110.464] (II) RADEON(0): [DRI2] Setup complete
[  3110.464] (II) RADEON(0): [DRI2]   DRI driver: r600
[  3110.464] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[  3110.465] (II) RADEON(0): Front buffer size: 8160K
[  3110.465] (II) RADEON(0): VRAM usage limit set to 456937K
[  3110.465] (==) RADEON(0): Backing store disabled
[  3110.465] (II) RADEON(0): Direct rendering enabled
[  3110.853] (II) RADEON(0): Use GLAMOR acceleration.
[  3110.853] (II) RADEON(0): Acceleration enabled
[  3110.853] (==) RADEON(0): DPMS enabled
[  3110.853] (==) RADEON(0): Silken mouse enabled
[  3110.853] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  3110.854] (--) RandR disabled
[  3110.873] (II) SELinux: Disabled on system
[  3110.879] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  3110.879] (II) AIGLX: enabled GLX_INTEL_swap_event
[  3110.879] (II) AIGLX: enabled GLX_ARB_create_context
[  3110.879] (II) AIGLX: enabled GLX_ARB_create_context_profile
[  3110.879] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[  3110.879] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  3110.879] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  3110.882] (II) AIGLX: Loaded and initialized r600
[  3110.882] (II) GLX: Initialized DRI2 GL provider for screen 0
[  3110.933] (II) RADEON(0): Setting screen physical size to 508 x 285
[  3110.962] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3110.971] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  3110.972] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3110.972] (II) LoadModule: "evdev"
[  3110.972] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  3110.973] (II) Module evdev: vendor="X.Org Foundation"
[  3110.973] 	compiled for 1.14.1, module version = 2.7.3
[  3110.973] 	Module class: X.Org XInput Driver
[  3110.973] 	ABI class: X.Org XInput driver, version 19.1
[  3110.973] (II) Using input driver 'evdev' for 'Power Button'
[  3110.973] (**) Power Button: always reports core events
[  3110.973] (**) evdev: Power Button: Device: "/dev/input/event2"
[  3110.974] (--) evdev: Power Button: Vendor 0 Product 0x1
[  3110.974] (--) evdev: Power Button: Found keys
[  3110.974] (II) evdev: Power Button: Configuring as keyboard
[  3110.974] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  3110.974] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  3110.974] (**) Option "xkb_rules" "evdev"
[  3110.974] (**) Option "xkb_model" "pc105"
[  3110.974] (**) Option "xkb_layout" "us"
[  3110.976] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  3110.976] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  3110.976] (II) Using input driver 'evdev' for 'Video Bus'
[  3110.976] (**) Video Bus: always reports core events
[  3110.976] (**) evdev: Video Bus: Device: "/dev/input/event4"
[  3110.976] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  3110.976] (--) evdev: Video Bus: Found keys
[  3110.976] (II) evdev: Video Bus: Configuring as keyboard
[  3110.976] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[  3110.976] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  3110.976] (**) Option "xkb_rules" "evdev"
[  3110.976] (**) Option "xkb_model" "pc105"
[  3110.977] (**) Option "xkb_layout" "us"
[  3110.978] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  3110.978] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  3110.978] (II) Using input driver 'evdev' for 'Video Bus'
[  3110.978] (**) Video Bus: always reports core events
[  3110.978] (**) evdev: Video Bus: Device: "/dev/input/event5"
[  3110.978] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  3110.979] (--) evdev: Video Bus: Found keys
[  3110.979] (II) evdev: Video Bus: Configuring as keyboard
[  3110.979] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:01/input/input5/event5"
[  3110.979] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[  3110.979] (**) Option "xkb_rules" "evdev"
[  3110.979] (**) Option "xkb_model" "pc105"
[  3110.979] (**) Option "xkb_layout" "us"
[  3110.980] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  3110.980] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  3110.980] (II) Using input driver 'evdev' for 'Power Button'
[  3110.981] (**) Power Button: always reports core events
[  3110.981] (**) evdev: Power Button: Device: "/dev/input/event0"
[  3110.981] (--) evdev: Power Button: Vendor 0 Product 0x1
[  3110.981] (--) evdev: Power Button: Found keys
[  3110.981] (II) evdev: Power Button: Configuring as keyboard
[  3110.981] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  3110.981] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[  3110.981] (**) Option "xkb_rules" "evdev"
[  3110.981] (**) Option "xkb_model" "pc105"
[  3110.981] (**) Option "xkb_layout" "us"
[  3110.983] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[  3110.983] (II) No input driver specified, ignoring this device.
[  3110.983] (II) This device may have been added with another device file.
[  3110.983] (II) config/udev: Adding drm device (/dev/dri/card0)
[  3110.983] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[  3110.984] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event7)
[  3110.984] (II) No input driver specified, ignoring this device.
[  3110.984] (II) This device may have been added with another device file.
[  3110.985] (II) config/udev: Adding drm device (/dev/dri/card1)
[  3110.985] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[  3110.986] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event11)
[  3110.986] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[  3110.986] (II) Using input driver 'evdev' for 'HP Truevision HD'
[  3110.986] (**) HP Truevision HD: always reports core events
[  3110.986] (**) evdev: HP Truevision HD: Device: "/dev/input/event11"
[  3110.986] (--) evdev: HP Truevision HD: Vendor 0xbda Product 0x58d8
[  3110.986] (--) evdev: HP Truevision HD: Found keys
[  3110.986] (II) evdev: HP Truevision HD: Configuring as keyboard
[  3110.986] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/input/input11/event11"
[  3110.986] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 10)
[  3110.986] (**) Option "xkb_rules" "evdev"
[  3110.986] (**) Option "xkb_model" "pc105"
[  3110.987] (**) Option "xkb_layout" "us"
[  3110.988] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event8)
[  3110.988] (II) No input driver specified, ignoring this device.
[  3110.988] (II) This device may have been added with another device file.
[  3110.989] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event9)
[  3110.989] (II) No input driver specified, ignoring this device.
[  3110.989] (II) This device may have been added with another device file.
[  3110.990] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  3110.990] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  3110.990] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  3110.990] (**) AT Translated Set 2 keyboard: always reports core events
[  3110.990] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  3110.990] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  3110.990] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  3110.990] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  3110.990] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  3110.990] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[  3110.991] (**) Option "xkb_rules" "evdev"
[  3110.991] (**) Option "xkb_model" "pc105"
[  3110.991] (**) Option "xkb_layout" "us"
[  3110.992] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[  3110.992] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  3110.992] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  3110.992] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[  3110.992] (II) LoadModule: "synaptics"
[  3110.993] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  3110.993] (II) Module synaptics: vendor="X.Org Foundation"
[  3110.993] 	compiled for 1.14.2, module version = 1.7.1
[  3110.994] 	Module class: X.Org XInput Driver
[  3110.994] 	ABI class: X.Org XInput driver, version 19.1
[  3110.994] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  3110.994] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  3110.994] (**) Option "Device" "/dev/input/event10"
[  3111.020] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5684 (res 47)
[  3111.020] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4862 (res 92)
[  3111.020] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  3111.020] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  3111.020] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  3111.020] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[  3111.021] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  3111.021] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  3111.036] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[  3111.036] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[  3111.036] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  3111.036] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[  3111.036] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[  3111.037] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  3111.037] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  3111.037] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  3111.037] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  3111.037] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  3111.038] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[  3111.038] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[  3111.039] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[  3111.039] (II) No input driver specified, ignoring this device.
[  3111.039] (II) This device may have been added with another device file.
[  3111.040] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[  3111.040] (II) No input driver specified, ignoring this device.
[  3111.040] (II) This device may have been added with another device file.
[  3111.046] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event12)
[  3111.046] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  3111.046] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[  3111.047] (**) HP WMI hotkeys: always reports core events
[  3111.047] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event12"
[  3111.047] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[  3111.047] (--) evdev: HP WMI hotkeys: Found keys
[  3111.047] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[  3111.047] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event12"
[  3111.047] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[  3111.047] (**) Option "xkb_rules" "evdev"
[  3111.047] (**) Option "xkb_model" "pc105"
[  3111.047] (**) Option "xkb_layout" "us"
[  3111.066] reporting 10 3 16 129
[  3111.834] reporting 10 3 16 129
[  3111.947] reporting 10 3 16 129
[  3112.065] reporting 10 3 16 129
[  3112.164] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3112.164] (II) RADEON(0): Printing DDC gathered Modelines:
[  3112.164] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3112.164] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3112.384] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3112.384] (II) RADEON(0): Printing DDC gathered Modelines:
[  3112.384] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3112.384] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3112.561] reporting 10 3 16 129
[  3112.689] reporting 10 3 16 129
[  3112.737] reporting 10 3 16 129
[  3112.743] reporting 10 3 16 129
[  3112.836] reporting 10 3 16 129
[  3113.036] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3113.036] (II) RADEON(0): Printing DDC gathered Modelines:
[  3113.036] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3113.036] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3113.261] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3113.261] (II) RADEON(0): Printing DDC gathered Modelines:
[  3113.261] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3113.261] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3113.437] reporting 10 3 16 129
[  3113.502] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3113.502] (II) RADEON(0): Printing DDC gathered Modelines:
[  3113.502] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3113.502] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3113.720] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3113.720] (II) RADEON(0): Printing DDC gathered Modelines:
[  3113.720] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3113.720] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3113.893] reporting 10 3 16 129
[  3113.931] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3114.053] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3114.059] reporting 10 3 16 129
[  3114.066] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3114.077] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3114.087] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3114.180] reporting 10 3 16 129
[  3114.869] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3114.906] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3114.939] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3114.971] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3115.202] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3116.450] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3118.855] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3122.034] reporting 10 3 16 129
[  3122.043] reporting 10 3 16 129
[  3122.141] reporting 10 3 16 129
[  3122.315] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3122.315] (II) RADEON(0): Printing DDC gathered Modelines:
[  3122.315] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3122.315] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3122.536] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3122.536] (II) RADEON(0): Printing DDC gathered Modelines:
[  3122.536] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3122.536] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3122.714] reporting 10 3 16 129
[  3122.881] reporting 10 3 16 129
[  3122.920] reporting 10 3 16 129
[  3123.007] reporting 10 3 16 129
[  3123.088] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3123.088] (II) RADEON(0): Printing DDC gathered Modelines:
[  3123.088] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3123.088] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3123.308] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3123.308] (II) RADEON(0): Printing DDC gathered Modelines:
[  3123.308] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3123.308] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3123.485] reporting 10 3 16 129
[  3124.162] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3124.173] reporting 10 3 16 129
[  3124.224] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3124.224] (II) RADEON(0): Printing DDC gathered Modelines:
[  3124.224] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3124.224] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3124.440] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3124.440] (II) RADEON(0): Printing DDC gathered Modelines:
[  3124.440] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3124.440] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3124.617] reporting 10 3 16 129
[  3124.780] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3124.879] reporting 10 3 16 129
[  3125.593] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3125.910] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  3128.107] (II) XKB: reuse xkmfile /var/lib/xkb/server-B59E50A6E741E924A50F942B78A8EF54156068A0.xkm
[  3130.485] reporting 10 3 16 129
[  3130.658] reporting 10 3 16 129
[  3131.654] reporting 10 3 16 129
[  3131.841] reporting 10 3 16 129
[  3135.770] reporting 10 3 16 129
[  3142.581] reporting 10 3 16 129
[  3145.156] reporting 10 3 16 129
[  3155.208] reporting 10 3 16 129
[  3155.448] reporting 10 3 16 129
[  3155.938] reporting 10 3 16 129
[  3156.769] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3156.769] (II) RADEON(0): Printing DDC gathered Modelines:
[  3156.769] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3156.769] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3156.988] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3156.988] (II) RADEON(0): Printing DDC gathered Modelines:
[  3156.988] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3156.988] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3157.165] reporting 10 3 16 129
[  3157.701] reporting 10 3 16 129
[  3157.786] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3157.786] (II) RADEON(0): Printing DDC gathered Modelines:
[  3157.786] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3157.786] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3158.005] (II) RADEON(0): EDID vendor "LGD", prod id 895
[  3158.005] (II) RADEON(0): Printing DDC gathered Modelines:
[  3158.005] (II) RADEON(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[  3158.005] (II) RADEON(0): Modeline "1920x1080"x0.0   99.33  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (45.0 kHz e)
[  3158.181] reporting 10 3 16 129
[  3187.582] reporting 10 3 16 129
[  3198.117] reporting 10 3 16 129

```

---

### Post by managementboy on 2013-10-28
I am having the exact same issue. Does someone know a work arround? with 13.04 it worked flawlessly.

---

### Post by CalcProgrammer1 on 2013-10-31
Update!  I installed the Oibaf graphics-drivers PPA that contains the new mesa 10.0 stuff and the first issue with the laptop goes away.  Now both GPU's successfully enable acceleration via glamor.  However, now my laptop is doing the same thing as my desktop, with two GPU's active there is complete window corruption on accelerated desktops (but likewise the GNOME menu stuff, GNOME overlay, etc. all work correctly).  On the desktop it's r600+r600, laptop is r600+radeonsi.

---

