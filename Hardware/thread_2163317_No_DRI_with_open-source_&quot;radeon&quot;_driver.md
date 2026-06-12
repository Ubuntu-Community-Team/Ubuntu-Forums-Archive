---
title: "No DRI with open-source &quot;radeon&quot; driver"
date: 2013-07-17
forum: Hardware
---

### Post by *Legion* on 2013-07-17
Running Ubuntu 13.04 with a Radeon 7870.

Completely uninstalled fglrx driver. Installed the "radeon" open source driver.

Performance is very slow. glxinfo says Direct Rendering is "yes", but with LIBGL_DEBUG=verbose, I see messages saying that screen 0 does not appear to be DRI2 capable, and that libGL is loading the swrast_dri.so driver, not radeon_dri.so.

glxinfo output w/verbose debug:
```

% LIBGL_DEBUG=verbose glxinfo
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/brendon/.drirc: No such file or directory.
libGL: Can't open configuration file /home/brendon/.drirc: No such file or directory.
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
(... etc ...)

```

dmesg output:
```

% dmesg | egrep 'drm|radeon'
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[    5.381683] [drm] Initialized drm 1.1.0 20060810
[    5.399621] [drm] radeon kernel modesetting enabled.
[    5.401278] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6818 0x1682:0x3251).
[    5.401463] [drm] register mmio base: 0xF7E00000
[    5.401464] [drm] register mmio size: 262144
[    5.401551] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    5.401552] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    5.403170] [drm] Detected VRAM RAM=2048M, BAR=256M
[    5.403172] [drm] RAM width 256bits DDR
[    5.405275] [drm] radeon: 2048M of VRAM memory ready
[    5.405275] [drm] radeon: 512M of GTT memory ready.
[    5.405286] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.405287] [drm] Driver supports precise vblank timestamp query.
[    5.405314] radeon 0000:01:00.0: irq 49 for MSI/MSI-X
[    5.405320] radeon 0000:01:00.0: radeon: using MSI.
[    5.405346] [drm] radeon: irq initialized.
[    5.405349] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    5.405743] [drm] Loading PITCAIRN Microcode
[    5.808707] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    5.808801] radeon 0000:01:00.0: WB enabled
[    5.808803] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff8804048d0c00
[    5.808804] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff8804048d0c04
[    5.808805] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff8804048d0c08
[    5.808807] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff8804048d0c0c
[    5.808807] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff8804048d0c10
[    5.827497] [drm] ring test on 0 succeeded in 4 usecs
[    5.827502] [drm] ring test on 1 succeeded in 1 usecs
[    5.827505] [drm] ring test on 2 succeeded in 1 usecs
[    5.827566] [drm] ring test on 3 succeeded in 2 usecs
[    5.827576] [drm] ring test on 4 succeeded in 1 usecs
[    5.837904] [drm] ib test on ring 0 succeeded in 0 usecs
[    5.837948] [drm] ib test on ring 1 succeeded in 0 usecs
[    5.837989] [drm] ib test on ring 2 succeeded in 0 usecs
[    5.838028] [drm] ib test on ring 3 succeeded in 0 usecs
[    5.838068] [drm] ib test on ring 4 succeeded in 1 usecs
[    5.838755] [drm] Radeon Display Connectors
[    5.838756] [drm] Connector 0:
[    5.838757] [drm]   DP-1
[    5.838758] [drm]   HPD4
[    5.838759] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    5.838759] [drm]   Encoders:
[    5.838760] [drm]     DFP1: INTERNAL_UNIPHY2
[    5.838761] [drm] Connector 1:
[    5.838761] [drm]   DP-2
[    5.838762] [drm]   HPD5
[    5.838763] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    5.838763] [drm]   Encoders:
[    5.838764] [drm]     DFP2: INTERNAL_UNIPHY2
[    5.838764] [drm] Connector 2:
[    5.838765] [drm]   HDMI-A-1
[    5.838765] [drm]   HPD1
[    5.838766] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    5.838767] [drm]   Encoders:
[    5.838767] [drm]     DFP3: INTERNAL_UNIPHY1
[    5.838768] [drm] Connector 3:
[    5.838769] [drm]   DVI-I-1
[    5.838769] [drm]   HPD6
[    5.838770] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    5.838771] [drm]   Encoders:
[    5.838771] [drm]     DFP4: INTERNAL_UNIPHY
[    5.838772] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    5.838772] [drm] Connector 4:
[    5.838773] [drm]   DVI-D-1
[    5.838773] [drm]   HPD3
[    5.838774] [drm]   DDC: 0x6570 0x6570 0x6574 0x6574 0x6578 0x6578 0x657c 0x657c
[    5.838775] [drm]   Encoders:
[    5.838775] [drm]     DFP5: INTERNAL_UNIPHY1
[    5.838822] [drm] Internal thermal controller with fan control
[    5.838857] [drm] radeon: power management initialized
[    5.963834] [drm] fb mappable at 0xE114B000
[    5.963836] [drm] vram apper at 0xE0000000
[    5.963837] [drm] size 8294400
[    5.963837] [drm] fb depth is 24
[    5.963838] [drm]    pitch is 7680
[    5.963897] fbcon: radeondrmfb (fb0) is primary device
[    6.000386] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    6.000387] radeon 0000:01:00.0: registered panic notifier
[    6.000391] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0


```

---

### Post by Yellow Pasque on 2013-07-17
Post your /var/log/Xorg.0.log

---

### Post by ssam on 2013-07-18
AMD South Island support in the opensource drivers is still a way behind the propriety driver.
[http://www.phoronix.com/scan.php?page=article&item=amd_radeonsi_fedora19&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_radeonsi_fedora19&num=1)

you might be best to stick with propriety driver for now, unless you want to play around with development versions of mesa and the kernel.

---

### Post by *Legion* on 2013-08-01
> **Temüjin said:**
> Post your /var/log/Xorg.0.log

Xorg.0.log:
```

[     7.281] 
X.Org X Server 1.13.4
Release Date: 2013-04-17
[     7.281] X Protocol Version 11, Revision 0
[     7.281] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[     7.281] Current Operating System: Linux halas 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64
[     7.281] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[     7.281] Build Date: 08 May 2013  02:34:03PM
[     7.281] xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see http://www.ubuntu.com/support) 
[     7.281] Current version of pixman: 0.28.2
[     7.281] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     7.281] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.281] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  1 12:55:01 2013
[     7.281] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.281] (==) No Layout section.  Using the first Screen section.
[     7.281] (==) No screen section available. Using defaults.
[     7.281] (**) |-->Screen "Default Screen Section" (0)
[     7.281] (**) |   |-->Monitor "<default monitor>"
[     7.281] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     7.281] (==) Automatically adding devices
[     7.281] (==) Automatically enabling devices
[     7.281] (==) Automatically adding GPU devices
[     7.281] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.281] 	Entry deleted from font path.
[     7.281] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.281] 	Entry deleted from font path.
[     7.281] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.281] 	Entry deleted from font path.
[     7.281] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.281] 	Entry deleted from font path.
[     7.281] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.281] 	Entry deleted from font path.
[     7.281] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     7.281] 	Entry deleted from font path.
[     7.281] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     7.281] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     7.281] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.281] (II) Loader magic: 0x7f5fba7d1d20
[     7.281] (II) Module ABI versions:
[     7.281] 	X.Org ANSI C Emulation: 0.4
[     7.281] 	X.Org Video Driver: 13.1
[     7.281] 	X.Org XInput driver : 18.0
[     7.281] 	X.Org Server Extension : 7.0
[     7.281] (II) config/udev: Adding drm device (/dev/dri/card0)
[     7.282] (--) PCI:*(0:1:0:0) 1002:6818:1682:3251 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     7.282] (II) Open ACPI successful (/var/run/acpid.socket)
[     7.282] Initializing built-in extension Generic Event Extension
[     7.282] Initializing built-in extension SHAPE
[     7.282] Initializing built-in extension MIT-SHM
[     7.282] Initializing built-in extension XInputExtension
[     7.282] Initializing built-in extension XTEST
[     7.282] Initializing built-in extension BIG-REQUESTS
[     7.282] Initializing built-in extension SYNC
[     7.282] Initializing built-in extension XKEYBOARD
[     7.282] Initializing built-in extension XC-MISC
[     7.282] Initializing built-in extension SECURITY
[     7.282] Initializing built-in extension XINERAMA
[     7.282] Initializing built-in extension XFIXES
[     7.282] Initializing built-in extension RENDER
[     7.282] Initializing built-in extension RANDR
[     7.283] Initializing built-in extension COMPOSITE
[     7.283] Initializing built-in extension DAMAGE
[     7.283] Initializing built-in extension MIT-SCREEN-SAVER
[     7.283] Initializing built-in extension DOUBLE-BUFFER
[     7.283] Initializing built-in extension RECORD
[     7.283] Initializing built-in extension DPMS
[     7.283] Initializing built-in extension X-Resource
[     7.283] Initializing built-in extension XVideo
[     7.283] Initializing built-in extension XVideo-MotionCompensation
[     7.283] Initializing built-in extension SELinux
[     7.283] Initializing built-in extension XFree86-VidModeExtension
[     7.283] Initializing built-in extension XFree86-DGA
[     7.283] Initializing built-in extension XFree86-DRI
[     7.283] Initializing built-in extension DRI2
[     7.283] (II) LoadModule: "glx"
[     7.283] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     7.283] (II) Module glx: vendor="X.Org Foundation"
[     7.283] 	compiled for 1.13.4, module version = 1.0.0
[     7.283] 	ABI class: X.Org Server Extension, version 7.0
[     7.283] (==) AIGLX enabled
[     7.283] Loading extension GLX
[     7.283] (==) Matched fglrx as autoconfigured driver 0
[     7.283] (==) Matched ati as autoconfigured driver 1
[     7.283] (==) Matched fglrx as autoconfigured driver 2
[     7.283] (==) Matched ati as autoconfigured driver 3
[     7.283] (==) Matched vesa as autoconfigured driver 4
[     7.283] (==) Matched modesetting as autoconfigured driver 5
[     7.283] (==) Matched fbdev as autoconfigured driver 6
[     7.283] (==) Assigned the driver to the xf86ConfigLayout
[     7.283] (II) LoadModule: "fglrx"
[     7.283] (WW) Warning, couldn't open module fglrx
[     7.283] (II) UnloadModule: "fglrx"
[     7.283] (II) Unloading fglrx
[     7.283] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     7.283] (II) LoadModule: "ati"
[     7.283] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     7.283] (II) Module ati: vendor="X.Org Foundation"
[     7.283] 	compiled for 1.13.4, module version = 7.1.99
[     7.283] 	Module class: X.Org Video Driver
[     7.283] 	ABI class: X.Org Video Driver, version 13.1
[     7.283] (II) LoadModule: "radeon"
[     7.284] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     7.284] (II) Module radeon: vendor="X.Org Foundation"
[     7.284] 	compiled for 1.13.4, module version = 7.1.99
[     7.284] 	Module class: X.Org Video Driver
[     7.284] 	ABI class: X.Org Video Driver, version 13.1
[     7.284] (II) LoadModule: "vesa"
[     7.284] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.284] (II) Module vesa: vendor="X.Org Foundation"
[     7.284] 	compiled for 1.12.99.902, module version = 2.3.2
[     7.284] 	Module class: X.Org Video Driver
[     7.284] 	ABI class: X.Org Video Driver, version 13.0
[     7.284] (II) LoadModule: "modesetting"
[     7.284] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     7.284] (II) Module modesetting: vendor="X.Org Foundation"
[     7.284] 	compiled for 1.13.3, module version = 0.7.0
[     7.284] 	Module class: X.Org Video Driver
[     7.284] 	ABI class: X.Org Video Driver, version 13.1
[     7.284] (II) LoadModule: "fbdev"
[     7.284] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.284] (II) Module fbdev: vendor="X.Org Foundation"
[     7.284] 	compiled for 1.12.99.902, module version = 0.4.3
[     7.284] 	Module class: X.Org Video Driver
[     7.284] 	ABI class: X.Org Video Driver, version 13.0
[     7.284] (==) Matched fglrx as autoconfigured driver 0
[     7.284] (==) Matched ati as autoconfigured driver 1
[     7.284] (==) Matched fglrx as autoconfigured driver 2
[     7.284] (==) Matched ati as autoconfigured driver 3
[     7.284] (==) Matched vesa as autoconfigured driver 4
[     7.284] (==) Matched modesetting as autoconfigured driver 5
[     7.284] (==) Matched fbdev as autoconfigured driver 6
[     7.284] (==) Assigned the driver to the xf86ConfigLayout
[     7.284] (II) LoadModule: "fglrx"
[     7.285] (WW) Warning, couldn't open module fglrx
[     7.285] (II) UnloadModule: "fglrx"
[     7.285] (II) Unloading fglrx
[     7.285] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     7.285] (II) LoadModule: "ati"
[     7.285] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     7.285] (II) Module ati: vendor="X.Org Foundation"
[     7.285] 	compiled for 1.13.4, module version = 7.1.99
[     7.285] 	Module class: X.Org Video Driver
[     7.285] 	ABI class: X.Org Video Driver, version 13.1
[     7.285] (II) LoadModule: "vesa"
[     7.285] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.285] (II) Module vesa: vendor="X.Org Foundation"
[     7.285] 	compiled for 1.12.99.902, module version = 2.3.2
[     7.285] 	Module class: X.Org Video Driver
[     7.285] 	ABI class: X.Org Video Driver, version 13.0
[     7.285] (II) UnloadModule: "vesa"
[     7.285] (II) Unloading vesa
[     7.285] (II) Failed to load module "vesa" (already loaded, 0)
[     7.285] (II) LoadModule: "modesetting"
[     7.285] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     7.285] (II) Module modesetting: vendor="X.Org Foundation"
[     7.285] 	compiled for 1.13.3, module version = 0.7.0
[     7.285] 	Module class: X.Org Video Driver
[     7.285] 	ABI class: X.Org Video Driver, version 13.1
[     7.285] (II) UnloadModule: "modesetting"
[     7.285] (II) Unloading modesetting
[     7.285] (II) Failed to load module "modesetting" (already loaded, 0)
[     7.285] (II) LoadModule: "fbdev"
[     7.285] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.285] (II) Module fbdev: vendor="X.Org Foundation"
[     7.285] 	compiled for 1.12.99.902, module version = 0.4.3
[     7.285] 	Module class: X.Org Video Driver
[     7.285] 	ABI class: X.Org Video Driver, version 13.0
[     7.285] (II) UnloadModule: "fbdev"
[     7.285] (II) Unloading fbdev
[     7.285] (II) Failed to load module "fbdev" (already loaded, 0)
[     7.285] (II) RADEON: Driver for ATI Radeon chipsets:
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
[     7.287] (II) VESA: driver for VESA chipsets: vesa
[     7.287] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     7.287] (II) FBDEV: driver for framebuffer: fbdev
[     7.287] (++) using VT number 7

[     7.287] (II) [KMS] Kernel modesetting enabled.
[     7.287] (WW) Falling back to old probe method for vesa
[     7.287] (WW) Falling back to old probe method for modesetting
[     7.287] (WW) Falling back to old probe method for fbdev
[     7.287] (II) Loading sub module "fbdevhw"
[     7.287] (II) LoadModule: "fbdevhw"
[     7.287] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     7.287] (II) Module fbdevhw: vendor="X.Org Foundation"
[     7.287] 	compiled for 1.13.4, module version = 0.0.2
[     7.287] 	ABI class: X.Org Video Driver, version 13.1
[     7.287] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     7.287] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[     7.287] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     7.287] (==) RADEON(0): Default visual is TrueColor
[     7.287] (==) RADEON(0): RGB weight 888
[     7.287] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[     7.287] (--) RADEON(0): Chipset: "PITCAIRN" (ChipID = 0x6818)
[     7.287] (II) Loading sub module "dri2"
[     7.287] (II) LoadModule: "dri2"
[     7.287] (II) Module "dri2" already built-in
[     7.287] (II) Loading sub module "shadow"
[     7.287] (II) LoadModule: "shadow"
[     7.287] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     7.287] (II) Module shadow: vendor="X.Org Foundation"
[     7.287] 	compiled for 1.13.4, module version = 1.1.0
[     7.287] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     7.287] (II) RADEON(0): KMS Color Tiling: disabled
[     7.287] (II) RADEON(0): KMS Color Tiling 2D: disabled
[     7.287] (II) RADEON(0): KMS Pageflipping: enabled
[     7.287] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[     7.304] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[     7.352] (II) RADEON(0): Output DisplayPort-1 has no monitor section
[     7.355] (II) RADEON(0): Output HDMI-0 has no monitor section
[     7.387] (II) RADEON(0): Output DVI-0 has no monitor section
[     7.420] (II) RADEON(0): Output DVI-1 has no monitor section
[     7.436] (II) RADEON(0): EDID for output DisplayPort-0
[     7.484] (II) RADEON(0): EDID for output DisplayPort-1
[     7.484] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 574643103
[     7.484] (II) RADEON(0): Year: 2012  Week: 24
[     7.484] (II) RADEON(0): EDID Version: 1.3
[     7.484] (II) RADEON(0): Digital Display Input
[     7.484] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     7.484] (II) RADEON(0): Gamma: 2.20
[     7.484] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     7.484] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.484] (II) RADEON(0): First detailed timing is preferred mode
[     7.485] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     7.485] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     7.485] (II) RADEON(0): Supported established timings:
[     7.485] (II) RADEON(0): 720x400@70Hz
[     7.485] (II) RADEON(0): 640x480@60Hz
[     7.485] (II) RADEON(0): 640x480@67Hz
[     7.485] (II) RADEON(0): 640x480@72Hz
[     7.485] (II) RADEON(0): 640x480@75Hz
[     7.485] (II) RADEON(0): 800x600@56Hz
[     7.485] (II) RADEON(0): 800x600@60Hz
[     7.485] (II) RADEON(0): 800x600@72Hz
[     7.485] (II) RADEON(0): 800x600@75Hz
[     7.485] (II) RADEON(0): 832x624@75Hz
[     7.485] (II) RADEON(0): 1024x768@60Hz
[     7.485] (II) RADEON(0): 1024x768@70Hz
[     7.485] (II) RADEON(0): 1024x768@75Hz
[     7.485] (II) RADEON(0): 1280x1024@75Hz
[     7.485] (II) RADEON(0): 1152x864@75Hz
[     7.485] (II) RADEON(0): Manufacturer's mask: 0
[     7.485] (II) RADEON(0): Supported standard timings:
[     7.485] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     7.485] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     7.485] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.485] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     7.485] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     7.485] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     7.485] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     7.485] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     7.485] (II) RADEON(0): Supported detailed timing:
[     7.485] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     7.485] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.485] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     7.485] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     7.485] (II) RADEON(0): Monitor name: S271HL
[     7.485] (II) RADEON(0): Serial No: LUW0D0108510
[     7.485] (II) RADEON(0): EDID (in hex):
[     7.485] (II) RADEON(0): 	00ffffffffffff000472ca029f5b4022
[     7.485] (II) RADEON(0): 	18160103803c2278ca7b45a4554aa227
[     7.485] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     7.485] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     7.485] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     7.485] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     7.485] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     7.485] (II) RADEON(0): 	004c55573044303130383531300a00cf
[     7.485] (II) RADEON(0): Printing probed modes for output DisplayPort-1
[     7.485] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.485] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.485] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.485] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.485] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.485] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.485] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.485] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.485] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     7.485] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     7.485] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.485] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.485] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.485] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.485] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.485] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.485] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.485] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     7.485] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.485] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.485] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.485] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.487] (II) RADEON(0): EDID for output HDMI-0
[     7.520] (II) RADEON(0): EDID for output DVI-0
[     7.520] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 573634853
[     7.520] (II) RADEON(0): Year: 2012  Week: 23
[     7.520] (II) RADEON(0): EDID Version: 1.3
[     7.520] (II) RADEON(0): Digital Display Input
[     7.520] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     7.520] (II) RADEON(0): Gamma: 2.20
[     7.520] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     7.520] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.520] (II) RADEON(0): First detailed timing is preferred mode
[     7.520] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     7.520] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     7.520] (II) RADEON(0): Supported established timings:
[     7.520] (II) RADEON(0): 720x400@70Hz
[     7.520] (II) RADEON(0): 640x480@60Hz
[     7.520] (II) RADEON(0): 640x480@67Hz
[     7.520] (II) RADEON(0): 640x480@72Hz
[     7.520] (II) RADEON(0): 640x480@75Hz
[     7.520] (II) RADEON(0): 800x600@56Hz
[     7.520] (II) RADEON(0): 800x600@60Hz
[     7.520] (II) RADEON(0): 800x600@72Hz
[     7.520] (II) RADEON(0): 800x600@75Hz
[     7.520] (II) RADEON(0): 832x624@75Hz
[     7.520] (II) RADEON(0): 1024x768@60Hz
[     7.520] (II) RADEON(0): 1024x768@70Hz
[     7.520] (II) RADEON(0): 1024x768@75Hz
[     7.520] (II) RADEON(0): 1280x1024@75Hz
[     7.520] (II) RADEON(0): 1152x864@75Hz
[     7.520] (II) RADEON(0): Manufacturer's mask: 0
[     7.520] (II) RADEON(0): Supported standard timings:
[     7.520] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     7.520] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     7.520] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.520] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     7.520] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     7.520] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     7.520] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     7.520] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     7.520] (II) RADEON(0): Supported detailed timing:
[     7.520] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     7.520] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.520] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     7.520] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     7.520] (II) RADEON(0): Monitor name: S271HL
[     7.520] (II) RADEON(0): Serial No: LUW0D0108510
[     7.520] (II) RADEON(0): EDID (in hex):
[     7.520] (II) RADEON(0): 	00ffffffffffff000472ca0225f93022
[     7.520] (II) RADEON(0): 	17160103803c2278ca7b45a4554aa227
[     7.520] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     7.520] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     7.520] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     7.520] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     7.520] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     7.520] (II) RADEON(0): 	004c55573044303130383531300a00bc
[     7.520] (II) RADEON(0): Printing probed modes for output DVI-0
[     7.520] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.520] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.520] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.520] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.520] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.520] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.520] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.520] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.520] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     7.520] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     7.520] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.520] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.520] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.520] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.520] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.520] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.520] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.520] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     7.520] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.520] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.520] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.520] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.553] (II) RADEON(0): EDID for output DVI-1
[     7.553] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 573634863
[     7.553] (II) RADEON(0): Year: 2012  Week: 23
[     7.553] (II) RADEON(0): EDID Version: 1.3
[     7.553] (II) RADEON(0): Digital Display Input
[     7.553] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     7.553] (II) RADEON(0): Gamma: 2.20
[     7.553] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     7.553] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.553] (II) RADEON(0): First detailed timing is preferred mode
[     7.553] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     7.553] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     7.553] (II) RADEON(0): Supported established timings:
[     7.553] (II) RADEON(0): 720x400@70Hz
[     7.553] (II) RADEON(0): 640x480@60Hz
[     7.553] (II) RADEON(0): 640x480@67Hz
[     7.553] (II) RADEON(0): 640x480@72Hz
[     7.553] (II) RADEON(0): 640x480@75Hz
[     7.553] (II) RADEON(0): 800x600@56Hz
[     7.553] (II) RADEON(0): 800x600@60Hz
[     7.553] (II) RADEON(0): 800x600@72Hz
[     7.553] (II) RADEON(0): 800x600@75Hz
[     7.553] (II) RADEON(0): 832x624@75Hz
[     7.553] (II) RADEON(0): 1024x768@60Hz
[     7.553] (II) RADEON(0): 1024x768@70Hz
[     7.553] (II) RADEON(0): 1024x768@75Hz
[     7.553] (II) RADEON(0): 1280x1024@75Hz
[     7.553] (II) RADEON(0): 1152x864@75Hz
[     7.553] (II) RADEON(0): Manufacturer's mask: 0
[     7.553] (II) RADEON(0): Supported standard timings:
[     7.553] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     7.553] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     7.553] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.553] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     7.553] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     7.553] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     7.553] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     7.553] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     7.553] (II) RADEON(0): Supported detailed timing:
[     7.553] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     7.553] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.553] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     7.553] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     7.553] (II) RADEON(0): Monitor name: S271HL
[     7.553] (II) RADEON(0): Serial No: LUW0D0108510
[     7.553] (II) RADEON(0): EDID (in hex):
[     7.553] (II) RADEON(0): 	00ffffffffffff000472ca022ff93022
[     7.553] (II) RADEON(0): 	17160103803c2278ca7b45a4554aa227
[     7.553] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     7.553] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     7.553] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     7.553] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     7.553] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     7.553] (II) RADEON(0): 	004c55573044303130383531300a00b2
[     7.553] (II) RADEON(0): Printing probed modes for output DVI-1
[     7.553] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.553] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.553] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.553] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.553] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.553] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.553] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.553] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.553] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     7.553] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     7.553] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.553] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.553] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.553] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.553] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.553] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.553] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.553] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     7.553] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.553] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.553] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.553] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.553] (II) RADEON(0): Output DisplayPort-0 disconnected
[     7.553] (II) RADEON(0): Output DisplayPort-1 connected
[     7.553] (II) RADEON(0): Output HDMI-0 disconnected
[     7.553] (II) RADEON(0): Output DVI-0 connected
[     7.553] (II) RADEON(0): Output DVI-1 connected
[     7.553] (II) RADEON(0): Using exact sizes for initial modes
[     7.553] (II) RADEON(0): Output DisplayPort-1 using initial mode 1920x1080
[     7.553] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080
[     7.553] (II) RADEON(0): Output DVI-1 using initial mode 1920x1080
[     7.553] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     7.553] (II) RADEON(0): mem size init: gart size :1fbdf000 vram size: s:80000000 visible:7f7d7000
[     7.553] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[     7.553] (==) RADEON(0): DPI set to (96, 96)
[     7.553] (II) Loading sub module "fb"
[     7.553] (II) LoadModule: "fb"
[     7.553] (II) Loading /usr/lib/xorg/modules/libfb.so
[     7.553] (II) Module fb: vendor="X.Org Foundation"
[     7.553] 	compiled for 1.13.4, module version = 1.0.0
[     7.553] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     7.553] (II) Loading sub module "ramdac"
[     7.553] (II) LoadModule: "ramdac"
[     7.553] (II) Module "ramdac" already built-in
[     7.553] (II) UnloadModule: "vesa"
[     7.553] (II) Unloading vesa
[     7.554] (II) UnloadModule: "modesetting"
[     7.554] (II) Unloading modesetting
[     7.554] (II) UnloadModule: "fbdev"
[     7.554] (II) Unloading fbdev
[     7.554] (II) UnloadSubModule: "fbdevhw"
[     7.554] (II) Unloading fbdevhw
[     7.554] (--) Depth 24 pixmap format is 32 bpp
[     7.554] (II) RADEON(0): Front buffer size: 8100K
[     7.554] (II) RADEON(0): VRAM usage limit set to 1872540K
[     7.554] (==) RADEON(0): Backing store disabled
[     7.554] (WW) RADEON(0): Direct rendering disabled
[     7.554] (II) RADEON(0): Acceleration disabled
[     7.554] (==) RADEON(0): DPMS enabled
[     7.554] (==) RADEON(0): Silken mouse enabled
[     7.554] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     7.554] (--) RandR disabled
[     7.556] (II) SELinux: Disabled on system
[     7.557] (II) AIGLX: Screen 0 is not DRI2 capable
[     7.557] (II) AIGLX: Screen 0 is not DRI capable
[     7.571] (II) AIGLX: Loaded and initialized swrast
[     7.571] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     7.573] (II) RADEON(0): Setting screen physical size to 508 x 285
[     7.579] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.580] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.580] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.580] (II) LoadModule: "evdev"
[     7.580] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.581] (II) Module evdev: vendor="X.Org Foundation"
[     7.581] 	compiled for 1.13.3, module version = 2.7.3
[     7.581] 	Module class: X.Org XInput Driver
[     7.581] 	ABI class: X.Org XInput driver, version 18.0
[     7.581] (II) Using input driver 'evdev' for 'Power Button'
[     7.581] (**) Power Button: always reports core events
[     7.581] (**) evdev: Power Button: Device: "/dev/input/event1"
[     7.581] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.581] (--) evdev: Power Button: Found keys
[     7.581] (II) evdev: Power Button: Configuring as keyboard
[     7.581] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     7.581] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     7.581] (**) Option "xkb_rules" "evdev"
[     7.581] (**) Option "xkb_model" "pc105"
[     7.581] (**) Option "xkb_layout" "us"
[     7.581] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.581] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.581] (II) Using input driver 'evdev' for 'Power Button'
[     7.581] (**) Power Button: always reports core events
[     7.581] (**) evdev: Power Button: Device: "/dev/input/event0"
[     7.581] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.581] (--) evdev: Power Button: Found keys
[     7.581] (II) evdev: Power Button: Configuring as keyboard
[     7.581] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     7.581] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     7.581] (**) Option "xkb_rules" "evdev"
[     7.581] (**) Option "xkb_model" "pc105"
[     7.581] (**) Option "xkb_layout" "us"
[     7.581] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     7.581] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     7.581] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event13)
[     7.581] (II) No input driver specified, ignoring this device.
[     7.581] (II) This device may have been added with another device file.
[     7.582] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event14)
[     7.582] (II) No input driver specified, ignoring this device.
[     7.582] (II) This device may have been added with another device file.
[     7.582] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event15)
[     7.582] (II) No input driver specified, ignoring this device.
[     7.582] (II) This device may have been added with another device file.
[     7.582] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event16)
[     7.582] (II) No input driver specified, ignoring this device.
[     7.582] (II) This device may have been added with another device file.
[     7.582] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event17)
[     7.582] (II) No input driver specified, ignoring this device.
[     7.582] (II) This device may have been added with another device file.
[     7.582] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event18)
[     7.582] (II) No input driver specified, ignoring this device.
[     7.582] (II) This device may have been added with another device file.
[     7.582] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[     7.582] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     7.582] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     7.582] (**) HID 04f3:0103: always reports core events
[     7.582] (**) evdev: HID 04f3:0103: Device: "/dev/input/event2"
[     7.582] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[     7.582] (--) evdev: HID 04f3:0103: Found keys
[     7.582] (II) evdev: HID 04f3:0103: Configuring as keyboard
[     7.582] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input2/event2"
[     7.582] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 8)
[     7.582] (**) Option "xkb_rules" "evdev"
[     7.582] (**) Option "xkb_model" "pc105"
[     7.582] (**) Option "xkb_layout" "us"
[     7.582] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[     7.582] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     7.582] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     7.582] (**) HID 04f3:0103: always reports core events
[     7.582] (**) evdev: HID 04f3:0103: Device: "/dev/input/event3"
[     7.582] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[     7.582] (--) evdev: HID 04f3:0103: Found 1 mouse buttons
[     7.582] (--) evdev: HID 04f3:0103: Found scroll wheel(s)
[     7.582] (--) evdev: HID 04f3:0103: Found relative axes
[     7.582] (II) evdev: HID 04f3:0103: Forcing relative x/y axes to exist.
[     7.582] (--) evdev: HID 04f3:0103: Found absolute axes
[     7.582] (II) evdev: HID 04f3:0103: Forcing absolute x/y axes to exist.
[     7.582] (--) evdev: HID 04f3:0103: Found keys
[     7.582] (II) evdev: HID 04f3:0103: Configuring as mouse
[     7.582] (II) evdev: HID 04f3:0103: Configuring as keyboard
[     7.582] (II) evdev: HID 04f3:0103: Adding scrollwheel support
[     7.582] (**) evdev: HID 04f3:0103: YAxisMapping: buttons 4 and 5
[     7.582] (**) evdev: HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.582] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input3/event3"
[     7.582] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 9)
[     7.582] (**) Option "xkb_rules" "evdev"
[     7.582] (**) Option "xkb_model" "pc105"
[     7.582] (**) Option "xkb_layout" "us"
[     7.583] (II) evdev: HID 04f3:0103: initialized for relative axes.
[     7.583] (WW) evdev: HID 04f3:0103: ignoring absolute axes.
[     7.583] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[     7.583] (**) HID 04f3:0103: (accel) acceleration profile 0
[     7.583] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[     7.583] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[     7.583] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event4)
[     7.583] (**) Cypress USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     7.583] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     7.583] (**) Cypress USB Keyboard: always reports core events
[     7.583] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event4"
[     7.583] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     7.583] (--) evdev: Cypress USB Keyboard: Found keys
[     7.583] (II) evdev: Cypress USB Keyboard: Configuring as keyboard
[     7.583] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/input/input4/event4"
[     7.583] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: KEYBOARD, id 10)
[     7.583] (**) Option "xkb_rules" "evdev"
[     7.583] (**) Option "xkb_model" "pc105"
[     7.583] (**) Option "xkb_layout" "us"
[     7.583] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event5)
[     7.583] (**) Cypress USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     7.583] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     7.583] (**) Cypress USB Keyboard: always reports core events
[     7.583] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event5"
[     7.583] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     7.583] (--) evdev: Cypress USB Keyboard: Found 1 mouse buttons
[     7.583] (--) evdev: Cypress USB Keyboard: Found scroll wheel(s)
[     7.583] (--) evdev: Cypress USB Keyboard: Found relative axes
[     7.583] (II) evdev: Cypress USB Keyboard: Forcing relative x/y axes to exist.
[     7.583] (--) evdev: Cypress USB Keyboard: Found absolute axes
[     7.583] (II) evdev: Cypress USB Keyboard: Forcing absolute x/y axes to exist.
[     7.583] (--) evdev: Cypress USB Keyboard: Found keys
[     7.583] (II) evdev: Cypress USB Keyboard: Configuring as mouse
[     7.583] (II) evdev: Cypress USB Keyboard: Configuring as keyboard
[     7.583] (II) evdev: Cypress USB Keyboard: Adding scrollwheel support
[     7.583] (**) evdev: Cypress USB Keyboard: YAxisMapping: buttons 4 and 5
[     7.583] (**) evdev: Cypress USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.583] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.1/input/input5/event5"
[     7.583] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: KEYBOARD, id 11)
[     7.583] (**) Option "xkb_rules" "evdev"
[     7.583] (**) Option "xkb_model" "pc105"
[     7.583] (**) Option "xkb_layout" "us"
[     7.583] (II) evdev: Cypress USB Keyboard: initialized for relative axes.
[     7.583] (WW) evdev: Cypress USB Keyboard: ignoring absolute axes.
[     7.583] (**) Cypress USB Keyboard: (accel) keeping acceleration scheme 1
[     7.583] (**) Cypress USB Keyboard: (accel) acceleration profile 0
[     7.583] (**) Cypress USB Keyboard: (accel) acceleration factor: 2.000
[     7.583] (**) Cypress USB Keyboard: (accel) acceleration threshold: 4
[     7.584] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event6)
[     7.584] (**) Cypress USB Keyboard: Applying InputClass "evdev pointer catchall"
[     7.584] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     7.584] (**) Cypress USB Keyboard: always reports core events
[     7.584] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event6"
[     7.584] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     7.584] (--) evdev: Cypress USB Keyboard: Found 9 mouse buttons
[     7.584] (--) evdev: Cypress USB Keyboard: Found scroll wheel(s)
[     7.584] (--) evdev: Cypress USB Keyboard: Found relative axes
[     7.584] (--) evdev: Cypress USB Keyboard: Found x and y relative axes
[     7.584] (II) evdev: Cypress USB Keyboard: Configuring as mouse
[     7.584] (II) evdev: Cypress USB Keyboard: Adding scrollwheel support
[     7.584] (**) evdev: Cypress USB Keyboard: YAxisMapping: buttons 4 and 5
[     7.584] (**) evdev: Cypress USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.584] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.2/input/input6/event6"
[     7.584] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: MOUSE, id 12)
[     7.584] (II) evdev: Cypress USB Keyboard: initialized for relative axes.
[     7.584] (**) Cypress USB Keyboard: (accel) keeping acceleration scheme 1
[     7.584] (**) Cypress USB Keyboard: (accel) acceleration profile 0
[     7.584] (**) Cypress USB Keyboard: (accel) acceleration factor: 2.000
[     7.584] (**) Cypress USB Keyboard: (accel) acceleration threshold: 4
[     7.584] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/mouse0)
[     7.584] (II) No input driver specified, ignoring this device.
[     7.584] (II) This device may have been added with another device file.
[     7.584] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[     7.584] (II) No input driver specified, ignoring this device.
[     7.584] (II) This device may have been added with another device file.
[     7.584] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[     7.584] (II) No input driver specified, ignoring this device.
[     7.584] (II) This device may have been added with another device file.
[     7.584] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event12)
[     7.584] (II) No input driver specified, ignoring this device.
[     7.584] (II) This device may have been added with another device file.
[     7.584] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event7)
[     7.584] (II) No input driver specified, ignoring this device.
[     7.584] (II) This device may have been added with another device file.
[     7.584] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[     7.584] (II) No input driver specified, ignoring this device.
[     7.584] (II) This device may have been added with another device file.
[     7.585] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[     7.585] (II) No input driver specified, ignoring this device.
[     7.585] (II) This device may have been added with another device file.
[     7.744] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     7.744] (II) RADEON(0): Using EDID range info for horizontal sync
[     7.744] (II) RADEON(0): Using EDID range info for vertical refresh
[     7.744] (II) RADEON(0): Printing DDC gathered Modelines:
[     7.744] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.744] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.744] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.744] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.744] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     7.744] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.744] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.744] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.744] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.744] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     7.744] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.744] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.744] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.744] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.744] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.744] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.744] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.744] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.744] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     7.744] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.744] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.744] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.744] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     7.745] (II) RADEON(0): Allocate new frame buffer 5760x1080 stride 5760
[     7.745] (II) RADEON(0): VRAM usage limit set to 1857960K
[     8.032] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     8.032] (II) RADEON(0): Using hsync ranges from config file
[     8.032] (II) RADEON(0): Using vrefresh ranges from config file
[     8.032] (II) RADEON(0): Printing DDC gathered Modelines:
[     8.032] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     8.032] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     8.032] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     8.032] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     8.032] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     8.032] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     8.032] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     8.032] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     8.032] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     8.032] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     8.032] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     8.032] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     8.032] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     8.032] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     8.032] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     8.032] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     8.032] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     8.032] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     8.032] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     8.032] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     8.032] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     8.032] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     8.032] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     8.411] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     8.411] (II) RADEON(0): Using hsync ranges from config file
[     8.411] (II) RADEON(0): Using vrefresh ranges from config file
[     8.411] (II) RADEON(0): Printing DDC gathered Modelines:
[     8.411] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     8.411] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     8.411] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     8.411] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     8.411] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     8.411] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     8.411] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     8.411] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     8.411] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     8.411] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     8.411] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     8.411] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     8.411] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     8.411] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     8.411] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     8.411] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     8.411] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     8.411] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     8.411] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     8.411] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     8.411] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     8.411] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     8.411] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   528.655] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/mouse1)
[   528.655] (II) No input driver specified, ignoring this device.
[   528.655] (II) This device may have been added with another device file.
[   528.655] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/event19)
[   528.655] (**) Logitech Gaming Mouse G400: Applying InputClass "evdev pointer catchall"
[   528.655] (II) Using input driver 'evdev' for 'Logitech Gaming Mouse G400'
[   528.656] (**) Logitech Gaming Mouse G400: always reports core events
[   528.656] (**) evdev: Logitech Gaming Mouse G400: Device: "/dev/input/event19"
[   528.656] (--) evdev: Logitech Gaming Mouse G400: Vendor 0x46d Product 0xc245
[   528.656] (--) evdev: Logitech Gaming Mouse G400: Found 12 mouse buttons
[   528.656] (--) evdev: Logitech Gaming Mouse G400: Found scroll wheel(s)
[   528.656] (--) evdev: Logitech Gaming Mouse G400: Found relative axes
[   528.656] (--) evdev: Logitech Gaming Mouse G400: Found x and y relative axes
[   528.656] (II) evdev: Logitech Gaming Mouse G400: Configuring as mouse
[   528.656] (II) evdev: Logitech Gaming Mouse G400: Adding scrollwheel support
[   528.656] (**) evdev: Logitech Gaming Mouse G400: YAxisMapping: buttons 4 and 5
[   528.656] (**) evdev: Logitech Gaming Mouse G400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   528.656] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input19/event19"
[   528.656] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse G400" (type: MOUSE, id 13)
[   528.656] (II) evdev: Logitech Gaming Mouse G400: initialized for relative axes.
[   528.656] (**) Logitech Gaming Mouse G400: (accel) keeping acceleration scheme 1
[   528.656] (**) Logitech Gaming Mouse G400: (accel) acceleration profile 0
[   528.656] (**) Logitech Gaming Mouse G400: (accel) acceleration factor: 2.000
[   528.656] (**) Logitech Gaming Mouse G400: (accel) acceleration threshold: 4
[   538.050] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   538.050] (II) RADEON(0): Using hsync ranges from config file
[   538.050] (II) RADEON(0): Using vrefresh ranges from config file
[   538.050] (II) RADEON(0): Printing DDC gathered Modelines:
[   538.050] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   538.050] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   538.050] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   538.050] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   538.050] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   538.050] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   538.050] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   538.050] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   538.050] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   538.050] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   538.050] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   538.050] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   538.051] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   538.051] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   538.051] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   538.051] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   538.051] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   538.051] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   538.051] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   538.051] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   538.051] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   538.051] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   538.051] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   538.279] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   538.279] (II) RADEON(0): Using hsync ranges from config file
[   538.279] (II) RADEON(0): Using vrefresh ranges from config file
[   538.279] (II) RADEON(0): Printing DDC gathered Modelines:
[   538.279] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   538.279] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   538.279] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   538.279] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   538.279] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   538.279] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   538.279] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   538.279] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   538.279] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   538.280] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   538.280] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   538.280] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   538.280] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   538.280] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   538.280] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   538.280] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   538.280] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   538.280] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   538.280] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   538.280] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   538.280] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   538.280] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   538.280] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   538.496] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   538.496] (II) RADEON(0): Using hsync ranges from config file
[   538.496] (II) RADEON(0): Using vrefresh ranges from config file
[   538.496] (II) RADEON(0): Printing DDC gathered Modelines:
[   538.496] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   538.496] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   538.496] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   538.496] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   538.496] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   538.496] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   538.496] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   538.496] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   538.496] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   538.496] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   538.496] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   538.496] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   538.496] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   538.496] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   538.496] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   538.496] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   538.496] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   538.496] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   538.496] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   538.496] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   538.496] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   538.496] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   538.496] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   538.635] (II) XKB: reuse xkmfile /var/lib/xkb/server-53A8C5DA194E264601CD74186096751A6970EE1E.xkm
[   539.300] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   539.300] (II) RADEON(0): Using hsync ranges from config file
[   539.300] (II) RADEON(0): Using vrefresh ranges from config file
[   539.300] (II) RADEON(0): Printing DDC gathered Modelines:
[   539.300] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   539.300] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   539.300] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   539.300] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   539.300] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   539.300] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   539.300] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   539.300] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   539.300] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   539.300] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   539.300] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   539.300] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   539.300] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   539.300] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   539.300] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   539.300] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   539.300] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   539.300] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   539.300] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   539.300] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   539.300] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   539.300] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   539.300] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   539.448] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   539.448] (II) RADEON(0): Using hsync ranges from config file
[   539.448] (II) RADEON(0): Using vrefresh ranges from config file
[   539.448] (II) RADEON(0): Printing DDC gathered Modelines:
[   539.448] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   539.448] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   539.448] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   539.448] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   539.448] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   539.448] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   539.448] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   539.448] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   539.448] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   539.448] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   539.448] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   539.448] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   539.448] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   539.448] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   539.448] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   539.448] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   539.448] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   539.448] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   539.448] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   539.448] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   539.448] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   539.448] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   539.448] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   539.596] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   539.596] (II) RADEON(0): Using hsync ranges from config file
[   539.596] (II) RADEON(0): Using vrefresh ranges from config file
[   539.596] (II) RADEON(0): Printing DDC gathered Modelines:
[   539.596] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   539.596] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   539.596] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   539.596] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   539.596] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   539.596] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   539.596] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   539.596] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   539.596] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   539.596] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   539.596] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   539.596] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   539.596] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   539.596] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   539.596] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   539.596] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   539.596] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   539.596] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   539.596] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   539.596] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   539.596] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   539.596] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   539.596] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   539.736] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   539.736] (II) RADEON(0): Using hsync ranges from config file
[   539.736] (II) RADEON(0): Using vrefresh ranges from config file
[   539.736] (II) RADEON(0): Printing DDC gathered Modelines:
[   539.736] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   539.736] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   539.736] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   539.736] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   539.736] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   539.736] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   539.736] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   539.736] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   539.736] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   539.736] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   539.736] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   539.736] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   539.736] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   539.736] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   539.736] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   539.736] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   539.736] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   539.736] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   539.736] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   539.736] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   539.736] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   539.736] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   539.736] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   539.877] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   539.877] (II) RADEON(0): Using hsync ranges from config file
[   539.877] (II) RADEON(0): Using vrefresh ranges from config file
[   539.877] (II) RADEON(0): Printing DDC gathered Modelines:
[   539.877] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   539.877] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   539.877] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   539.877] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   539.877] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   539.877] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   539.877] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   539.877] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   539.877] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   539.877] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   539.877] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   539.877] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   539.877] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   539.877] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   539.877] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   539.877] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   539.877] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   539.877] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   539.877] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   539.877] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   539.877] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   539.877] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   539.877] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   540.020] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   540.020] (II) RADEON(0): Using hsync ranges from config file
[   540.020] (II) RADEON(0): Using vrefresh ranges from config file
[   540.020] (II) RADEON(0): Printing DDC gathered Modelines:
[   540.020] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   540.020] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   540.020] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   540.020] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   540.020] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   540.020] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   540.020] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   540.020] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   540.020] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   540.020] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   540.020] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   540.020] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   540.020] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   540.020] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   540.020] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   540.020] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   540.020] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   540.020] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   540.020] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   540.020] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   540.020] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   540.020] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   540.020] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   540.152] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   540.152] (II) RADEON(0): Using hsync ranges from config file
[   540.152] (II) RADEON(0): Using vrefresh ranges from config file
[   540.152] (II) RADEON(0): Printing DDC gathered Modelines:
[   540.152] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   540.152] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   540.152] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   540.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   540.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   540.152] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   540.152] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   540.152] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   540.152] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   540.152] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   540.152] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   540.152] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   540.152] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   540.152] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   540.152] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   540.152] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   540.152] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   540.152] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   540.152] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   540.152] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   540.152] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   540.152] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   540.152] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   540.292] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   540.292] (II) RADEON(0): Using hsync ranges from config file
[   540.292] (II) RADEON(0): Using vrefresh ranges from config file
[   540.292] (II) RADEON(0): Printing DDC gathered Modelines:
[   540.292] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   540.292] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   540.292] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   540.292] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   540.292] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   540.292] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   540.292] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   540.292] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   540.292] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   540.292] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   540.292] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   540.292] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   540.292] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   540.292] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   540.292] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   540.292] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   540.292] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   540.292] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   540.292] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   540.292] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   540.292] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   540.292] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   540.292] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   540.428] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   540.428] (II) RADEON(0): Using hsync ranges from config file
[   540.428] (II) RADEON(0): Using vrefresh ranges from config file
[   540.428] (II) RADEON(0): Printing DDC gathered Modelines:
[   540.428] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   540.428] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   540.428] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   540.428] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   540.428] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   540.428] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   540.428] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   540.428] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   540.428] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   540.428] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   540.428] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   540.428] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   540.428] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   540.428] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   540.428] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   540.428] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   540.428] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   540.428] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   540.428] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   540.428] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   540.428] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   540.429] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   540.429] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   540.568] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   540.568] (II) RADEON(0): Using hsync ranges from config file
[   540.568] (II) RADEON(0): Using vrefresh ranges from config file
[   540.568] (II) RADEON(0): Printing DDC gathered Modelines:
[   540.568] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   540.568] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   540.568] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   540.568] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   540.568] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   540.568] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   540.568] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   540.568] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   540.568] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   540.568] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   540.568] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   540.568] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   540.568] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   540.568] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   540.568] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   540.568] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   540.568] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   540.568] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   540.568] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   540.568] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   540.568] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   540.568] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   540.568] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   559.152] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   559.152] (II) RADEON(0): Using hsync ranges from config file
[   559.152] (II) RADEON(0): Using vrefresh ranges from config file
[   559.152] (II) RADEON(0): Printing DDC gathered Modelines:
[   559.152] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   559.152] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   559.152] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   559.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   559.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   559.152] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   559.152] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   559.152] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   559.152] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   559.152] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   559.152] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   559.152] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   559.152] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   559.152] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   559.152] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   559.153] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   559.153] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   559.153] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   559.153] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   559.153] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   559.153] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   559.153] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   559.153] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   559.292] (II) RADEON(0): EDID vendor "ACR", prod id 714
[   559.293] (II) RADEON(0): Using hsync ranges from config file
[   559.293] (II) RADEON(0): Using vrefresh ranges from config file
[   559.293] (II) RADEON(0): Printing DDC gathered Modelines:
[   559.293] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   559.293] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   559.293] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   559.293] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   559.293] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   559.293] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   559.293] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   559.293] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   559.293] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   559.293] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   559.293] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   559.293] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   559.293] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   559.293] (II) RAaDEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   559.293] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   559.293] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   559.293] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   559.293] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   559.293] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   559.293] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   559.293] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[   559.293] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   559.293] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)

```

---

### Post by *Legion* on 2013-08-01
> **ssam said:**
> AMD South Island support in the opensource drivers is still a way behind the propriety driver.

That's fine. I'm not looking for peak performance. fglrx has been unstable for me.

Slower DRI is OK, but no DRI is something wrong.

---

### Post by Yellow Pasque on 2013-08-01
Yeah, you need updated llvm and mesa. Try the xorg-edgers PPA (and it's easy to revert with the included ppa-purge package if something goes wrong): [https://launchpad.net/~xorg-edgers/+archive/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ppa/+packages)

---

### Post by *Legion* on 2013-08-01
I'm actually already on xorg-edgers. I just updated to the latest packages, and the result is the same.

Installed packages:
```

% sudo apt-cache policy xserver-xorg-core
  Installed: 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring

% sudo apt-cache policy xserver-xorg-video-radeon
xserver-xorg-video-radeon:
  Installed: 1:7.1.99+git20130730.6a278369-0ubuntu0sarvatt~raring

% sudo apt-cache policy libgl1-mesa-dri
libgl1-mesa-dri:
  Installed: 9.2.0~git20130729+9.2.9b8ad643-0ubuntu0sarvatt~raring

```

glxinfo:
```

% LIBGL_DEBUG=verbose glxinfo
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/brendon/.drirc: No such file or directory.
libGL: Can't open configuration file /home/brendon/.drirc: No such file or directory.
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
... snipped rest ...

```

dmesg:
```

% dmesg | egrep 'drm|radeon'
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.0-27-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-27-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[    5.265312] [drm] Initialized drm 1.1.0 20060810
[    5.287008] [drm] radeon kernel modesetting enabled.
[    5.287149] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6818 0x1682:0x3251).
[    5.287180] [drm] register mmio base: 0xF7E00000
[    5.287181] [drm] register mmio size: 262144
[    5.287322] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    5.287323] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    5.289101] [drm] Detected VRAM RAM=2048M, BAR=256M
[    5.289102] [drm] RAM width 256bits DDR
[    5.289264] [drm] radeon: 2048M of VRAM memory ready
[    5.289264] [drm] radeon: 512M of GTT memory ready.
[    5.289277] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    5.289741] [drm] Loading PITCAIRN Microcode
[    5.679689] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    5.679795] radeon 0000:01:00.0: WB enabled
[    5.679797] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880406b2fc00
[    5.679798] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880406b2fc04
[    5.679800] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880406b2fc08
[    5.679801] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880406b2fc0c
[    5.679802] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880406b2fc10
[    5.679803] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.679804] [drm] Driver supports precise vblank timestamp query.
[    5.679832] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
[    5.679840] radeon 0000:01:00.0: radeon: using MSI.
[    5.679863] [drm] radeon: irq initialized.
[    5.698578] [drm] ring test on 0 succeeded in 4 usecs
[    5.698582] [drm] ring test on 1 succeeded in 1 usecs
[    5.698585] [drm] ring test on 2 succeeded in 1 usecs
[    5.698647] [drm] ring test on 3 succeeded in 2 usecs
[    5.698657] [drm] ring test on 4 succeeded in 1 usecs
[    5.709259] [drm] ib test on ring 0 succeeded in 0 usecs
[    5.709302] [drm] ib test on ring 1 succeeded in 0 usecs
[    5.709344] [drm] ib test on ring 2 succeeded in 0 usecs
[    5.709386] [drm] ib test on ring 3 succeeded in 0 usecs
[    5.709426] [drm] ib test on ring 4 succeeded in 1 usecs
[    5.710099] [drm] Radeon Display Connectors
[    5.710100] [drm] Connector 0:
[    5.710101] [drm]   DP-1
[    5.710102] [drm]   HPD4
[    5.710103] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    5.710103] [drm]   Encoders:
[    5.710104] [drm]     DFP1: INTERNAL_UNIPHY2
[    5.710104] [drm] Connector 1:
[    5.710105] [drm]   DP-2
[    5.710106] [drm]   HPD5
[    5.710106] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    5.710107] [drm]   Encoders:
[    5.710108] [drm]     DFP2: INTERNAL_UNIPHY2
[    5.710108] [drm] Connector 2:
[    5.710109] [drm]   HDMI-A-1
[    5.710109] [drm]   HPD1
[    5.710110] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    5.710111] [drm]   Encoders:
[    5.710111] [drm]     DFP3: INTERNAL_UNIPHY1
[    5.710112] [drm] Connector 3:
[    5.710112] [drm]   DVI-I-1
[    5.710113] [drm]   HPD6
[    5.710114] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    5.710114] [drm]   Encoders:
[    5.710115] [drm]     DFP4: INTERNAL_UNIPHY
[    5.710116] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    5.710116] [drm] Connector 4:
[    5.710117] [drm]   DVI-D-1
[    5.710117] [drm]   HPD3
[    5.710118] [drm]   DDC: 0x6570 0x6570 0x6574 0x6574 0x6578 0x6578 0x657c 0x657c
[    5.710119] [drm]   Encoders:
[    5.710119] [drm]     DFP5: INTERNAL_UNIPHY1
[    5.710171] [drm] Internal thermal controller with fan control
[    5.710197] [drm] radeon: power management initialized
[    5.833255] [drm] fb mappable at 0xE114B000
[    5.833257] [drm] vram apper at 0xE0000000
[    5.833257] [drm] size 8294400
[    5.833258] [drm] fb depth is 24
[    5.833258] [drm]    pitch is 7680
[    5.833323] fbcon: radeondrmfb (fb0) is primary device
[    5.867871] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    5.867872] radeon 0000:01:00.0: registered panic notifier
[    5.867875] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0

```

Xorg.0.log:
```

[     6.393] 
X.Org X Server 1.13.4
Release Date: 2013-04-17
[     6.393] X Protocol Version 11, Revision 0
[     6.393] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[     6.393] Current Operating System: Linux halas 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64
[     6.393] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-27-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[     6.393] Build Date: 08 May 2013  02:34:03PM
[     6.393] xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see http://www.ubuntu.com/support) 
[     6.393] Current version of pixman: 0.28.2
[     6.393] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     6.393] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.393] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  1 15:17:52 2013
[     6.394] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.395] (==) No Layout section.  Using the first Screen section.
[     6.395] (==) No screen section available. Using defaults.
[     6.395] (**) |-->Screen "Default Screen Section" (0)
[     6.395] (**) |   |-->Monitor "<default monitor>"
[     6.395] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     6.395] (==) Automatically adding devices
[     6.395] (==) Automatically enabling devices
[     6.395] (==) Automatically adding GPU devices
[     6.396] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.396] 	Entry deleted from font path.
[     6.396] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.396] 	Entry deleted from font path.
[     6.396] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.396] 	Entry deleted from font path.
[     6.397] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.397] 	Entry deleted from font path.
[     6.397] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.397] 	Entry deleted from font path.
[     6.397] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     6.397] 	Entry deleted from font path.
[     6.397] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     6.397] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.397] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.397] (II) Loader magic: 0x7fe687c24d20
[     6.397] (II) Module ABI versions:
[     6.397] 	X.Org ANSI C Emulation: 0.4
[     6.397] 	X.Org Video Driver: 13.1
[     6.397] 	X.Org XInput driver : 18.0
[     6.397] 	X.Org Server Extension : 7.0
[     6.397] (II) config/udev: Adding drm device (/dev/dri/card0)
[     6.398] (--) PCI:*(0:1:0:0) 1002:6818:1682:3251 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     6.398] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.398] Initializing built-in extension Generic Event Extension
[     6.398] Initializing built-in extension SHAPE
[     6.398] Initializing built-in extension MIT-SHM
[     6.398] Initializing built-in extension XInputExtension
[     6.398] Initializing built-in extension XTEST
[     6.398] Initializing built-in extension BIG-REQUESTS
[     6.398] Initializing built-in extension SYNC
[     6.398] Initializing built-in extension XKEYBOARD
[     6.398] Initializing built-in extension XC-MISC
[     6.398] Initializing built-in extension SECURITY
[     6.398] Initializing built-in extension XINERAMA
[     6.398] Initializing built-in extension XFIXES
[     6.398] Initializing built-in extension RENDER
[     6.398] Initializing built-in extension RANDR
[     6.398] Initializing built-in extension COMPOSITE
[     6.398] Initializing built-in extension DAMAGE
[     6.398] Initializing built-in extension MIT-SCREEN-SAVER
[     6.398] Initializing built-in extension DOUBLE-BUFFER
[     6.398] Initializing built-in extension RECORD
[     6.398] Initializing built-in extension DPMS
[     6.398] Initializing built-in extension X-Resource
[     6.398] Initializing built-in extension XVideo
[     6.398] Initializing built-in extension XVideo-MotionCompensation
[     6.398] Initializing built-in extension SELinux
[     6.398] Initializing built-in extension XFree86-VidModeExtension
[     6.398] Initializing built-in extension XFree86-DGA
[     6.398] Initializing built-in extension XFree86-DRI
[     6.398] Initializing built-in extension DRI2
[     6.398] (II) LoadModule: "glx"
[     6.399] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.401] (II) Module glx: vendor="X.Org Foundation"
[     6.401] 	compiled for 1.13.4, module version = 1.0.0
[     6.401] 	ABI class: X.Org Server Extension, version 7.0
[     6.401] (==) AIGLX enabled
[     6.401] Loading extension GLX
[     6.401] (==) Matched fglrx as autoconfigured driver 0
[     6.401] (==) Matched ati as autoconfigured driver 1
[     6.401] (==) Matched fglrx as autoconfigured driver 2
[     6.401] (==) Matched ati as autoconfigured driver 3
[     6.401] (==) Matched vesa as autoconfigured driver 4
[     6.401] (==) Matched modesetting as autoconfigured driver 5
[     6.401] (==) Matched fbdev as autoconfigured driver 6
[     6.401] (==) Assigned the driver to the xf86ConfigLayout
[     6.401] (II) LoadModule: "fglrx"
[     6.403] (WW) Warning, couldn't open module fglrx
[     6.403] (II) UnloadModule: "fglrx"
[     6.403] (II) Unloading fglrx
[     6.403] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     6.403] (II) LoadModule: "ati"
[     6.403] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     6.403] (II) Module ati: vendor="X.Org Foundation"
[     6.403] 	compiled for 1.13.4, module version = 7.1.99
[     6.403] 	Module class: X.Org Video Driver
[     6.403] 	ABI class: X.Org Video Driver, version 13.1
[     6.403] (II) LoadModule: "radeon"
[     6.403] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     6.405] (II) Module radeon: vendor="X.Org Foundation"
[     6.405] 	compiled for 1.13.4, module version = 7.1.99
[     6.405] 	Module class: X.Org Video Driver
[     6.405] 	ABI class: X.Org Video Driver, version 13.1
[     6.405] (II) LoadModule: "vesa"
[     6.405] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.405] (II) Module vesa: vendor="X.Org Foundation"
[     6.405] 	compiled for 1.12.99.902, module version = 2.3.2
[     6.405] 	Module class: X.Org Video Driver
[     6.405] 	ABI class: X.Org Video Driver, version 13.0
[     6.405] (II) LoadModule: "modesetting"
[     6.405] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.406] (II) Module modesetting: vendor="X.Org Foundation"
[     6.406] 	compiled for 1.13.3, module version = 0.7.0
[     6.406] 	Module class: X.Org Video Driver
[     6.406] 	ABI class: X.Org Video Driver, version 13.1
[     6.406] (II) LoadModule: "fbdev"
[     6.406] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.406] (II) Module fbdev: vendor="X.Org Foundation"
[     6.406] 	compiled for 1.12.99.902, module version = 0.4.3
[     6.406] 	Module class: X.Org Video Driver
[     6.406] 	ABI class: X.Org Video Driver, version 13.0
[     6.406] (==) Matched fglrx as autoconfigured driver 0
[     6.406] (==) Matched ati as autoconfigured driver 1
[     6.406] (==) Matched fglrx as autoconfigured driver 2
[     6.406] (==) Matched ati as autoconfigured driver 3
[     6.406] (==) Matched vesa as autoconfigured driver 4
[     6.406] (==) Matched modesetting as autoconfigured driver 5
[     6.406] (==) Matched fbdev as autoconfigured driver 6
[     6.406] (==) Assigned the driver to the xf86ConfigLayout
[     6.406] (II) LoadModule: "fglrx"
[     6.407] (WW) Warning, couldn't open module fglrx
[     6.407] (II) UnloadModule: "fglrx"
[     6.407] (II) Unloading fglrx
[     6.407] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     6.407] (II) LoadModule: "ati"
[     6.407] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     6.407] (II) Module ati: vendor="X.Org Foundation"
[     6.407] 	compiled for 1.13.4, module version = 7.1.99
[     6.407] 	Module class: X.Org Video Driver
[     6.407] 	ABI class: X.Org Video Driver, version 13.1
[     6.407] (II) LoadModule: "vesa"
[     6.407] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.407] (II) Module vesa: vendor="X.Org Foundation"
[     6.407] 	compiled for 1.12.99.902, module version = 2.3.2
[     6.407] 	Module class: X.Org Video Driver
[     6.407] 	ABI class: X.Org Video Driver, version 13.0
[     6.407] (II) UnloadModule: "vesa"
[     6.407] (II) Unloading vesa
[     6.407] (II) Failed to load module "vesa" (already loaded, 0)
[     6.407] (II) LoadModule: "modesetting"
[     6.407] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.407] (II) Module modesetting: vendor="X.Org Foundation"
[     6.407] 	compiled for 1.13.3, module version = 0.7.0
[     6.407] 	Module class: X.Org Video Driver
[     6.407] 	ABI class: X.Org Video Driver, version 13.1
[     6.407] (II) UnloadModule: "modesetting"
[     6.407] (II) Unloading modesetting
[     6.407] (II) Failed to load module "modesetting" (already loaded, 0)
[     6.407] (II) LoadModule: "fbdev"
[     6.407] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.407] (II) Module fbdev: vendor="X.Org Foundation"
[     6.407] 	compiled for 1.12.99.902, module version = 0.4.3
[     6.407] 	Module class: X.Org Video Driver
[     6.407] 	ABI class: X.Org Video Driver, version 13.0
[     6.407] (II) UnloadModule: "fbdev"
[     6.407] (II) Unloading fbdev
[     6.407] (II) Failed to load module "fbdev" (already loaded, 0)
[     6.407] (II) RADEON: Driver for ATI Radeon chipsets:
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
[     6.409] (II) VESA: driver for VESA chipsets: vesa
[     6.409] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     6.409] (II) FBDEV: driver for framebuffer: fbdev
[     6.409] (++) using VT number 7

[     6.410] (II) [KMS] Kernel modesetting enabled.
[     6.410] (WW) Falling back to old probe method for vesa
[     6.410] (WW) Falling back to old probe method for modesetting
[     6.410] (WW) Falling back to old probe method for fbdev
[     6.410] (II) Loading sub module "fbdevhw"
[     6.410] (II) LoadModule: "fbdevhw"
[     6.410] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.410] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.410] 	compiled for 1.13.4, module version = 0.0.2
[     6.410] 	ABI class: X.Org Video Driver, version 13.1
[     6.410] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     6.410] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[     6.410] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     6.410] (==) RADEON(0): Default visual is TrueColor
[     6.410] (==) RADEON(0): RGB weight 888
[     6.410] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[     6.410] (--) RADEON(0): Chipset: "PITCAIRN" (ChipID = 0x6818)
[     6.410] (II) Loading sub module "dri2"
[     6.410] (II) LoadModule: "dri2"
[     6.410] (II) Module "dri2" already built-in
[     6.410] (II) Loading sub module "shadow"
[     6.410] (II) LoadModule: "shadow"
[     6.410] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     6.411] (II) Module shadow: vendor="X.Org Foundation"
[     6.411] 	compiled for 1.13.4, module version = 1.1.0
[     6.411] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.411] (II) RADEON(0): KMS Color Tiling: disabled
[     6.411] (II) RADEON(0): KMS Color Tiling 2D: disabled
[     6.411] (II) RADEON(0): KMS Pageflipping: enabled
[     6.411] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[     6.424] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[     6.472] (II) RADEON(0): Output DisplayPort-1 has no monitor section
[     6.474] (II) RADEON(0): Output HDMI-0 has no monitor section
[     6.507] (II) RADEON(0): Output DVI-0 has no monitor section
[     6.539] (II) RADEON(0): Output DVI-1 has no monitor section
[     6.552] (II) RADEON(0): EDID for output DisplayPort-0
[     6.600] (II) RADEON(0): EDID for output DisplayPort-1
[     6.600] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 574643103
[     6.600] (II) RADEON(0): Year: 2012  Week: 24
[     6.600] (II) RADEON(0): EDID Version: 1.3
[     6.600] (II) RADEON(0): Digital Display Input
[     6.600] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     6.600] (II) RADEON(0): Gamma: 2.20
[     6.600] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     6.600] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.600] (II) RADEON(0): First detailed timing is preferred mode
[     6.600] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     6.600] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     6.600] (II) RADEON(0): Supported established timings:
[     6.600] (II) RADEON(0): 720x400@70Hz
[     6.600] (II) RADEON(0): 640x480@60Hz
[     6.600] (II) RADEON(0): 640x480@67Hz
[     6.600] (II) RADEON(0): 640x480@72Hz
[     6.600] (II) RADEON(0): 640x480@75Hz
[     6.600] (II) RADEON(0): 800x600@56Hz
[     6.600] (II) RADEON(0): 800x600@60Hz
[     6.600] (II) RADEON(0): 800x600@72Hz
[     6.600] (II) RADEON(0): 800x600@75Hz
[     6.600] (II) RADEON(0): 832x624@75Hz
[     6.600] (II) RADEON(0): 1024x768@60Hz
[     6.600] (II) RADEON(0): 1024x768@70Hz
[     6.600] (II) RADEON(0): 1024x768@75Hz
[     6.600] (II) RADEON(0): 1280x1024@75Hz
[     6.600] (II) RADEON(0): 1152x864@75Hz
[     6.600] (II) RADEON(0): Manufacturer's mask: 0
[     6.600] (II) RADEON(0): Supported standard timings:
[     6.600] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     6.600] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     6.600] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     6.600] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     6.600] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     6.600] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     6.600] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     6.600] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     6.600] (II) RADEON(0): Supported detailed timing:
[     6.600] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     6.600] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.600] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     6.600] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     6.600] (II) RADEON(0): Monitor name: S271HL
[     6.600] (II) RADEON(0): Serial No: LUW0D0108510
[     6.600] (II) RADEON(0): EDID (in hex):
[     6.600] (II) RADEON(0): 	00ffffffffffff000472ca029f5b4022
[     6.600] (II) RADEON(0): 	18160103803c2278ca7b45a4554aa227
[     6.600] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     6.600] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     6.600] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     6.600] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     6.600] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     6.600] (II) RADEON(0): 	004c55573044303130383531300a00cf
[     6.600] (II) RADEON(0): Printing probed modes for output DisplayPort-1
[     6.600] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.600] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.600] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.600] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.600] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.600] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.601] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.601] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.601] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     6.601] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     6.601] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.601] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.601] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.601] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.601] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.601] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.601] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.601] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     6.601] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.601] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.601] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.601] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.603] (II) RADEON(0): EDID for output HDMI-0
[     6.635] (II) RADEON(0): EDID for output DVI-0
[     6.635] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 573634853
[     6.635] (II) RADEON(0): Year: 2012  Week: 23
[     6.635] (II) RADEON(0): EDID Version: 1.3
[     6.635] (II) RADEON(0): Digital Display Input
[     6.635] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     6.635] (II) RADEON(0): Gamma: 2.20
[     6.635] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     6.635] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.635] (II) RADEON(0): First detailed timing is preferred mode
[     6.635] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     6.635] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     6.635] (II) RADEON(0): Supported established timings:
[     6.635] (II) RADEON(0): 720x400@70Hz
[     6.635] (II) RADEON(0): 640x480@60Hz
[     6.635] (II) RADEON(0): 640x480@67Hz
[     6.635] (II) RADEON(0): 640x480@72Hz
[     6.635] (II) RADEON(0): 640x480@75Hz
[     6.635] (II) RADEON(0): 800x600@56Hz
[     6.635] (II) RADEON(0): 800x600@60Hz
[     6.635] (II) RADEON(0): 800x600@72Hz
[     6.635] (II) RADEON(0): 800x600@75Hz
[     6.635] (II) RADEON(0): 832x624@75Hz
[     6.635] (II) RADEON(0): 1024x768@60Hz
[     6.635] (II) RADEON(0): 1024x768@70Hz
[     6.635] (II) RADEON(0): 1024x768@75Hz
[     6.635] (II) RADEON(0): 1280x1024@75Hz
[     6.635] (II) RADEON(0): 1152x864@75Hz
[     6.635] (II) RADEON(0): Manufacturer's mask: 0
[     6.635] (II) RADEON(0): Supported standard timings:
[     6.635] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     6.635] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     6.635] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     6.635] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     6.635] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     6.635] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     6.635] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     6.635] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     6.635] (II) RADEON(0): Supported detailed timing:
[     6.635] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     6.635] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.635] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     6.635] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     6.635] (II) RADEON(0): Monitor name: S271HL
[     6.635] (II) RADEON(0): Serial No: LUW0D0108510
[     6.635] (II) RADEON(0): EDID (in hex):
[     6.635] (II) RADEON(0): 	00ffffffffffff000472ca0225f93022
[     6.635] (II) RADEON(0): 	17160103803c2278ca7b45a4554aa227
[     6.635] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     6.635] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     6.635] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     6.635] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     6.635] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     6.635] (II) RADEON(0): 	004c55573044303130383531300a00bc
[     6.635] (II) RADEON(0): Printing probed modes for output DVI-0
[     6.635] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.635] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.635] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.635] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.635] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.635] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.635] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.635] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.635] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     6.635] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     6.635] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.635] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.635] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.635] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.635] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.635] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.635] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.635] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     6.635] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.635] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.635] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.635] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.668] (II) RADEON(0): EDID for output DVI-1
[     6.668] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 573634863
[     6.668] (II) RADEON(0): Year: 2012  Week: 23
[     6.668] (II) RADEON(0): EDID Version: 1.3
[     6.668] (II) RADEON(0): Digital Display Input
[     6.668] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     6.668] (II) RADEON(0): Gamma: 2.20
[     6.668] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     6.668] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.668] (II) RADEON(0): First detailed timing is preferred mode
[     6.668] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     6.668] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     6.668] (II) RADEON(0): Supported established timings:
[     6.668] (II) RADEON(0): 720x400@70Hz
[     6.668] (II) RADEON(0): 640x480@60Hz
[     6.668] (II) RADEON(0): 640x480@67Hz
[     6.668] (II) RADEON(0): 640x480@72Hz
[     6.668] (II) RADEON(0): 640x480@75Hz
[     6.668] (II) RADEON(0): 800x600@56Hz
[     6.668] (II) RADEON(0): 800x600@60Hz
[     6.668] (II) RADEON(0): 800x600@72Hz
[     6.668] (II) RADEON(0): 800x600@75Hz
[     6.668] (II) RADEON(0): 832x624@75Hz
[     6.668] (II) RADEON(0): 1024x768@60Hz
[     6.668] (II) RADEON(0): 1024x768@70Hz
[     6.668] (II) RADEON(0): 1024x768@75Hz
[     6.668] (II) RADEON(0): 1280x1024@75Hz
[     6.668] (II) RADEON(0): 1152x864@75Hz
[     6.668] (II) RADEON(0): Manufacturer's mask: 0
[     6.668] (II) RADEON(0): Supported standard timings:
[     6.668] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     6.668] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     6.668] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     6.668] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     6.668] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     6.668] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     6.668] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     6.668] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     6.668] (II) RADEON(0): Supported detailed timing:
[     6.668] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     6.668] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.668] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     6.668] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     6.668] (II) RADEON(0): Monitor name: S271HL
[     6.668] (II) RADEON(0): Serial No: LUW0D0108510
[     6.668] (II) RADEON(0): EDID (in hex):
[     6.668] (II) RADEON(0): 	00ffffffffffff000472ca022ff93022
[     6.668] (II) RADEON(0): 	17160103803c2278ca7b45a4554aa227
[     6.668] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     6.668] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     6.668] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     6.668] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     6.668] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     6.668] (II) RADEON(0): 	004c55573044303130383531300a00b2
[     6.668] (II) RADEON(0): Printing probed modes for output DVI-1
[     6.668] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.668] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.668] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.668] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.668] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.668] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.668] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.668] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.668] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     6.668] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     6.668] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.668] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.668] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.668] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.668] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.668] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.668] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.668] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     6.668] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.668] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.668] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.668] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.668] (II) RADEON(0): Output DisplayPort-0 disconnected
[     6.668] (II) RADEON(0): Output DisplayPort-1 connected
[     6.668] (II) RADEON(0): Output HDMI-0 disconnected
[     6.668] (II) RADEON(0): Output DVI-0 connected
[     6.668] (II) RADEON(0): Output DVI-1 connected
[     6.668] (II) RADEON(0): Using exact sizes for initial modes
[     6.668] (II) RADEON(0): Output DisplayPort-1 using initial mode 1920x1080
[     6.668] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080
[     6.668] (II) RADEON(0): Output DVI-1 using initial mode 1920x1080
[     6.668] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     6.668] (II) RADEON(0): mem size init: gart size :1fbdf000 vram size: s:80000000 visible:7f7d7000
[     6.668] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[     6.668] (==) RADEON(0): DPI set to (96, 96)
[     6.668] (II) Loading sub module "fb"
[     6.668] (II) LoadModule: "fb"
[     6.668] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.670] (II) Module fb: vendor="X.Org Foundation"
[     6.670] 	compiled for 1.13.4, module version = 1.0.0
[     6.670] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.670] (II) Loading sub module "ramdac"
[     6.670] (II) LoadModule: "ramdac"
[     6.670] (II) Module "ramdac" already built-in
[     6.670] (II) UnloadModule: "vesa"
[     6.670] (II) Unloading vesa
[     6.670] (II) UnloadModule: "modesetting"
[     6.670] (II) Unloading modesetting
[     6.670] (II) UnloadModule: "fbdev"
[     6.670] (II) Unloading fbdev
[     6.670] (II) UnloadSubModule: "fbdevhw"
[     6.670] (II) Unloading fbdevhw
[     6.670] (--) Depth 24 pixmap format is 32 bpp
[     6.670] (II) RADEON(0): Front buffer size: 8100K
[     6.670] (II) RADEON(0): VRAM usage limit set to 1872540K
[     6.671] (==) RADEON(0): Backing store disabled
[     6.671] (WW) RADEON(0): Direct rendering disabled
[     6.671] (II) RADEON(0): Acceleration disabled
[     6.671] (==) RADEON(0): DPMS enabled
[     6.671] (==) RADEON(0): Silken mouse enabled
[     6.671] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     6.671] (--) RandR disabled
[     6.674] (II) SELinux: Disabled on system
[     6.674] (II) AIGLX: Screen 0 is not DRI2 capable
[     6.674] (II) AIGLX: Screen 0 is not DRI capable
[     6.722] (II) AIGLX: Loaded and initialized swrast
[     6.722] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     6.725] (II) RADEON(0): Setting screen physical size to 508 x 285
[     6.733] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.734] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.734] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.734] (II) LoadModule: "evdev"
[     6.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.735] (II) Module evdev: vendor="X.Org Foundation"
[     6.735] 	compiled for 1.13.3, module version = 2.7.3
[     6.735] 	Module class: X.Org XInput Driver
[     6.735] 	ABI class: X.Org XInput driver, version 18.0
[     6.735] (II) Using input driver 'evdev' for 'Power Button'
[     6.735] (**) Power Button: always reports core events
[     6.735] (**) evdev: Power Button: Device: "/dev/input/event1"
[     6.735] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.735] (--) evdev: Power Button: Found keys
[     6.735] (II) evdev: Power Button: Configuring as keyboard
[     6.735] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     6.735] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.735] (**) Option "xkb_rules" "evdev"
[     6.735] (**) Option "xkb_model" "pc105"
[     6.735] (**) Option "xkb_layout" "us"
[     6.735] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     6.735] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.735] (II) Using input driver 'evdev' for 'Power Button'
[     6.735] (**) Power Button: always reports core events
[     6.735] (**) evdev: Power Button: Device: "/dev/input/event0"
[     6.735] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.735] (--) evdev: Power Button: Found keys
[     6.735] (II) evdev: Power Button: Configuring as keyboard
[     6.735] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     6.735] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     6.735] (**) Option "xkb_rules" "evdev"
[     6.735] (**) Option "xkb_model" "pc105"
[     6.735] (**) Option "xkb_layout" "us"
[     6.736] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     6.736] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     6.736] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event13)
[     6.736] (II) No input driver specified, ignoring this device.
[     6.736] (II) This device may have been added with another device file.
[     6.736] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event14)
[     6.736] (II) No input driver specified, ignoring this device.
[     6.736] (II) This device may have been added with another device file.
[     6.736] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event15)
[     6.736] (II) No input driver specified, ignoring this device.
[     6.736] (II) This device may have been added with another device file.
[     6.736] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event16)
[     6.736] (II) No input driver specified, ignoring this device.
[     6.736] (II) This device may have been added with another device file.
[     6.736] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event17)
[     6.736] (II) No input driver specified, ignoring this device.
[     6.736] (II) This device may have been added with another device file.
[     6.736] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event18)
[     6.736] (II) No input driver specified, ignoring this device.
[     6.736] (II) This device may have been added with another device file.
[     6.736] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[     6.737] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     6.737] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     6.737] (**) HID 04f3:0103: always reports core events
[     6.737] (**) evdev: HID 04f3:0103: Device: "/dev/input/event2"
[     6.737] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[     6.737] (--) evdev: HID 04f3:0103: Found keys
[     6.737] (II) evdev: HID 04f3:0103: Configuring as keyboard
[     6.737] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input2/event2"
[     6.737] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 8)
[     6.737] (**) Option "xkb_rules" "evdev"
[     6.737] (**) Option "xkb_model" "pc105"
[     6.737] (**) Option "xkb_layout" "us"
[     6.737] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[     6.737] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     6.737] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     6.737] (**) HID 04f3:0103: always reports core events
[     6.737] (**) evdev: HID 04f3:0103: Device: "/dev/input/event3"
[     6.737] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[     6.737] (--) evdev: HID 04f3:0103: Found 1 mouse buttons
[     6.737] (--) evdev: HID 04f3:0103: Found scroll wheel(s)
[     6.737] (--) evdev: HID 04f3:0103: Found relative axes
[     6.737] (II) evdev: HID 04f3:0103: Forcing relative x/y axes to exist.
[     6.737] (--) evdev: HID 04f3:0103: Found absolute axes
[     6.737] (II) evdev: HID 04f3:0103: Forcing absolute x/y axes to exist.
[     6.737] (--) evdev: HID 04f3:0103: Found keys
[     6.737] (II) evdev: HID 04f3:0103: Configuring as mouse
[     6.737] (II) evdev: HID 04f3:0103: Configuring as keyboard
[     6.737] (II) evdev: HID 04f3:0103: Adding scrollwheel support
[     6.737] (**) evdev: HID 04f3:0103: YAxisMapping: buttons 4 and 5
[     6.737] (**) evdev: HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.737] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input3/event3"
[     6.737] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 9)
[     6.737] (**) Option "xkb_rules" "evdev"
[     6.737] (**) Option "xkb_model" "pc105"
[     6.737] (**) Option "xkb_layout" "us"
[     6.737] (II) evdev: HID 04f3:0103: initialized for relative axes.
[     6.737] (WW) evdev: HID 04f3:0103: ignoring absolute axes.
[     6.737] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[     6.737] (**) HID 04f3:0103: (accel) acceleration profile 0
[     6.737] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[     6.737] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[     6.737] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event4)
[     6.737] (**) Cypress USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     6.737] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     6.737] (**) Cypress USB Keyboard: always reports core events
[     6.737] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event4"
[     6.737] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     6.737] (--) evdev: Cypress USB Keyboard: Found keys
[     6.737] (II) evdev: Cypress USB Keyboard: Configuring as keyboard
[     6.737] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/input/input4/event4"
[     6.737] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: KEYBOARD, id 10)
[     6.737] (**) Option "xkb_rules" "evdev"
[     6.737] (**) Option "xkb_model" "pc105"
[     6.737] (**) Option "xkb_layout" "us"
[     6.738] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event5)
[     6.738] (**) Cypress USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     6.738] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     6.738] (**) Cypress USB Keyboard: always reports core events
[     6.738] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event5"
[     6.738] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     6.738] (--) evdev: Cypress USB Keyboard: Found 1 mouse buttons
[     6.738] (--) evdev: Cypress USB Keyboard: Found scroll wheel(s)
[     6.738] (--) evdev: Cypress USB Keyboard: Found relative axes
[     6.738] (II) evdev: Cypress USB Keyboard: Forcing relative x/y axes to exist.
[     6.738] (--) evdev: Cypress USB Keyboard: Found absolute axes
[     6.738] (II) evdev: Cypress USB Keyboard: Forcing absolute x/y axes to exist.
[     6.738] (--) evdev: Cypress USB Keyboard: Found keys
[     6.738] (II) evdev: Cypress USB Keyboard: Configuring as mouse
[     6.738] (II) evdev: Cypress USB Keyboard: Configuring as keyboard
[     6.738] (II) evdev: Cypress USB Keyboard: Adding scrollwheel support
[     6.738] (**) evdev: Cypress USB Keyboard: YAxisMapping: buttons 4 and 5
[     6.738] (**) evdev: Cypress USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.738] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.1/input/input5/event5"
[     6.738] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: KEYBOARD, id 11)
[     6.738] (**) Option "xkb_rules" "evdev"
[     6.738] (**) Option "xkb_model" "pc105"
[     6.738] (**) Option "xkb_layout" "us"
[     6.738] (II) evdev: Cypress USB Keyboard: initialized for relative axes.
[     6.738] (WW) evdev: Cypress USB Keyboard: ignoring absolute axes.
[     6.738] (**) Cypress USB Keyboard: (accel) keeping acceleration scheme 1
[     6.738] (**) Cypress USB Keyboard: (accel) acceleration profile 0
[     6.738] (**) Cypress USB Keyboard: (accel) acceleration factor: 2.000
[     6.738] (**) Cypress USB Keyboard: (accel) acceleration threshold: 4
[     6.738] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event6)
[     6.738] (**) Cypress USB Keyboard: Applying InputClass "evdev pointer catchall"
[     6.738] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     6.738] (**) Cypress USB Keyboard: always reports core events
[     6.738] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event6"
[     6.738] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     6.738] (--) evdev: Cypress USB Keyboard: Found 9 mouse buttons
[     6.738] (--) evdev: Cypress USB Keyboard: Found scroll wheel(s)
[     6.738] (--) evdev: Cypress USB Keyboard: Found relative axes
[     6.738] (--) evdev: Cypress USB Keyboard: Found x and y relative axes
[     6.738] (II) evdev: Cypress USB Keyboard: Configuring as mouse
[     6.738] (II) evdev: Cypress USB Keyboard: Adding scrollwheel support
[     6.738] (**) evdev: Cypress USB Keyboard: YAxisMapping: buttons 4 and 5
[     6.738] (**) evdev: Cypress USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.738] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.2/input/input6/event6"
[     6.738] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: MOUSE, id 12)
[     6.738] (II) evdev: Cypress USB Keyboard: initialized for relative axes.
[     6.738] (**) Cypress USB Keyboard: (accel) keeping acceleration scheme 1
[     6.738] (**) Cypress USB Keyboard: (accel) acceleration profile 0
[     6.738] (**) Cypress USB Keyboard: (accel) acceleration factor: 2.000
[     6.738] (**) Cypress USB Keyboard: (accel) acceleration threshold: 4
[     6.738] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/mouse0)
[     6.738] (II) No input driver specified, ignoring this device.
[     6.738] (II) This device may have been added with another device file.
[     6.739] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[     6.739] (II) No input driver specified, ignoring this device.
[     6.739] (II) This device may have been added with another device file.
[     6.739] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[     6.739] (II) No input driver specified, ignoring this device.
[     6.739] (II) This device may have been added with another device file.
[     6.739] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event12)
[     6.739] (II) No input driver specified, ignoring this device.
[     6.739] (II) This device may have been added with another device file.
[     6.739] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event7)
[     6.739] (II) No input driver specified, ignoring this device.
[     6.739] (II) This device may have been added with another device file.
[     6.739] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[     6.739] (II) No input driver specified, ignoring this device.
[     6.739] (II) This device may have been added with another device file.
[     6.739] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[     6.739] (II) No input driver specified, ignoring this device.
[     6.739] (II) This device may have been added with another device file.
[     6.900] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     6.900] (II) RADEON(0): Using EDID range info for horizontal sync
[     6.900] (II) RADEON(0): Using EDID range info for vertical refresh
[     6.900] (II) RADEON(0): Printing DDC gathered Modelines:
[     6.900] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.900] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.900] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.900] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.900] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     6.900] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.900] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.900] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.900] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.900] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     6.900] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.900] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.900] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.900] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.900] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.900] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.900] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.900] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.900] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     6.900] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.900] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.900] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.900] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     6.901] (II) RADEON(0): Allocate new frame buffer 5760x1080 stride 5760
[     6.901] (II) RADEON(0): VRAM usage limit set to 1857960K
[     7.256] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     7.256] (II) RADEON(0): Using hsync ranges from config file
[     7.256] (II) RADEON(0): Using vrefresh ranges from config file
[     7.256] (II) RADEON(0): Printing DDC gathered Modelines:
[     7.256] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.256] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.256] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.256] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.256] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     7.256] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.256] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.256] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.256] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.256] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     7.256] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.256] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.256] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.256] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.256] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.256] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.256] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.256] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.256] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     7.256] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.256] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.256] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.256] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     7.592] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     7.592] (II) RADEON(0): Using hsync ranges from config file
[     7.592] (II) RADEON(0): Using vrefresh ranges from config file
[     7.592] (II) RADEON(0): Printing DDC gathered Modelines:
[     7.592] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.592] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.592] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.592] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.592] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     7.592] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.592] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.592] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.592] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.592] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     7.592] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.592] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.592] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.592] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.592] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.592] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.592] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.592] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.592] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     7.592] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.592] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.592] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.592] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1741.808] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/mouse1)
[  1741.808] (II) No input driver specified, ignoring this device.
[  1741.808] (II) This device may have been added with another device file.
[  1741.808] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/event19)
[  1741.808] (**) Logitech Gaming Mouse G400: Applying InputClass "evdev pointer catchall"
[  1741.808] (II) Using input driver 'evdev' for 'Logitech Gaming Mouse G400'
[  1741.808] (**) Logitech Gaming Mouse G400: always reports core events
[  1741.808] (**) evdev: Logitech Gaming Mouse G400: Device: "/dev/input/event19"
[  1741.808] (--) evdev: Logitech Gaming Mouse G400: Vendor 0x46d Product 0xc245
[  1741.808] (--) evdev: Logitech Gaming Mouse G400: Found 12 mouse buttons
[  1741.808] (--) evdev: Logitech Gaming Mouse G400: Found scroll wheel(s)
[  1741.808] (--) evdev: Logitech Gaming Mouse G400: Found relative axes
[  1741.809] (--) evdev: Logitech Gaming Mouse G400: Found x and y relative axes
[  1741.809] (II) evdev: Logitech Gaming Mouse G400: Configuring as mouse
[  1741.809] (II) evdev: Logitech Gaming Mouse G400: Adding scrollwheel support
[  1741.809] (**) evdev: Logitech Gaming Mouse G400: YAxisMapping: buttons 4 and 5
[  1741.809] (**) evdev: Logitech Gaming Mouse G400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1741.809] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input19/event19"
[  1741.809] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse G400" (type: MOUSE, id 13)
[  1741.809] (II) evdev: Logitech Gaming Mouse G400: initialized for relative axes.
[  1741.809] (**) Logitech Gaming Mouse G400: (accel) keeping acceleration scheme 1
[  1741.809] (**) Logitech Gaming Mouse G400: (accel) acceleration profile 0
[  1741.809] (**) Logitech Gaming Mouse G400: (accel) acceleration factor: 2.000
[  1741.809] (**) Logitech Gaming Mouse G400: (accel) acceleration threshold: 4
[  1751.286] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1751.286] (II) RADEON(0): Using hsync ranges from config file
[  1751.286] (II) RADEON(0): Using vrefresh ranges from config file
[  1751.286] (II) RADEON(0): Printing DDC gathered Modelines:
[  1751.286] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1751.286] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1751.286] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1751.286] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1751.286] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1751.286] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1751.286] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1751.286] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1751.286] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1751.286] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1751.286] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1751.286] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1751.287] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1751.287] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1751.287] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1751.287] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1751.287] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1751.492] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1751.492] (II) RADEON(0): Using hsync ranges from config file
[  1751.492] (II) RADEON(0): Using vrefresh ranges from config file
[  1751.492] (II) RADEON(0): Printing DDC gathered Modelines:
[  1751.492] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1751.492] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1751.492] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1751.492] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1751.492] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1751.492] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1751.492] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1751.492] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1751.492] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1751.492] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1751.492] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1751.492] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1751.713] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1751.713] (II) RADEON(0): Using hsync ranges from config file
[  1751.713] (II) RADEON(0): Using vrefresh ranges from config file
[  1751.713] (II) RADEON(0): Printing DDC gathered Modelines:
[  1751.713] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1751.713] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1751.713] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1751.713] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1751.713] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1751.713] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1751.713] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1751.713] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1751.713] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1751.713] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1751.713] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1751.713] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1751.846] (II) XKB: reuse xkmfile /var/lib/xkb/server-53A8C5DA194E264601CD74186096751A6970EE1E.xkm
[  1752.612] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1752.612] (II) RADEON(0): Using hsync ranges from config file
[  1752.612] (II) RADEON(0): Using vrefresh ranges from config file
[  1752.612] (II) RADEON(0): Printing DDC gathered Modelines:
[  1752.612] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1752.612] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1752.612] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1752.612] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1752.612] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1752.612] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1752.612] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1752.612] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1752.612] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1752.612] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1752.612] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1752.612] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1752.756] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1752.756] (II) RADEON(0): Using hsync ranges from config file
[  1752.756] (II) RADEON(0): Using vrefresh ranges from config file
[  1752.756] (II) RADEON(0): Printing DDC gathered Modelines:
[  1752.756] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1752.756] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1752.756] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1752.756] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1752.756] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1752.756] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1752.756] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1752.756] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1752.756] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1752.756] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1752.756] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1752.756] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1752.896] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1752.897] (II) RADEON(0): Using hsync ranges from config file
[  1752.897] (II) RADEON(0): Using vrefresh ranges from config file
[  1752.897] (II) RADEON(0): Printing DDC gathered Modelines:
[  1752.897] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1752.897] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1752.897] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1752.897] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1752.897] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1752.897] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1752.897] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1752.897] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1752.897] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1752.897] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1752.897] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1752.897] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.036] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.036] (II) RADEON(0): Using hsync ranges from config file
[  1753.036] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.036] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.036] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.036] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.037] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.037] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.037] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.037] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.037] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.037] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.037] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.037] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.037] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.037] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.168] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.168] (II) RADEON(0): Using hsync ranges from config file
[  1753.168] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.168] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.168] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.168] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.168] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.168] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.168] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.168] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.168] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.168] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.168] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.168] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.168] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.168] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.328] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.328] (II) RADEON(0): Using hsync ranges from config file
[  1753.328] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.328] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.328] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.328] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.328] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.328] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.328] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.328] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.328] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.328] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.328] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.328] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.328] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.328] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.466] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.466] (II) RADEON(0): Using hsync ranges from config file
[  1753.466] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.466] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.466] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.466] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.466] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.466] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.466] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.466] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.466] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.466] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.466] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.466] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.466] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.466] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.608] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.608] (II) RADEON(0): Using hsync ranges from config file
[  1753.608] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.608] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.608] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.608] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.608] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.608] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.608] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.608] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.608] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.608] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.608] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.608] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.608] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.608] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.608] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.608] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.609] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.609] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.740] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.740] (II) RADEON(0): Using hsync ranges from config file
[  1753.740] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.740] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.740] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.740] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.740] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.740] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.740] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.740] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.740] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.740] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.740] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.740] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.740] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.740] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1753.880] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1753.880] (II) RADEON(0): Using hsync ranges from config file
[  1753.880] (II) RADEON(0): Using vrefresh ranges from config file
[  1753.880] (II) RADEON(0): Printing DDC gathered Modelines:
[  1753.880] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1753.880] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1753.880] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1753.880] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1753.880] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1753.880] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1753.880] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1753.880] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1753.880] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1753.880] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1753.880] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1753.880] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1772.336] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1772.336] (II) RADEON(0): Using hsync ranges from config file
[  1772.336] (II) RADEON(0): Using vrefresh ranges from config file
[  1772.336] (II) RADEON(0): Printing DDC gathered Modelines:
[  1772.336] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1772.336] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1772.336] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1772.336] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1772.336] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1772.336] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1772.336] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1772.336] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1772.336] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1772.336] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1772.336] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1772.336] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[  1772.468] (II) RADEON(0): EDID vendor "ACR", prod id 714
[  1772.468] (II) RADEON(0): Using hsync ranges from config file
[  1772.468] (II) RADEON(0): Using vrefresh ranges from config file
[  1772.468] (II) RADEON(0): Printing DDC gathered Modelines:
[  1772.468] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1772.468] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1772.468] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1772.468] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1772.468] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1772.468] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1772.468] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1772.468] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1772.468] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1772.468] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1772.468] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  1772.468] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)

```

---

### Post by Yellow Pasque on 2013-08-01
Ah, I see xorg-edgers still isn't building the radeonsi module, which is kind of odd because they have llvm 3.3 in their repo:
```
mesa (9.2.0~git20130729+9.2.9b8ad643-0ubuntu0sarvatt~raring) raring; urgency=critical
  * hook: Don't build radeonsi, requires llvm-3.3.
.
```

I would purge the xorg-edgers stuff (sudo ppa-purge xorg-edgers) and try oibaf's ppa: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

---

### Post by *Legion* on 2013-08-01
Unfortunately, this does not appear to have gotten me anywhere.

Installed:
```

% sudo apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.13.3-0ubuntu6

% sudo apt-cache policy xserver-xorg-video-radeon
xserver-xorg-video-radeon:
  Installed: 1:7.1.0+git1307310858.6a2783~gd~r

%  sudo apt-cache policy libgl1-mesa-dri
libgl1-mesa-dri:
  Installed: 9.3~git1307310940.7568a8~gd~r

% sudo apt-cache policy libllvm3.3
libllvm3.3:
  Installed: 1:3.3-3~r~gd

```

glxinfo:
```

% LIBGL_DEBUG=verbose glxinfo
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/brendon/.drirc: No such file or directory.
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
... snipped rest ...

```

dmesg:
```

% dmesg | egrep 'drm|radeon'
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.0-27-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-27-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[    5.255845] [drm] Initialized drm 1.1.0 20060810
[    5.267072] [drm] radeon kernel modesetting enabled.
[    5.267259] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6818 0x1682:0x3251).
[    5.267291] [drm] register mmio base: 0xF7E00000
[    5.267292] [drm] register mmio size: 262144
[    5.267378] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    5.267380] radeon 0000:01:00.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[    5.269044] [drm] Detected VRAM RAM=2048M, BAR=256M
[    5.269046] [drm] RAM width 256bits DDR
[    5.273733] [drm] radeon: 2048M of VRAM memory ready
[    5.273734] [drm] radeon: 512M of GTT memory ready.
[    5.273744] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    5.274097] [drm] Loading PITCAIRN Microcode
[    5.675514] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    5.675616] radeon 0000:01:00.0: WB enabled
[    5.675618] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880404092c00
[    5.675620] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880404092c04
[    5.675621] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880404092c08
[    5.675622] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880404092c0c
[    5.675623] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880404092c10
[    5.675624] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.675625] [drm] Driver supports precise vblank timestamp query.
[    5.675651] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
[    5.675658] radeon 0000:01:00.0: radeon: using MSI.
[    5.675679] [drm] radeon: irq initialized.
[    5.694353] [drm] ring test on 0 succeeded in 4 usecs
[    5.694356] [drm] ring test on 1 succeeded in 1 usecs
[    5.694360] [drm] ring test on 2 succeeded in 1 usecs
[    5.694421] [drm] ring test on 3 succeeded in 2 usecs
[    5.694430] [drm] ring test on 4 succeeded in 1 usecs
[    5.704967] [drm] ib test on ring 0 succeeded in 0 usecs
[    5.705015] [drm] ib test on ring 1 succeeded in 0 usecs
[    5.705056] [drm] ib test on ring 2 succeeded in 0 usecs
[    5.705095] [drm] ib test on ring 3 succeeded in 0 usecs
[    5.705135] [drm] ib test on ring 4 succeeded in 1 usecs
[    5.705821] [drm] Radeon Display Connectors
[    5.705821] [drm] Connector 0:
[    5.705822] [drm]   DP-1
[    5.705823] [drm]   HPD4
[    5.705824] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    5.705824] [drm]   Encoders:
[    5.705825] [drm]     DFP1: INTERNAL_UNIPHY2
[    5.705826] [drm] Connector 1:
[    5.705826] [drm]   DP-2
[    5.705827] [drm]   HPD5
[    5.705828] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    5.705828] [drm]   Encoders:
[    5.705829] [drm]     DFP2: INTERNAL_UNIPHY2
[    5.705829] [drm] Connector 2:
[    5.705830] [drm]   HDMI-A-1
[    5.705830] [drm]   HPD1
[    5.705831] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    5.705832] [drm]   Encoders:
[    5.705832] [drm]     DFP3: INTERNAL_UNIPHY1
[    5.705833] [drm] Connector 3:
[    5.705834] [drm]   DVI-I-1
[    5.705834] [drm]   HPD6
[    5.705835] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    5.705836] [drm]   Encoders:
[    5.705836] [drm]     DFP4: INTERNAL_UNIPHY
[    5.705837] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    5.705837] [drm] Connector 4:
[    5.705838] [drm]   DVI-D-1
[    5.705839] [drm]   HPD3
[    5.705839] [drm]   DDC: 0x6570 0x6570 0x6574 0x6574 0x6578 0x6578 0x657c 0x657c
[    5.705840] [drm]   Encoders:
[    5.705841] [drm]     DFP5: INTERNAL_UNIPHY1
[    5.705892] [drm] Internal thermal controller with fan control
[    5.705935] [drm] radeon: power management initialized
[    5.829378] [drm] fb mappable at 0xE114B000
[    5.829379] [drm] vram apper at 0xE0000000
[    5.829380] [drm] size 8294400
[    5.829381] [drm] fb depth is 24
[    5.829381] [drm]    pitch is 7680
[    5.829436] fbcon: radeondrmfb (fb0) is primary device
[    5.863817] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    5.863819] radeon 0000:01:00.0: registered panic notifier
[    5.863822] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0

```

Xorg.0.log
```

[     6.376] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[     6.376] X Protocol Version 11, Revision 0
[     6.376] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     6.376] Current Operating System: Linux halas 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64
[     6.376] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-27-generic root=/dev/mapper/UBUNTU-ROOT ro radeon.modeset=1 quiet splash vt.handoff=7
[     6.376] Build Date: 17 April 2013  10:43:13PM
[     6.376] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[     6.376] Current version of pixman: 0.28.2
[     6.376] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     6.376] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.376] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug  1 18:34:45 2013
[     6.377] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.377] (==) No Layout section.  Using the first Screen section.
[     6.377] (==) No screen section available. Using defaults.
[     6.377] (**) |-->Screen "Default Screen Section" (0)
[     6.377] (**) |   |-->Monitor "<default monitor>"
[     6.377] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     6.377] (==) Automatically adding devices
[     6.377] (==) Automatically enabling devices
[     6.377] (==) Automatically adding GPU devices
[     6.377] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.377] 	Entry deleted from font path.
[     6.377] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.377] 	Entry deleted from font path.
[     6.377] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.377] 	Entry deleted from font path.
[     6.377] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.377] 	Entry deleted from font path.
[     6.377] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.377] 	Entry deleted from font path.
[     6.377] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     6.377] 	Entry deleted from font path.
[     6.377] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     6.377] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.377] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.377] (II) Loader magic: 0x7f3f32278d20
[     6.377] (II) Module ABI versions:
[     6.377] 	X.Org ANSI C Emulation: 0.4
[     6.377] 	X.Org Video Driver: 13.1
[     6.377] 	X.Org XInput driver : 18.0
[     6.377] 	X.Org Server Extension : 7.0
[     6.377] (II) config/udev: Adding drm device (/dev/dri/card0)
[     6.378] (--) PCI:*(0:1:0:0) 1002:6818:1682:3251 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     6.378] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.378] Initializing built-in extension Generic Event Extension
[     6.378] Initializing built-in extension SHAPE
[     6.378] Initializing built-in extension MIT-SHM
[     6.378] Initializing built-in extension XInputExtension
[     6.378] Initializing built-in extension XTEST
[     6.378] Initializing built-in extension BIG-REQUESTS
[     6.378] Initializing built-in extension SYNC
[     6.378] Initializing built-in extension XKEYBOARD
[     6.378] Initializing built-in extension XC-MISC
[     6.378] Initializing built-in extension SECURITY
[     6.378] Initializing built-in extension XINERAMA
[     6.378] Initializing built-in extension XFIXES
[     6.378] Initializing built-in extension RENDER
[     6.378] Initializing built-in extension RANDR
[     6.378] Initializing built-in extension COMPOSITE
[     6.378] Initializing built-in extension DAMAGE
[     6.378] Initializing built-in extension MIT-SCREEN-SAVER
[     6.378] Initializing built-in extension DOUBLE-BUFFER
[     6.378] Initializing built-in extension RECORD
[     6.378] Initializing built-in extension DPMS
[     6.378] Initializing built-in extension X-Resource
[     6.378] Initializing built-in extension XVideo
[     6.378] Initializing built-in extension XVideo-MotionCompensation
[     6.378] Initializing built-in extension SELinux
[     6.378] Initializing built-in extension XFree86-VidModeExtension
[     6.378] Initializing built-in extension XFree86-DGA
[     6.378] Initializing built-in extension XFree86-DRI
[     6.378] Initializing built-in extension DRI2
[     6.378] (II) LoadModule: "glx"
[     6.379] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.379] (II) Module glx: vendor="X.Org Foundation"
[     6.379] 	compiled for 1.13.3, module version = 1.0.0
[     6.379] 	ABI class: X.Org Server Extension, version 7.0
[     6.379] (==) AIGLX enabled
[     6.379] Loading extension GLX
[     6.379] (==) Matched fglrx as autoconfigured driver 0
[     6.379] (==) Matched ati as autoconfigured driver 1
[     6.379] (==) Matched fglrx as autoconfigured driver 2
[     6.379] (==) Matched ati as autoconfigured driver 3
[     6.379] (==) Matched vesa as autoconfigured driver 4
[     6.379] (==) Matched modesetting as autoconfigured driver 5
[     6.379] (==) Matched fbdev as autoconfigured driver 6
[     6.379] (==) Assigned the driver to the xf86ConfigLayout
[     6.379] (II) LoadModule: "fglrx"
[     6.380] (WW) Warning, couldn't open module fglrx
[     6.380] (II) UnloadModule: "fglrx"
[     6.380] (II) Unloading fglrx
[     6.380] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     6.380] (II) LoadModule: "ati"
[     6.380] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     6.380] (II) Module ati: vendor="X.Org Foundation"
[     6.380] 	compiled for 1.13.3, module version = 7.1.99
[     6.380] 	Module class: X.Org Video Driver
[     6.380] 	ABI class: X.Org Video Driver, version 13.1
[     6.380] (II) LoadModule: "radeon"
[     6.380] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     6.387] (II) Module radeon: vendor="X.Org Foundation"
[     6.387] 	compiled for 1.13.3, module version = 7.1.99
[     6.387] 	Module class: X.Org Video Driver
[     6.387] 	ABI class: X.Org Video Driver, version 13.1
[     6.387] (II) LoadModule: "vesa"
[     6.387] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.387] (II) Module vesa: vendor="X.Org Foundation"
[     6.387] 	compiled for 1.12.99.902, module version = 2.3.2
[     6.387] 	Module class: X.Org Video Driver
[     6.387] 	ABI class: X.Org Video Driver, version 13.0
[     6.387] (II) LoadModule: "modesetting"
[     6.387] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.387] (II) Module modesetting: vendor="X.Org Foundation"
[     6.387] 	compiled for 1.13.3, module version = 0.7.0
[     6.387] 	Module class: X.Org Video Driver
[     6.387] 	ABI class: X.Org Video Driver, version 13.1
[     6.387] (II) LoadModule: "fbdev"
[     6.387] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.387] (II) Module fbdev: vendor="X.Org Foundation"
[     6.387] 	compiled for 1.12.99.902, module version = 0.4.3
[     6.387] 	Module class: X.Org Video Driver
[     6.387] 	ABI class: X.Org Video Driver, version 13.0
[     6.387] (==) Matched fglrx as autoconfigured driver 0
[     6.387] (==) Matched ati as autoconfigured driver 1
[     6.387] (==) Matched fglrx as autoconfigured driver 2
[     6.387] (==) Matched ati as autoconfigured driver 3
[     6.387] (==) Matched vesa as autoconfigured driver 4
[     6.387] (==) Matched modesetting as autoconfigured driver 5
[     6.387] (==) Matched fbdev as autoconfigured driver 6
[     6.387] (==) Assigned the driver to the xf86ConfigLayout
[     6.387] (II) LoadModule: "fglrx"
[     6.388] (WW) Warning, couldn't open module fglrx
[     6.388] (II) UnloadModule: "fglrx"
[     6.388] (II) Unloading fglrx
[     6.388] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     6.388] (II) LoadModule: "ati"
[     6.388] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     6.388] (II) Module ati: vendor="X.Org Foundation"
[     6.388] 	compiled for 1.13.3, module version = 7.1.99
[     6.388] 	Module class: X.Org Video Driver
[     6.388] 	ABI class: X.Org Video Driver, version 13.1
[     6.388] (II) LoadModule: "vesa"
[     6.388] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.388] (II) Module vesa: vendor="X.Org Foundation"
[     6.388] 	compiled for 1.12.99.902, module version = 2.3.2
[     6.388] 	Module class: X.Org Video Driver
[     6.388] 	ABI class: X.Org Video Driver, version 13.0
[     6.388] (II) UnloadModule: "vesa"
[     6.388] (II) Unloading vesa
[     6.388] (II) Failed to load module "vesa" (already loaded, 0)
[     6.388] (II) LoadModule: "modesetting"
[     6.388] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.388] (II) Module modesetting: vendor="X.Org Foundation"
[     6.388] 	compiled for 1.13.3, module version = 0.7.0
[     6.388] 	Module class: X.Org Video Driver
[     6.388] 	ABI class: X.Org Video Driver, version 13.1
[     6.388] (II) UnloadModule: "modesetting"
[     6.388] (II) Unloading modesetting
[     6.388] (II) Failed to load module "modesetting" (already loaded, 0)
[     6.388] (II) LoadModule: "fbdev"
[     6.388] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.388] (II) Module fbdev: vendor="X.Org Foundation"
[     6.388] 	compiled for 1.12.99.902, module version = 0.4.3
[     6.388] 	Module class: X.Org Video Driver
[     6.388] 	ABI class: X.Org Video Driver, version 13.0
[     6.388] (II) UnloadModule: "fbdev"
[     6.388] (II) Unloading fbdev
[     6.388] (II) Failed to load module "fbdev" (already loaded, 0)
[     6.388] (II) RADEON: Driver for ATI Radeon chipsets:
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
[     6.390] (II) VESA: driver for VESA chipsets: vesa
[     6.390] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     6.390] (II) FBDEV: driver for framebuffer: fbdev
[     6.390] (++) using VT number 7

[     6.390] (II) [KMS] Kernel modesetting enabled.
[     6.390] (WW) Falling back to old probe method for vesa
[     6.390] (WW) Falling back to old probe method for modesetting
[     6.390] (WW) Falling back to old probe method for fbdev
[     6.390] (II) Loading sub module "fbdevhw"
[     6.390] (II) LoadModule: "fbdevhw"
[     6.390] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.390] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.390] 	compiled for 1.13.3, module version = 0.0.2
[     6.390] 	ABI class: X.Org Video Driver, version 13.1
[     6.390] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     6.390] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[     6.390] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     6.390] (==) RADEON(0): Default visual is TrueColor
[     6.390] (==) RADEON(0): RGB weight 888
[     6.390] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[     6.390] (--) RADEON(0): Chipset: "PITCAIRN" (ChipID = 0x6818)
[     6.390] (II) Loading sub module "dri2"
[     6.390] (II) LoadModule: "dri2"
[     6.390] (II) Module "dri2" already built-in
[     6.390] (WW) RADEON(0): glamor requires Load "glamoregl" in Section "Module", disabling.
[     6.390] (II) Loading sub module "shadow"
[     6.390] (II) LoadModule: "shadow"
[     6.390] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     6.390] (II) Module shadow: vendor="X.Org Foundation"
[     6.390] 	compiled for 1.13.3, module version = 1.1.0
[     6.390] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.390] (II) RADEON(0): KMS Color Tiling: disabled
[     6.390] (II) RADEON(0): KMS Color Tiling 2D: disabled
[     6.390] (II) RADEON(0): KMS Pageflipping: enabled
[     6.390] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[     6.404] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[     6.452] (II) RADEON(0): Output DisplayPort-1 has no monitor section
[     6.454] (II) RADEON(0): Output HDMI-0 has no monitor section
[     6.487] (II) RADEON(0): Output DVI-0 has no monitor section
[     6.519] (II) RADEON(0): Output DVI-1 has no monitor section
[     6.532] (II) RADEON(0): EDID for output DisplayPort-0
[     6.580] (II) RADEON(0): EDID for output DisplayPort-1
[     6.580] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 574643103
[     6.580] (II) RADEON(0): Year: 2012  Week: 24
[     6.580] (II) RADEON(0): EDID Version: 1.3
[     6.580] (II) RADEON(0): Digital Display Input
[     6.580] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     6.580] (II) RADEON(0): Gamma: 2.20
[     6.580] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     6.580] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.580] (II) RADEON(0): First detailed timing is preferred mode
[     6.580] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     6.580] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     6.580] (II) RADEON(0): Supported established timings:
[     6.580] (II) RADEON(0): 720x400@70Hz
[     6.580] (II) RADEON(0): 640x480@60Hz
[     6.580] (II) RADEON(0): 640x480@67Hz
[     6.580] (II) RADEON(0): 640x480@72Hz
[     6.580] (II) RADEON(0): 640x480@75Hz
[     6.580] (II) RADEON(0): 800x600@56Hz
[     6.580] (II) RADEON(0): 800x600@60Hz
[     6.580] (II) RADEON(0): 800x600@72Hz
[     6.580] (II) RADEON(0): 800x600@75Hz
[     6.580] (II) RADEON(0): 832x624@75Hz
[     6.580] (II) RADEON(0): 1024x768@60Hz
[     6.580] (II) RADEON(0): 1024x768@70Hz
[     6.580] (II) RADEON(0): 1024x768@75Hz
[     6.580] (II) RADEON(0): 1280x1024@75Hz
[     6.580] (II) RADEON(0): 1152x864@75Hz
[     6.580] (II) RADEON(0): Manufacturer's mask: 0
[     6.580] (II) RADEON(0): Supported standard timings:
[     6.580] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     6.580] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     6.580] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     6.580] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     6.580] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     6.580] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     6.580] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     6.580] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     6.580] (II) RADEON(0): Supported detailed timing:
[     6.580] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     6.580] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.580] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     6.580] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     6.581] (II) RADEON(0): Monitor name: S271HL
[     6.581] (II) RADEON(0): Serial No: LUW0D0108510
[     6.581] (II) RADEON(0): EDID (in hex):
[     6.581] (II) RADEON(0): 	00ffffffffffff000472ca029f5b4022
[     6.581] (II) RADEON(0): 	18160103803c2278ca7b45a4554aa227
[     6.581] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     6.581] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     6.581] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     6.581] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     6.581] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     6.581] (II) RADEON(0): 	004c55573044303130383531300a00cf
[     6.581] (II) RADEON(0): Printing probed modes for output DisplayPort-1
[     6.581] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.581] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.581] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.581] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.581] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.581] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.581] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.581] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.581] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     6.581] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     6.581] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.581] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.581] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.581] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.581] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.581] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.581] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.581] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     6.581] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.581] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.581] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.581] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.583] (II) RADEON(0): EDID for output HDMI-0
[     6.615] (II) RADEON(0): EDID for output DVI-0
[     6.615] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 573634853
[     6.615] (II) RADEON(0): Year: 2012  Week: 23
[     6.615] (II) RADEON(0): EDID Version: 1.3
[     6.615] (II) RADEON(0): Digital Display Input
[     6.615] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     6.615] (II) RADEON(0): Gamma: 2.20
[     6.615] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     6.615] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.615] (II) RADEON(0): First detailed timing is preferred mode
[     6.615] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     6.615] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     6.615] (II) RADEON(0): Supported established timings:
[     6.615] (II) RADEON(0): 720x400@70Hz
[     6.615] (II) RADEON(0): 640x480@60Hz
[     6.615] (II) RADEON(0): 640x480@67Hz
[     6.615] (II) RADEON(0): 640x480@72Hz
[     6.615] (II) RADEON(0): 640x480@75Hz
[     6.615] (II) RADEON(0): 800x600@56Hz
[     6.615] (II) RADEON(0): 800x600@60Hz
[     6.615] (II) RADEON(0): 800x600@72Hz
[     6.615] (II) RADEON(0): 800x600@75Hz
[     6.615] (II) RADEON(0): 832x624@75Hz
[     6.615] (II) RADEON(0): 1024x768@60Hz
[     6.615] (II) RADEON(0): 1024x768@70Hz
[     6.615] (II) RADEON(0): 1024x768@75Hz
[     6.615] (II) RADEON(0): 1280x1024@75Hz
[     6.615] (II) RADEON(0): 1152x864@75Hz
[     6.615] (II) RADEON(0): Manufacturer's mask: 0
[     6.615] (II) RADEON(0): Supported standard timings:
[     6.615] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     6.615] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     6.615] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     6.615] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     6.615] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     6.615] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     6.615] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     6.615] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     6.616] (II) RADEON(0): Supported detailed timing:
[     6.616] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     6.616] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.616] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     6.616] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     6.616] (II) RADEON(0): Monitor name: S271HL
[     6.616] (II) RADEON(0): Serial No: LUW0D0108510
[     6.616] (II) RADEON(0): EDID (in hex):
[     6.616] (II) RADEON(0): 	00ffffffffffff000472ca0225f93022
[     6.616] (II) RADEON(0): 	17160103803c2278ca7b45a4554aa227
[     6.616] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     6.616] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     6.616] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     6.616] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     6.616] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     6.616] (II) RADEON(0): 	004c55573044303130383531300a00bc
[     6.616] (II) RADEON(0): Printing probed modes for output DVI-0
[     6.616] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.616] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.616] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.616] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.616] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.616] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.616] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.616] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.616] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     6.616] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     6.616] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.616] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.616] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.616] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.616] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.616] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.616] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.616] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     6.616] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.616] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.616] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.616] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.648] (II) RADEON(0): EDID for output DVI-1
[     6.648] (II) RADEON(0): Manufacturer: ACR  Model: 2ca  Serial#: 573634863
[     6.648] (II) RADEON(0): Year: 2012  Week: 23
[     6.648] (II) RADEON(0): EDID Version: 1.3
[     6.648] (II) RADEON(0): Digital Display Input
[     6.648] (II) RADEON(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     6.648] (II) RADEON(0): Gamma: 2.20
[     6.648] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[     6.648] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.648] (II) RADEON(0): First detailed timing is preferred mode
[     6.648] (II) RADEON(0): redX: 0.642 redY: 0.335   greenX: 0.291 greenY: 0.636
[     6.648] (II) RADEON(0): blueX: 0.153 blueY: 0.043   whiteX: 0.313 whiteY: 0.329
[     6.648] (II) RADEON(0): Supported established timings:
[     6.648] (II) RADEON(0): 720x400@70Hz
[     6.648] (II) RADEON(0): 640x480@60Hz
[     6.648] (II) RADEON(0): 640x480@67Hz
[     6.648] (II) RADEON(0): 640x480@72Hz
[     6.648] (II) RADEON(0): 640x480@75Hz
[     6.648] (II) RADEON(0): 800x600@56Hz
[     6.648] (II) RADEON(0): 800x600@60Hz
[     6.648] (II) RADEON(0): 800x600@72Hz
[     6.648] (II) RADEON(0): 800x600@75Hz
[     6.648] (II) RADEON(0): 832x624@75Hz
[     6.648] (II) RADEON(0): 1024x768@60Hz
[     6.648] (II) RADEON(0): 1024x768@70Hz
[     6.648] (II) RADEON(0): 1024x768@75Hz
[     6.648] (II) RADEON(0): 1280x1024@75Hz
[     6.648] (II) RADEON(0): 1152x864@75Hz
[     6.648] (II) RADEON(0): Manufacturer's mask: 0
[     6.648] (II) RADEON(0): Supported standard timings:
[     6.648] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     6.648] (II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     6.648] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     6.648] (II) RADEON(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     6.648] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 60  vid: 129
[     6.648] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     6.648] (II) RADEON(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     6.648] (II) RADEON(0): #7: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     6.648] (II) RADEON(0): Supported detailed timing:
[     6.648] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 336 mm
[     6.648] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.648] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     6.648] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[     6.648] (II) RADEON(0): Monitor name: S271HL
[     6.648] (II) RADEON(0): Serial No: LUW0D0108510
[     6.648] (II) RADEON(0): EDID (in hex):
[     6.648] (II) RADEON(0): 	00ffffffffffff000472ca022ff93022
[     6.648] (II) RADEON(0): 	17160103803c2278ca7b45a4554aa227
[     6.648] (II) RADEON(0): 	0b5054bfef80714f8140818081c08100
[     6.648] (II) RADEON(0): 	9500b300d1c0023a801871382d40582c
[     6.648] (II) RADEON(0): 	450056502100001e000000fd00384c1f
[     6.648] (II) RADEON(0): 	5311000a202020202020000000fc0053
[     6.648] (II) RADEON(0): 	323731484c0a202020202020000000ff
[     6.648] (II) RADEON(0): 	004c55573044303130383531300a00b2
[     6.648] (II) RADEON(0): Printing probed modes for output DVI-1
[     6.648] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.648] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.648] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.648] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.648] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.648] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.648] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.648] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.648] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[     6.648] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     6.648] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.648] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.649] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.649] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.649] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.649] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.649] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.649] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     6.649] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.649] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.649] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.649] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.649] (II) RADEON(0): Output DisplayPort-0 disconnected
[     6.649] (II) RADEON(0): Output DisplayPort-1 connected
[     6.649] (II) RADEON(0): Output HDMI-0 disconnected
[     6.649] (II) RADEON(0): Output DVI-0 connected
[     6.649] (II) RADEON(0): Output DVI-1 connected
[     6.649] (II) RADEON(0): Using exact sizes for initial modes
[     6.649] (II) RADEON(0): Output DisplayPort-1 using initial mode 1920x1080
[     6.649] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080
[     6.649] (II) RADEON(0): Output DVI-1 using initial mode 1920x1080
[     6.649] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     6.649] (II) RADEON(0): mem size init: gart size :1fbdf000 vram size: s:80000000 visible:7f7d7000
[     6.649] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[     6.649] (==) RADEON(0): DPI set to (96, 96)
[     6.649] (II) Loading sub module "fb"
[     6.649] (II) LoadModule: "fb"
[     6.649] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.649] (II) Module fb: vendor="X.Org Foundation"
[     6.649] 	compiled for 1.13.3, module version = 1.0.0
[     6.649] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.649] (II) Loading sub module "ramdac"
[     6.649] (II) LoadModule: "ramdac"
[     6.649] (II) Module "ramdac" already built-in
[     6.649] (II) UnloadModule: "vesa"
[     6.649] (II) Unloading vesa
[     6.649] (II) UnloadModule: "modesetting"
[     6.649] (II) Unloading modesetting
[     6.649] (II) UnloadModule: "fbdev"
[     6.649] (II) Unloading fbdev
[     6.649] (II) UnloadSubModule: "fbdevhw"
[     6.649] (II) Unloading fbdevhw
[     6.649] (--) Depth 24 pixmap format is 32 bpp
[     6.649] (II) RADEON(0): Front buffer size: 8100K
[     6.649] (II) RADEON(0): VRAM usage limit set to 1872540K
[     6.649] (==) RADEON(0): Backing store disabled
[     6.649] (WW) RADEON(0): Direct rendering disabled
[     6.649] (II) RADEON(0): Acceleration disabled
[     6.649] (==) RADEON(0): DPMS enabled
[     6.649] (==) RADEON(0): Silken mouse enabled
[     6.649] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     6.649] (--) RandR disabled
[     6.651] (II) SELinux: Disabled on system
[     6.652] (II) AIGLX: Screen 0 is not DRI2 capable
[     6.652] (II) AIGLX: Screen 0 is not DRI capable
[     6.697] (II) AIGLX: Loaded and initialized swrast
[     6.697] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     6.700] (II) RADEON(0): Setting screen physical size to 508 x 285
[     6.706] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.707] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.707] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.707] (II) LoadModule: "evdev"
[     6.707] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.707] (II) Module evdev: vendor="X.Org Foundation"
[     6.707] 	compiled for 1.13.3, module version = 2.7.3
[     6.707] 	Module class: X.Org XInput Driver
[     6.707] 	ABI class: X.Org XInput driver, version 18.0
[     6.707] (II) Using input driver 'evdev' for 'Power Button'
[     6.707] (**) Power Button: always reports core events
[     6.707] (**) evdev: Power Button: Device: "/dev/input/event1"
[     6.708] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.708] (--) evdev: Power Button: Found keys
[     6.708] (II) evdev: Power Button: Configuring as keyboard
[     6.708] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     6.708] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.708] (**) Option "xkb_rules" "evdev"
[     6.708] (**) Option "xkb_model" "pc105"
[     6.708] (**) Option "xkb_layout" "us"
[     6.708] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     6.708] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.708] (II) Using input driver 'evdev' for 'Power Button'
[     6.708] (**) Power Button: always reports core events
[     6.708] (**) evdev: Power Button: Device: "/dev/input/event0"
[     6.708] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.708] (--) evdev: Power Button: Found keys
[     6.708] (II) evdev: Power Button: Configuring as keyboard
[     6.708] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     6.708] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     6.708] (**) Option "xkb_rules" "evdev"
[     6.708] (**) Option "xkb_model" "pc105"
[     6.708] (**) Option "xkb_layout" "us"
[     6.708] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
[     6.708] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     6.708] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event13)
[     6.708] (II) No input driver specified, ignoring this device.
[     6.708] (II) This device may have been added with another device file.
[     6.708] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event14)
[     6.708] (II) No input driver specified, ignoring this device.
[     6.708] (II) This device may have been added with another device file.
[     6.708] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event15)
[     6.708] (II) No input driver specified, ignoring this device.
[     6.708] (II) This device may have been added with another device file.
[     6.708] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event16)
[     6.709] (II) No input driver specified, ignoring this device.
[     6.709] (II) This device may have been added with another device file.
[     6.709] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event17)
[     6.709] (II) No input driver specified, ignoring this device.
[     6.709] (II) This device may have been added with another device file.
[     6.709] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event18)
[     6.709] (II) No input driver specified, ignoring this device.
[     6.709] (II) This device may have been added with another device file.
[     6.709] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[     6.709] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     6.709] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     6.709] (**) HID 04f3:0103: always reports core events
[     6.709] (**) evdev: HID 04f3:0103: Device: "/dev/input/event2"
[     6.709] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[     6.709] (--) evdev: HID 04f3:0103: Found keys
[     6.709] (II) evdev: HID 04f3:0103: Configuring as keyboard
[     6.709] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input2/event2"
[     6.709] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 8)
[     6.709] (**) Option "xkb_rules" "evdev"
[     6.709] (**) Option "xkb_model" "pc105"
[     6.709] (**) Option "xkb_layout" "us"
[     6.709] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[     6.709] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[     6.709] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[     6.709] (**) HID 04f3:0103: always reports core events
[     6.709] (**) evdev: HID 04f3:0103: Device: "/dev/input/event3"
[     6.709] (--) evdev: HID 04f3:0103: Vendor 0x4f3 Product 0x103
[     6.709] (--) evdev: HID 04f3:0103: Found 1 mouse buttons
[     6.709] (--) evdev: HID 04f3:0103: Found scroll wheel(s)
[     6.709] (--) evdev: HID 04f3:0103: Found relative axes
[     6.709] (II) evdev: HID 04f3:0103: Forcing relative x/y axes to exist.
[     6.709] (--) evdev: HID 04f3:0103: Found absolute axes
[     6.709] (II) evdev: HID 04f3:0103: Forcing absolute x/y axes to exist.
[     6.709] (--) evdev: HID 04f3:0103: Found keys
[     6.709] (II) evdev: HID 04f3:0103: Configuring as mouse
[     6.709] (II) evdev: HID 04f3:0103: Configuring as keyboard
[     6.709] (II) evdev: HID 04f3:0103: Adding scrollwheel support
[     6.709] (**) evdev: HID 04f3:0103: YAxisMapping: buttons 4 and 5
[     6.709] (**) evdev: HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.709] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input3/event3"
[     6.709] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD, id 9)
[     6.709] (**) Option "xkb_rules" "evdev"
[     6.709] (**) Option "xkb_model" "pc105"
[     6.709] (**) Option "xkb_layout" "us"
[     6.709] (II) evdev: HID 04f3:0103: initialized for relative axes.
[     6.709] (WW) evdev: HID 04f3:0103: ignoring absolute axes.
[     6.709] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[     6.709] (**) HID 04f3:0103: (accel) acceleration profile 0
[     6.709] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[     6.709] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[     6.710] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event4)
[     6.710] (**) Cypress USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     6.710] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     6.710] (**) Cypress USB Keyboard: always reports core events
[     6.710] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event4"
[     6.710] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     6.710] (--) evdev: Cypress USB Keyboard: Found keys
[     6.710] (II) evdev: Cypress USB Keyboard: Configuring as keyboard
[     6.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/input/input4/event4"
[     6.710] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: KEYBOARD, id 10)
[     6.710] (**) Option "xkb_rules" "evdev"
[     6.710] (**) Option "xkb_model" "pc105"
[     6.710] (**) Option "xkb_layout" "us"
[     6.710] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event5)
[     6.710] (**) Cypress USB Keyboard: Applying InputClass "evdev keyboard catchall"
[     6.710] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     6.710] (**) Cypress USB Keyboard: always reports core events
[     6.710] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event5"
[     6.710] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     6.710] (--) evdev: Cypress USB Keyboard: Found 1 mouse buttons
[     6.710] (--) evdev: Cypress USB Keyboard: Found scroll wheel(s)
[     6.710] (--) evdev: Cypress USB Keyboard: Found relative axes
[     6.710] (II) evdev: Cypress USB Keyboard: Forcing relative x/y axes to exist.
[     6.710] (--) evdev: Cypress USB Keyboard: Found absolute axes
[     6.710] (II) evdev: Cypress USB Keyboard: Forcing absolute x/y axes to exist.
[     6.710] (--) evdev: Cypress USB Keyboard: Found keys
[     6.710] (II) evdev: Cypress USB Keyboard: Configuring as mouse
[     6.710] (II) evdev: Cypress USB Keyboard: Configuring as keyboard
[     6.710] (II) evdev: Cypress USB Keyboard: Adding scrollwheel support
[     6.710] (**) evdev: Cypress USB Keyboard: YAxisMapping: buttons 4 and 5
[     6.710] (**) evdev: Cypress USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.1/input/input5/event5"
[     6.710] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: KEYBOARD, id 11)
[     6.710] (**) Option "xkb_rules" "evdev"
[     6.710] (**) Option "xkb_model" "pc105"
[     6.710] (**) Option "xkb_layout" "us"
[     6.710] (II) evdev: Cypress USB Keyboard: initialized for relative axes.
[     6.710] (WW) evdev: Cypress USB Keyboard: ignoring absolute axes.
[     6.710] (**) Cypress USB Keyboard: (accel) keeping acceleration scheme 1
[     6.710] (**) Cypress USB Keyboard: (accel) acceleration profile 0
[     6.710] (**) Cypress USB Keyboard: (accel) acceleration factor: 2.000
[     6.710] (**) Cypress USB Keyboard: (accel) acceleration threshold: 4
[     6.710] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/event6)
[     6.710] (**) Cypress USB Keyboard: Applying InputClass "evdev pointer catchall"
[     6.710] (II) Using input driver 'evdev' for 'Cypress USB Keyboard'
[     6.710] (**) Cypress USB Keyboard: always reports core events
[     6.710] (**) evdev: Cypress USB Keyboard: Device: "/dev/input/event6"
[     6.710] (--) evdev: Cypress USB Keyboard: Vendor 0x4b4 Product 0x101
[     6.710] (--) evdev: Cypress USB Keyboard: Found 9 mouse buttons
[     6.710] (--) evdev: Cypress USB Keyboard: Found scroll wheel(s)
[     6.710] (--) evdev: Cypress USB Keyboard: Found relative axes
[     6.710] (--) evdev: Cypress USB Keyboard: Found x and y relative axes
[     6.710] (II) evdev: Cypress USB Keyboard: Configuring as mouse
[     6.710] (II) evdev: Cypress USB Keyboard: Adding scrollwheel support
[     6.710] (**) evdev: Cypress USB Keyboard: YAxisMapping: buttons 4 and 5
[     6.710] (**) evdev: Cypress USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.2/input/input6/event6"
[     6.710] (II) XINPUT: Adding extended input device "Cypress USB Keyboard" (type: MOUSE, id 12)
[     6.710] (II) evdev: Cypress USB Keyboard: initialized for relative axes.
[     6.711] (**) Cypress USB Keyboard: (accel) keeping acceleration scheme 1
[     6.711] (**) Cypress USB Keyboard: (accel) acceleration profile 0
[     6.711] (**) Cypress USB Keyboard: (accel) acceleration factor: 2.000
[     6.711] (**) Cypress USB Keyboard: (accel) acceleration threshold: 4
[     6.711] (II) config/udev: Adding input device Cypress USB Keyboard (/dev/input/mouse0)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.711] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.711] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.711] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event12)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.711] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event7)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.711] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event8)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.711] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)
[     6.711] (II) No input driver specified, ignoring this device.
[     6.711] (II) This device may have been added with another device file.
[     6.871] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     6.871] (II) RADEON(0): Using EDID range info for horizontal sync
[     6.871] (II) RADEON(0): Using EDID range info for vertical refresh
[     6.871] (II) RADEON(0): Printing DDC gathered Modelines:
[     6.871] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     6.871] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     6.871] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     6.871] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     6.871] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     6.871] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     6.871] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     6.871] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     6.871] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     6.871] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     6.872] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     6.872] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     6.872] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     6.872] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     6.872] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     6.872] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     6.872] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     6.872] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     6.872] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     6.872] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     6.872] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     6.872] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     6.872] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     6.873] (II) RADEON(0): Allocate new frame buffer 5760x1080 stride 5760
[     6.873] (II) RADEON(0): VRAM usage limit set to 1857960K
[     7.152] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     7.152] (II) RADEON(0): Using hsync ranges from config file
[     7.152] (II) RADEON(0): Using vrefresh ranges from config file
[     7.152] (II) RADEON(0): Printing DDC gathered Modelines:
[     7.152] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.152] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.152] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.152] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     7.152] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.152] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.152] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.152] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.152] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     7.152] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.152] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.152] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.152] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.152] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.152] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.152] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.152] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.152] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     7.152] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.152] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.152] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.152] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[     7.541] (II) RADEON(0): EDID vendor "ACR", prod id 714
[     7.541] (II) RADEON(0): Using hsync ranges from config file
[     7.541] (II) RADEON(0): Using vrefresh ranges from config file
[     7.541] (II) RADEON(0): Printing DDC gathered Modelines:
[     7.541] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     7.541] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.541] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     7.541] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     7.541] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     7.541] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     7.541] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.541] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     7.541] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     7.541] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     7.541] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     7.541] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.541] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     7.541] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     7.541] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     7.541] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     7.541] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     7.541] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.541] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[     7.541] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[     7.541] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[     7.541] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[     7.541] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    38.890] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/mouse1)
[    38.890] (II) No input driver specified, ignoring this device.
[    38.890] (II) This device may have been added with another device file.
[    38.890] (II) config/udev: Adding input device Logitech Gaming Mouse G400 (/dev/input/event19)
[    38.890] (**) Logitech Gaming Mouse G400: Applying InputClass "evdev pointer catchall"
[    38.890] (II) Using input driver 'evdev' for 'Logitech Gaming Mouse G400'
[    38.890] (**) Logitech Gaming Mouse G400: always reports core events
[    38.890] (**) evdev: Logitech Gaming Mouse G400: Device: "/dev/input/event19"
[    38.890] (--) evdev: Logitech Gaming Mouse G400: Vendor 0x46d Product 0xc245
[    38.890] (--) evdev: Logitech Gaming Mouse G400: Found 12 mouse buttons
[    38.890] (--) evdev: Logitech Gaming Mouse G400: Found scroll wheel(s)
[    38.890] (--) evdev: Logitech Gaming Mouse G400: Found relative axes
[    38.890] (--) evdev: Logitech Gaming Mouse G400: Found x and y relative axes
[    38.890] (II) evdev: Logitech Gaming Mouse G400: Configuring as mouse
[    38.890] (II) evdev: Logitech Gaming Mouse G400: Adding scrollwheel support
[    38.890] (**) evdev: Logitech Gaming Mouse G400: YAxisMapping: buttons 4 and 5
[    38.890] (**) evdev: Logitech Gaming Mouse G400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    38.890] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input19/event19"
[    38.890] (II) XINPUT: Adding extended input device "Logitech Gaming Mouse G400" (type: MOUSE, id 13)
[    38.890] (II) evdev: Logitech Gaming Mouse G400: initialized for relative axes.
[    38.890] (**) Logitech Gaming Mouse G400: (accel) keeping acceleration scheme 1
[    38.890] (**) Logitech Gaming Mouse G400: (accel) acceleration profile 0
[    38.890] (**) Logitech Gaming Mouse G400: (accel) acceleration factor: 2.000
[    38.890] (**) Logitech Gaming Mouse G400: (accel) acceleration threshold: 4
[    48.088] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    48.088] (II) RADEON(0): Using hsync ranges from config file
[    48.088] (II) RADEON(0): Using vrefresh ranges from config file
[    48.088] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.088] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    48.088] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.088] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    48.088] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.088] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    48.088] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    48.088] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.088] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.088] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    48.088] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.088] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    48.088] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.088] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.088] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.088] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    48.088] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    48.088] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    48.088] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    48.088] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    48.088] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    48.088] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    48.088] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    48.088] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    48.276] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    48.276] (II) RADEON(0): Using hsync ranges from config file
[    48.276] (II) RADEON(0): Using vrefresh ranges from config file
[    48.276] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.276] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    48.276] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.276] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    48.276] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.276] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    48.276] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    48.276] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.276] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.276] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    48.276] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.276] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    48.276] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.276] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.276] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.276] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    48.276] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    48.276] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    48.276] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    48.276] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    48.276] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    48.276] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    48.276] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    48.276] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    48.463] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    48.463] (II) RADEON(0): Using hsync ranges from config file
[    48.463] (II) RADEON(0): Using vrefresh ranges from config file
[    48.463] (II) RADEON(0): Printing DDC gathered Modelines:
[    48.463] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    48.463] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    48.463] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    48.463] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    48.463] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    48.463] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    48.463] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    48.463] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    48.463] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    48.463] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    48.463] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    48.463] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    48.463] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    48.463] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    48.463] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    48.463] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    48.463] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    48.463] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    48.463] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    48.463] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    48.463] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    48.463] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    48.463] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    48.551] (II) XKB: reuse xkmfile /var/lib/xkb/server-53A8C5DA194E264601CD74186096751A6970EE1E.xkm
[    49.336] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    49.336] (II) RADEON(0): Using hsync ranges from config file
[    49.336] (II) RADEON(0): Using vrefresh ranges from config file
[    49.336] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.336] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.336] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.336] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.336] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.336] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    49.336] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.336] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.336] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.336] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.336] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.336] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.336] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.336] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.336] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.336] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    49.336] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.336] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.336] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.336] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    49.336] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.336] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.336] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    49.336] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    49.480] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    49.480] (II) RADEON(0): Using hsync ranges from config file
[    49.480] (II) RADEON(0): Using vrefresh ranges from config file
[    49.480] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.480] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.480] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.480] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.480] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.480] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    49.480] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.480] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.480] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.480] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.480] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.480] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.480] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.480] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.480] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.480] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    49.480] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.480] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.480] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.480] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    49.480] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.480] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.480] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    49.480] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    49.480] [mi] Increasing EQ size to 512 to prevent dropped events.
[    49.624] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    49.624] (II) RADEON(0): Using hsync ranges from config file
[    49.624] (II) RADEON(0): Using vrefresh ranges from config file
[    49.624] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.624] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.624] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.624] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.625] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.625] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    49.625] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.625] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.625] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.625] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.625] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.625] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.625] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.625] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.625] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.625] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    49.625] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.625] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.625] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.625] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    49.625] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.625] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.625] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    49.625] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    49.756] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    49.756] (II) RADEON(0): Using hsync ranges from config file
[    49.756] (II) RADEON(0): Using vrefresh ranges from config file
[    49.756] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.756] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.756] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.756] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.756] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.756] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    49.756] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.756] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.756] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.756] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.756] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.756] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.756] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.756] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.756] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.756] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    49.756] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.756] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.756] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.756] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    49.756] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.756] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.756] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    49.756] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    49.888] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    49.888] (II) RADEON(0): Using hsync ranges from config file
[    49.888] (II) RADEON(0): Using vrefresh ranges from config file
[    49.888] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.888] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.888] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.888] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.888] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.888] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    49.888] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.888] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.888] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.888] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.888] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.888] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.888] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.888] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.888] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.888] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    49.888] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.888] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.888] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.888] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    49.888] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.888] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.888] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    49.888] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    50.032] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    50.033] (II) RADEON(0): Using hsync ranges from config file
[    50.033] (II) RADEON(0): Using vrefresh ranges from config file
[    50.033] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.033] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    50.033] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    50.033] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    50.033] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    50.033] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    50.033] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    50.033] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    50.033] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    50.033] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    50.033] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    50.033] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    50.033] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    50.033] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    50.033] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    50.033] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    50.033] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    50.033] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    50.033] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    50.033] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    50.033] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    50.033] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    50.033] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    50.033] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    50.167] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    50.167] (II) RADEON(0): Using hsync ranges from config file
[    50.167] (II) RADEON(0): Using vrefresh ranges from config file
[    50.167] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.167] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    50.167] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    50.167] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    50.167] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    50.167] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    50.167] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    50.167] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    50.167] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    50.167] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    50.167] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    50.167] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    50.167] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    50.167] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    50.167] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    50.168] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    50.168] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    50.168] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    50.168] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    50.168] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    50.168] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    50.168] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    50.168] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    50.168] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    50.308] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    50.308] (II) RADEON(0): Using hsync ranges from config file
[    50.308] (II) RADEON(0): Using vrefresh ranges from config file
[    50.308] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.308] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    50.308] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    50.308] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    50.308] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    50.308] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    50.308] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    50.308] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    50.308] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    50.308] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    50.308] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    50.308] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    50.308] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    50.308] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    50.308] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    50.308] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    50.308] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    50.308] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    50.308] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    50.308] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    50.308] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    50.308] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    50.308] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    50.308] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    50.440] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    50.440] (II) RADEON(0): Using hsync ranges from config file
[    50.440] (II) RADEON(0): Using vrefresh ranges from config file
[    50.440] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.440] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    50.440] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    50.440] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    50.440] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    50.440] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    50.440] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    50.440] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    50.440] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    50.440] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    50.440] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    50.440] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    50.440] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    50.440] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    50.440] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    50.440] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    50.440] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    50.440] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    50.440] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    50.440] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    50.440] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    50.440] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    50.440] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    50.440] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    50.580] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    50.580] (II) RADEON(0): Using hsync ranges from config file
[    50.580] (II) RADEON(0): Using vrefresh ranges from config file
[    50.580] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.580] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    50.580] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    50.580] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    50.580] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    50.580] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    50.580] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    50.580] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    50.580] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    50.580] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    50.580] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    50.580] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    50.580] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    50.580] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    50.580] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    50.580] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    50.580] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    50.580] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    50.580] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    50.580] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    50.580] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    50.580] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    50.580] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    50.580] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    68.921] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    68.921] (II) RADEON(0): Using hsync ranges from config file
[    68.921] (II) RADEON(0): Using vrefresh ranges from config file
[    68.921] (II) RADEON(0): Printing DDC gathered Modelines:
[    68.921] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    68.921] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    68.921] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    68.921] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    68.921] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    68.921] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    68.921] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    68.921] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    68.921] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    68.921] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    68.921] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    68.921] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    68.921] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    68.921] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    68.921] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    68.921] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    68.921] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    68.921] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    68.921] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    68.921] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    68.921] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    68.921] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    68.921] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    69.053] (II) RADEON(0): EDID vendor "ACR", prod id 714
[    69.053] (II) RADEON(0): Using hsync ranges from config file
[    69.053] (II) RADEON(0): Using vrefresh ranges from config file
[    69.053] (II) RADEON(0): Printing DDC gathered Modelines:
[    69.053] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    69.053] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    69.053] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    69.053] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    69.053] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    69.053] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    69.053] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    69.053] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    69.053] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    69.053] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    69.053] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    69.053] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    69.053] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    69.053] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    69.053] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    69.053] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    69.053] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    69.053] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    69.053] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    69.053] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    69.053] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    69.053] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    69.053] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)

```

---

### Post by Yellow Pasque on 2013-08-01
Hmm. I thought that would do it. The only other thing I can think of is using a 3.10.x kernel

---

### Post by *Legion* on 2013-08-01
Resolved!

Two posts from other forums got me the rest of the way there. First, [https://bbs.archlinux.org/viewtopic.php?id=160101]from the Arch forums]("https://bbs.archlinux.org/viewtopic.php?id=160101"):

> HD 7000 series and newer use glamor for 2D acceleration. Try removing the line containing "EXA" (and other lines beginning with the word "Option" as they might conflict with glamor, once you get everything working, then, if you really need those options, you can try adding them back, apart from "AccelMethod" "EXA" that is) from your 20-radeon.conf and adding those described in the wiki under the glamor section.

I snagged the xorg.conf snippet that followed in the next message. That got this message into my Xorg log: Failed to load module "glamoregl" (module does not exist, 0)

That led me to [this thread on Phoronix]("http://phoronix.com/forums/printthread.php?t=50038&pp=10&page=53"), which indicated that there was actually an additional driver package, xserver-xorg-video-glamor, that would need to be installed.

After installing that package and rebooting, DRI enabled.

Thanks Temüjin for the help that got me halfway there.

---

### Post by Yellow Pasque on 2013-08-01
You're welcome. I learned some good stuff and now I know to look for this line:
```
(WW) RADEON(0): glamor requires Load "glamoregl" in Section "Module", disabling.
```

---

