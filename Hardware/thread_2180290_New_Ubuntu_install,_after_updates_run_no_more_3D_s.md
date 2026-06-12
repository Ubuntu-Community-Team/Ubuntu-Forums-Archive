---
title: "New Ubuntu install, after updates run no more 3D support"
date: 2013-10-12
forum: Hardware
---

### Post by jogger2 on 2013-10-12
Hi guys,

First of all I hope this is the right sub-forum. So here it is:

I've just reinstalled Ubuntu on my machine after getting some wicked disk error. So OK, no problem. I get into 3D-Unity, run all the updates via ```
sudo apt-get upgrade
```. Then after reboot logging into 3D-Unity only gives a blank desktop, so I have to go for the 2D version. 
Now I wanna use Gnome 3, because it works for me on a small screen. Needless to say that won't run either so I'm using Gnome Classic No Effects right now. It get's the job done but I'd rather have the eye-candy. 
The weird thing to me is that under ```
 lshw -c video 
``` it lists my graphics card as run by the Open Source radeon driver. Which should provide sufficient 3D acceleration. So here's the terminal output:
```

sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: R580 [Radeon X1900 XT]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:41 memory:d0000000-dfffffff memory:febe0000-febeffff ioport:e000(size=256) memory:febc0000-febdffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: R580 [Radeon X1900 XT] (Secondary)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:04:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff

```

One more thing: Before the disk error on my old installation I had Gnome 3 running smoothly -- everything was perfect :**-(

Thank you very much for any additional tips you can come up with :-)

Cheers,
Robert

---

### Post by Yellow Pasque on 2013-10-12
Post the /var/log/Xorg.0.log file (use [ code ][ /code ] tags).

glxinfo might be helpful too
```
sudo apt-get install mesa-utils
export LIBGL_DEBUG=verbose; glxinfo
```

---

### Post by jogger2 on 2013-10-13
The Xorg.0.log file

```
 [    20.461] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    20.461] X Protocol Version 11, Revision 0
[    20.461] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    20.461] Current Operating System: Linux nadeleibe 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 17:01:55 UTC 2013 i686
[    20.461] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-41-generic root=UUID=b65caf53-81ac-4f66-9258-7c601da5a676 ro quiet splash vt.handoff=7
[    20.461] Build Date: 11 April 2013  11:50:36PM
[    20.461] xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see http://www.ubuntu.com/support) 
[    20.461] Current version of pixman: 0.24.4
[    20.461]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.461] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.461] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 13 15:28:42 2013
[    20.554] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.554] (==) No Layout section.  Using the first Screen section.
[    20.554] (==) No screen section available. Using defaults.
[    20.554] (**) |-->Screen "Default Screen Section" (0)
[    20.554] (**) |   |-->Monitor "<default monitor>"
[    20.554] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.554] (==) Automatically adding devices
[    20.554] (==) Automatically enabling devices
[    20.554] (==) Automatically adding GPU devices
[    20.554] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.554]     Entry deleted from font path.
[    20.554] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.554]     Entry deleted from font path.
[    20.555] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.555]     Entry deleted from font path.
[    20.555] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.555]     Entry deleted from font path.
[    20.555] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.555] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.555] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.555] (II) Loader magic: 0xb77f7620
[    20.555] (II) Module ABI versions:
[    20.555]     X.Org ANSI C Emulation: 0.4
[    20.555]     X.Org Video Driver: 13.0
[    20.555]     X.Org XInput driver : 18.0
[    20.555]     X.Org Server Extension : 7.0
[    20.555] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.557] (--) PCI:*(0:4:0:0) 1002:7249:1002:0b12 rev 0, Mem @ 0xd0000000/268435456, 0xfebe0000/65536, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    20.557] (--) PCI: (0:4:0:1) 1002:7269:1002:0b13 rev 0, Mem @ 0xfebf0000/65536
[    20.557] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.557] Initializing built-in extension Generic Event Extension
[    20.557] Initializing built-in extension SHAPE
[    20.557] Initializing built-in extension MIT-SHM
[    20.557] Initializing built-in extension XInputExtension
[    20.557] Initializing built-in extension XTEST
[    20.557] Initializing built-in extension BIG-REQUESTS
[    20.557] Initializing built-in extension SYNC
[    20.557] Initializing built-in extension XKEYBOARD
[    20.557] Initializing built-in extension XC-MISC
[    20.557] Initializing built-in extension SECURITY
[    20.557] Initializing built-in extension XINERAMA
[    20.557] Initializing built-in extension XFIXES
[    20.557] Initializing built-in extension RENDER
[    20.557] Initializing built-in extension RANDR
[    20.557] Initializing built-in extension COMPOSITE
[    20.557] Initializing built-in extension DAMAGE
[    20.557] Initializing built-in extension MIT-SCREEN-SAVER
[    20.557] Initializing built-in extension DOUBLE-BUFFER
[    20.557] Initializing built-in extension RECORD
[    20.557] Initializing built-in extension DPMS
[    20.557] Initializing built-in extension X-Resource
[    20.557] Initializing built-in extension XVideo
[    20.557] Initializing built-in extension XVideo-MotionCompensation
[    20.557] Initializing built-in extension XFree86-VidModeExtension
[    20.557] Initializing built-in extension XFree86-DGA
[    20.557] Initializing built-in extension XFree86-DRI
[    20.557] Initializing built-in extension DRI2
[    20.557] (II) LoadModule: "glx"
[    20.574] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    20.574] (II) Module glx: vendor="X.Org Foundation"
[    20.574]     compiled for 1.13.0, module version = 1.0.0
[    20.574]     ABI class: X.Org Server Extension, version 7.0
[    20.574] (==) AIGLX enabled
[    20.575] Loading extension GLX
[    20.575] (==) Matched fglrx as autoconfigured driver 0
[    20.575] (==) Matched ati as autoconfigured driver 1
[    20.575] (==) Matched fglrx as autoconfigured driver 2
[    20.575] (==) Matched ati as autoconfigured driver 3
[    20.575] (==) Matched vesa as autoconfigured driver 4
[    20.575] (==) Matched modesetting as autoconfigured driver 5
[    20.575] (==) Matched fbdev as autoconfigured driver 6
[    20.575] (==) Assigned the driver to the xf86ConfigLayout
[    20.575] (II) LoadModule: "fglrx"
[    20.583] (WW) Warning, couldn't open module fglrx
[    20.583] (II) UnloadModule: "fglrx"
[    20.583] (II) Unloading fglrx
[    20.583] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.583] (II) LoadModule: "ati"
[    20.583] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.583] (II) Module ati: vendor="X.Org Foundation"
[    20.583]     compiled for 1.13.0, module version = 6.99.99
[    20.583]     Module class: X.Org Video Driver
[    20.583]     ABI class: X.Org Video Driver, version 13.0
[    20.583] (II) LoadModule: "radeon"
[    20.584] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    20.584] (II) Module radeon: vendor="X.Org Foundation"
[    20.584]     compiled for 1.13.0, module version = 6.99.99
[    20.584]     Module class: X.Org Video Driver
[    20.584]     ABI class: X.Org Video Driver, version 13.0
[    20.584] (II) LoadModule: "vesa"
[    20.584] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.584] (II) Module vesa: vendor="X.Org Foundation"
[    20.584]     compiled for 1.13.0, module version = 2.3.2
[    20.584]     Module class: X.Org Video Driver
[    20.584]     ABI class: X.Org Video Driver, version 13.0
[    20.584] (II) LoadModule: "modesetting"
[    20.584] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.584] (II) Module modesetting: vendor="X.Org Foundation"
[    20.584]     compiled for 1.13.0, module version = 0.5.0
[    20.584]     Module class: X.Org Video Driver
[    20.584]     ABI class: X.Org Video Driver, version 13.0
[    20.584] (II) LoadModule: "fbdev"
[    20.585] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.585] (II) Module fbdev: vendor="X.Org Foundation"
[    20.585]     compiled for 1.13.0, module version = 0.4.3
[    20.585]     Module class: X.Org Video Driver
[    20.585]     ABI class: X.Org Video Driver, version 13.0
[    20.585] (==) Matched fglrx as autoconfigured driver 0
[    20.585] (==) Matched ati as autoconfigured driver 1
[    20.585] (==) Matched fglrx as autoconfigured driver 2
[    20.585] (==) Matched ati as autoconfigured driver 3
[    20.585] (==) Matched vesa as autoconfigured driver 4
[    20.585] (==) Matched modesetting as autoconfigured driver 5
[    20.585] (==) Matched fbdev as autoconfigured driver 6
[    20.585] (==) Assigned the driver to the xf86ConfigLayout
[    20.585] (II) LoadModule: "fglrx"
[    20.585] (WW) Warning, couldn't open module fglrx
[    20.585] (II) UnloadModule: "fglrx"
[    20.585] (II) Unloading fglrx
[    20.585] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.585] (II) LoadModule: "ati"
[    20.586] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.586] (II) Module ati: vendor="X.Org Foundation"
[    20.586]     compiled for 1.13.0, module version = 6.99.99
[    20.586]     Module class: X.Org Video Driver
[    20.586]     ABI class: X.Org Video Driver, version 13.0
[    20.586] (II) LoadModule: "vesa"
[    20.586] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.586] (II) Module vesa: vendor="X.Org Foundation"
[    20.586]     compiled for 1.13.0, module version = 2.3.2
[    20.586]     Module class: X.Org Video Driver
[    20.586]     ABI class: X.Org Video Driver, version 13.0
[    20.586] (II) UnloadModule: "vesa"
[    20.586] (II) Unloading vesa
[    20.586] (II) Failed to load module "vesa" (already loaded, 0)
[    20.586] (II) LoadModule: "modesetting"
[    20.586] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    20.586] (II) Module modesetting: vendor="X.Org Foundation"
[    20.586]     compiled for 1.13.0, module version = 0.5.0
[    20.586]     Module class: X.Org Video Driver
[    20.586]     ABI class: X.Org Video Driver, version 13.0
[    20.586] (II) UnloadModule: "modesetting"
[    20.586] (II) Unloading modesetting
[    20.586] (II) Failed to load module "modesetting" (already loaded, 0)
[    20.586] (II) LoadModule: "fbdev"
[    20.587] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.587] (II) Module fbdev: vendor="X.Org Foundation"
[    20.587]     compiled for 1.13.0, module version = 0.4.3
[    20.587]     Module class: X.Org Video Driver
[    20.587]     ABI class: X.Org Video Driver, version 13.0
[    20.587] (II) UnloadModule: "fbdev"
[    20.587] (II) Unloading fbdev
[    20.587] (II) Failed to load module "fbdev" (already loaded, 0)
[    20.587] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE
[    20.592] (II) VESA: driver for VESA chipsets: vesa
[    20.592] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    20.592] (II) FBDEV: driver for framebuffer: fbdev
[    20.592] (++) using VT number 7

[    20.592] (II) [KMS] Kernel modesetting enabled.
[    20.592] (WW) Falling back to old probe method for vesa
[    20.592] (WW) Falling back to old probe method for modesetting
[    20.592] (WW) Falling back to old probe method for fbdev
[    20.592] (II) Loading sub module "fbdevhw"
[    20.592] (II) LoadModule: "fbdevhw"
[    20.592] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.592] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.592]     compiled for 1.13.0, module version = 0.0.2
[    20.592]     ABI class: X.Org Video Driver, version 13.0
[    20.592] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    20.592] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    20.592] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    20.592] (==) RADEON(0): Default visual is TrueColor
[    20.592] (==) RADEON(0): RGB weight 888
[    20.592] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    20.592] (--) RADEON(0): Chipset: "ATI Radeon X1900" (ChipID = 0x7249)
[    20.593] (II) Loading sub module "dri2"
[    20.593] (II) LoadModule: "dri2"
[    20.593] (II) Module "dri2" already built-in
[    20.593] (II) Loading sub module "exa"
[    20.593] (II) LoadModule: "exa"
[    20.593] (II) Loading /usr/lib/xorg/modules/libexa.so
[    20.593] (II) Module exa: vendor="X.Org Foundation"
[    20.593]     compiled for 1.13.0, module version = 2.6.0
[    20.593]     ABI class: X.Org Video Driver, version 13.0
[    20.593] (II) RADEON(0): KMS Color Tiling: enabled
[    20.593] (II) RADEON(0): KMS Pageflipping: enabled
[    20.593] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    20.626] (II) RADEON(0): Output DVI-0 has no monitor section
[    20.664] (II) RADEON(0): Output S-video has no monitor section
[    20.697] (II) RADEON(0): Output DVI-1 has no monitor section
[    20.730] (II) RADEON(0): EDID for output DVI-0
[    20.730] (II) RADEON(0): Manufacturer: NEC  Model: 65d4  Serial#: 16843009
[    20.730] (II) RADEON(0): Year: 2002  Week: 8
[    20.730] (II) RADEON(0): EDID Version: 1.3
[    20.730] (II) RADEON(0): Digital Display Input
[    20.730] (II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 29
[    20.730] (II) RADEON(0): Gamma: 2.20
[    20.730] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    20.731] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    20.731] (II) RADEON(0): First detailed timing is preferred mode
[    20.731] (II) RADEON(0): redX: 0.610 redY: 0.350   greenX: 0.300 greenY: 0.600
[    20.731] (II) RADEON(0): blueX: 0.150 blueY: 0.100   whiteX: 0.300 whiteY: 0.315
[    20.731] (II) RADEON(0): Supported established timings:
[    20.731] (II) RADEON(0): 720x400@70Hz
[    20.731] (II) RADEON(0): 640x480@60Hz
[    20.731] (II) RADEON(0): 640x480@67Hz
[    20.731] (II) RADEON(0): 640x480@72Hz
[    20.731] (II) RADEON(0): 640x480@75Hz
[    20.731] (II) RADEON(0): 800x600@56Hz
[    20.731] (II) RADEON(0): 800x600@60Hz
[    20.731] (II) RADEON(0): 800x600@72Hz
[    20.731] (II) RADEON(0): 800x600@75Hz
[    20.731] (II) RADEON(0): 832x624@75Hz
[    20.731] (II) RADEON(0): 1024x768@60Hz
[    20.731] (II) RADEON(0): 1024x768@70Hz
[    20.731] (II) RADEON(0): 1024x768@75Hz
[    20.731] (II) RADEON(0): 1280x1024@75Hz
[    20.731] (II) RADEON(0): 1152x864@75Hz
[    20.731] (II) RADEON(0): Manufacturer's mask: 0
[    20.731] (II) RADEON(0): Supported standard timings:
[    20.731] (II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[    20.731] (II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[    20.731] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[    20.731] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    20.731] (II) RADEON(0): #4: hsize: 1280  vsize 960  refresh: 75  vid: 20353
[    20.731] (II) RADEON(0): Supported detailed timing:
[    20.731] (II) RADEON(0): clock: 108.0 MHz   Image Size:  359 x 287 mm
[    20.731] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    20.731] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    20.731] (II) RADEON(0): Ranges: V min: 50 V max: 85 Hz, H min: 31 H max: 82 kHz, PixClock max 145 MHz
[    20.731] (II) RADEON(0): Monitor name: LCD1880SX
[    20.731] (II) RADEON(0): Serial No: 2200244CB
[    20.731] (II) RADEON(0): EDID (in hex):
[    20.731] (II) RADEON(0):     00ffffffffffff0038a3d46501010101
[    20.731] (II) RADEON(0):     080c010380241d78ea6eaf9c594c9926
[    20.731] (II) RADEON(0):     194c50bfef80315945596159714f814f
[    20.731] (II) RADEON(0):     010101010101302a009851002a403070
[    20.731] (II) RADEON(0):     1300671f1100001e000000fd0032551f
[    20.731] (II) RADEON(0):     520e000a202020202020000000fc004c
[    20.731] (II) RADEON(0):     43443138383053580a202020000000ff
[    20.731] (II) RADEON(0):     003232303032343443420a2020200058
[    20.731] (II) RADEON(0): Printing probed modes for output DVI-0
[    20.731] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    20.731] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    20.731] (II) RADEON(0): Modeline "1280x960"x75.0  129.94  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    20.731] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    20.731] (II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    20.731] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    20.731] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    20.731] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    20.731] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    20.731] (II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    20.731] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    20.731] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    20.731] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    20.731] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    20.731] (II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    20.731] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    20.731] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    20.731] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    20.731] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    20.731] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    20.768] (II) RADEON(0): EDID for output S-video
[    20.801] (II) RADEON(0): EDID for output DVI-1
[    20.801] (II) RADEON(0): Manufacturer: NEC  Model: 65d4  Serial#: 16843009
[    20.801] (II) RADEON(0): Year: 2002  Week: 8
[    20.801] (II) RADEON(0): EDID Version: 1.3
[    20.801] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    20.801] (II) RADEON(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
[    20.801] (II) RADEON(0): Max Image Size [cm]: horiz.: 36  vert.: 29
[    20.801] (II) RADEON(0): Gamma: 2.20
[    20.801] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    20.801] (II) RADEON(0): First detailed timing is preferred mode
[    20.801] (II) RADEON(0): redX: 0.610 redY: 0.350   greenX: 0.300 greenY: 0.600
[    20.801] (II) RADEON(0): blueX: 0.150 blueY: 0.100   whiteX: 0.300 whiteY: 0.315
[    20.801] (II) RADEON(0): Supported established timings:
[    20.801] (II) RADEON(0): 720x400@70Hz
[    20.801] (II) RADEON(0): 640x480@60Hz
[    20.801] (II) RADEON(0): 640x480@67Hz
[    20.801] (II) RADEON(0): 640x480@72Hz
[    20.801] (II) RADEON(0): 640x480@75Hz
[    20.801] (II) RADEON(0): 800x600@56Hz
[    20.802] (II) RADEON(0): 800x600@60Hz
[    20.802] (II) RADEON(0): 800x600@72Hz
[    20.802] (II) RADEON(0): 800x600@75Hz
[    20.802] (II) RADEON(0): 832x624@75Hz
[    20.802] (II) RADEON(0): 1024x768@60Hz
[    20.802] (II) RADEON(0): 1024x768@70Hz
[    20.802] (II) RADEON(0): 1024x768@75Hz
[    20.802] (II) RADEON(0): 1280x1024@75Hz
[    20.802] (II) RADEON(0): 1152x864@75Hz
[    20.802] (II) RADEON(0): Manufacturer's mask: 0
[    20.802] (II) RADEON(0): Supported standard timings:
[    20.802] (II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[    20.802] (II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[    20.802] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[    20.802] (II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    20.802] (II) RADEON(0): #4: hsize: 1280  vsize 960  refresh: 75  vid: 20353
[    20.802] (II) RADEON(0): Supported detailed timing:
[    20.802] (II) RADEON(0): clock: 108.0 MHz   Image Size:  359 x 287 mm
[    20.802] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    20.802] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    20.802] (II) RADEON(0): Ranges: V min: 50 V max: 85 Hz, H min: 31 H max: 82 kHz, PixClock max 145 MHz
[    20.802] (II) RADEON(0): Monitor name: LCD1880SX
[    20.802] (II) RADEON(0): Serial No: 2200244CB
[    20.802] (II) RADEON(0): EDID (in hex):
[    20.802] (II) RADEON(0):     00ffffffffffff0038a3d46501010101
[    20.802] (II) RADEON(0):     080c01030f241d78ea6eaf9c594c9926
[    20.802] (II) RADEON(0):     194c50bfef80315945596159714f814f
[    20.802] (II) RADEON(0):     010101010101302a009851002a403070
[    20.802] (II) RADEON(0):     1300671f1100001e000000fd0032551f
[    20.802] (II) RADEON(0):     520e000a202020202020000000fc004c
[    20.802] (II) RADEON(0):     43443138383053580a202020000000ff
[    20.802] (II) RADEON(0):     003232303032343443420a20202000c9
[    20.802] (II) RADEON(0): Printing probed modes for output DVI-1
[    20.802] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    20.802] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    20.802] (II) RADEON(0): Modeline "1280x960"x75.0  129.94  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    20.802] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    20.802] (II) RADEON(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    20.802] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    20.802] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    20.802] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    20.802] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    20.802] (II) RADEON(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    20.802] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    20.802] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    20.802] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    20.802] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    20.802] (II) RADEON(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    20.802] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    20.802] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    20.802] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    20.802] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    20.802] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    20.802] (II) RADEON(0): Output DVI-0 connected
[    20.802] (II) RADEON(0): Output S-video disconnected
[    20.802] (II) RADEON(0): Output DVI-1 connected
[    20.802] (II) RADEON(0): Using exact sizes for initial modes
[    20.802] (II) RADEON(0): Output DVI-0 using initial mode 1280x1024
[    20.802] (II) RADEON(0): Output DVI-1 using initial mode 1280x1024
[    20.802] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.802] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:1fac0000
[    20.802] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    20.802] (==) RADEON(0): DPI set to (96, 96)
[    20.802] (II) Loading sub module "fb"
[    20.802] (II) LoadModule: "fb"
[    20.803] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.803] (II) Module fb: vendor="X.Org Foundation"
[    20.803]     compiled for 1.13.0, module version = 1.0.0
[    20.803]     ABI class: X.Org ANSI C Emulation, version 0.4
[    20.803] (II) Loading sub module "ramdac"
[    20.803] (II) LoadModule: "ramdac"
[    20.803] (II) Module "ramdac" already built-in
[    20.803] (II) UnloadModule: "vesa"
[    20.803] (II) Unloading vesa
[    20.803] (II) UnloadModule: "modesetting"
[    20.803] (II) Unloading modesetting
[    20.803] (II) UnloadModule: "fbdev"
[    20.803] (II) Unloading fbdev
[    20.803] (II) UnloadSubModule: "fbdevhw"
[    20.803] (II) Unloading fbdevhw
[    20.803] (--) Depth 24 pixmap format is 32 bpp
[    20.803] (II) RADEON(0): [DRI2] Setup complete
[    20.803] (II) RADEON(0): [DRI2]   DRI driver: r300
[    20.803] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    20.803] (II) RADEON(0): Front buffer size: 5120K
[    20.803] (II) RADEON(0): VRAM usage limit set to 462412K
[    20.803] (==) RADEON(0): Backing store disabled
[    20.803] (II) RADEON(0): Direct rendering enabled
[    20.803] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    20.803] (II) RADEON(0): Setting EXA maxPitchBytes
[    20.803] (II) EXA(0): Driver allocated offscreen pixmaps
[    20.803] (II) EXA(0): Driver registered support for the following operations:
[    20.803] (II)         Solid
[    20.803] (II)         Copy
[    20.803] (II)         Composite (RENDER acceleration)
[    20.803] (II)         UploadToScreen
[    20.803] (II)         DownloadFromScreen
[    20.803] (II) RADEON(0): Acceleration enabled
[    20.803] (==) RADEON(0): DPMS enabled
[    20.803] (==) RADEON(0): Silken mouse enabled
[    20.804] (II) RADEON(0): Set up textured video
[    20.804] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    20.804] (II) RADEON(0): [XvMC] Extension initialized.
[    20.804] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.810] (--) RandR disabled
[    20.829] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.829] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.829] (II) AIGLX: enabled GLX_ARB_create_context
[    20.829] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    20.829] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    20.829] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.829] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.829] (II) AIGLX: Loaded and initialized r300
[    20.829] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.844] (II) RADEON(0): Setting screen physical size to 338 x 270
[    20.867] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.871] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.871] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.871] (II) LoadModule: "evdev"
[    20.871] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.871] (II) Module evdev: vendor="X.Org Foundation"
[    20.871]     compiled for 1.13.0, module version = 2.7.3
[    20.871]     Module class: X.Org XInput Driver
[    20.871]     ABI class: X.Org XInput driver, version 18.0
[    20.871] (II) Using input driver 'evdev' for 'Power Button'
[    20.871] (**) Power Button: always reports core events
[    20.871] (**) evdev: Power Button: Device: "/dev/input/event1"
[    20.871] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.871] (--) evdev: Power Button: Found keys
[    20.871] (II) evdev: Power Button: Configuring as keyboard
[    20.871] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    20.871] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    20.871] (**) Option "xkb_rules" "evdev"
[    20.872] (**) Option "xkb_model" "pc105"
[    20.872] (**) Option "xkb_layout" "de"
[    20.874] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    20.875] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.875] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.875] (II) Using input driver 'evdev' for 'Power Button'
[    20.875] (**) Power Button: always reports core events
[    20.875] (**) evdev: Power Button: Device: "/dev/input/event0"
[    20.875] (--) evdev: Power Button: Vendor 0 Product 0x1
[    20.875] (--) evdev: Power Button: Found keys
[    20.875] (II) evdev: Power Button: Configuring as keyboard
[    20.875] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    20.875] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    20.875] (**) Option "xkb_rules" "evdev"
[    20.875] (**) Option "xkb_model" "pc105"
[    20.875] (**) Option "xkb_layout" "de"
[    20.876] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event10)
[    20.876] (II) No input driver specified, ignoring this device.
[    20.876] (II) This device may have been added with another device file.
[    20.876] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event5)
[    20.876] (II) No input driver specified, ignoring this device.
[    20.876] (II) This device may have been added with another device file.
[    20.876] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    20.876] (II) No input driver specified, ignoring this device.
[    20.876] (II) This device may have been added with another device file.
[    20.877] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event7)
[    20.877] (II) No input driver specified, ignoring this device.
[    20.877] (II) This device may have been added with another device file.
[    20.877] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event8)
[    20.877] (II) No input driver specified, ignoring this device.
[    20.877] (II) This device may have been added with another device file.
[    20.877] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event9)
[    20.877] (II) No input driver specified, ignoring this device.
[    20.877] (II) This device may have been added with another device file.
[    20.877] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.878] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event2)
[    20.878] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[    20.878] (II) Using input driver 'evdev' for 'HID 046a:0023'
[    20.878] (**) HID 046a:0023: always reports core events
[    20.878] (**) evdev: HID 046a:0023: Device: "/dev/input/event2"
[    20.878] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[    20.878] (--) evdev: HID 046a:0023: Found keys
[    20.878] (II) evdev: HID 046a:0023: Configuring as keyboard
[    20.878] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input2/event2"
[    20.878] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 8)
[    20.878] (**) Option "xkb_rules" "evdev"
[    20.878] (**) Option "xkb_model" "pc105"
[    20.878] (**) Option "xkb_layout" "de"
[    20.879] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event3)
[    20.879] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[    20.879] (II) Using input driver 'evdev' for 'HID 046a:0023'
[    20.879] (**) HID 046a:0023: always reports core events
[    20.879] (**) evdev: HID 046a:0023: Device: "/dev/input/event3"
[    20.879] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[    20.879] (--) evdev: HID 046a:0023: Found 1 mouse buttons
[    20.879] (--) evdev: HID 046a:0023: Found scroll wheel(s)
[    20.879] (--) evdev: HID 046a:0023: Found relative axes
[    20.879] (II) evdev: HID 046a:0023: Forcing relative x/y axes to exist.
[    20.879] (--) evdev: HID 046a:0023: Found absolute axes
[    20.879] (II) evdev: HID 046a:0023: Forcing absolute x/y axes to exist.
[    20.879] (--) evdev: HID 046a:0023: Found keys
[    20.879] (II) evdev: HID 046a:0023: Configuring as mouse
[    20.879] (II) evdev: HID 046a:0023: Configuring as keyboard
[    20.879] (II) evdev: HID 046a:0023: Adding scrollwheel support
[    20.879] (**) evdev: HID 046a:0023: YAxisMapping: buttons 4 and 5
[    20.879] (**) evdev: HID 046a:0023: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.879] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.1/input/input3/event3"
[    20.879] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 9)
[    20.879] (**) Option "xkb_rules" "evdev"
[    20.879] (**) Option "xkb_model" "pc105"
[    20.879] (**) Option "xkb_layout" "de"
[    20.879] (II) evdev: HID 046a:0023: initialized for relative axes.
[    20.879] (WW) evdev: HID 046a:0023: ignoring absolute axes.
[    20.880] (**) HID 046a:0023: (accel) keeping acceleration scheme 1
[    20.880] (**) HID 046a:0023: (accel) acceleration profile 0
[    20.880] (**) HID 046a:0023: (accel) acceleration factor: 2.000
[    20.880] (**) HID 046a:0023: (accel) acceleration threshold: 4
[    20.880] (II) config/udev: Adding input device Microsoft SideWinder™ Mouse (/dev/input/event4)
[    20.880] (**) Microsoft SideWinder™ Mouse: Applying InputClass "evdev pointer catchall"
[    20.880] (**) Microsoft SideWinder™ Mouse: Applying InputClass "evdev keyboard catchall"
[    20.880] (II) Using input driver 'evdev' for 'Microsoft SideWinder™ Mouse'
[    20.880] (**) Microsoft SideWinder™ Mouse: always reports core events
[    20.880] (**) evdev: Microsoft SideWinder™ Mouse: Device: "/dev/input/event4"
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Vendor 0x45e Product 0x724
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found 9 mouse buttons
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found scroll wheel(s)
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found relative axes
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found x and y relative axes
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found absolute axes
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found absolute multitouch axes
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found x and y absolute axes
[    20.880] (--) evdev: Microsoft SideWinder™ Mouse: Found keys
[    20.880] (II) evdev: Microsoft SideWinder™ Mouse: Configuring as mouse
[    20.880] (II) evdev: Microsoft SideWinder™ Mouse: Configuring as keyboard
[    20.880] (II) evdev: Microsoft SideWinder™ Mouse: Adding scrollwheel support
[    20.880] (**) evdev: Microsoft SideWinder™ Mouse: YAxisMapping: buttons 4 and 5
[    20.880] (**) evdev: Microsoft SideWinder™ Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.880] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:01:00.0/usb7/7-2/7-2:1.0/input/input4/event4"
[    20.880] (II) XINPUT: Adding extended input device "Microsoft SideWinder™ Mouse" (type: KEYBOARD, id 10)
[    20.880] (**) Option "xkb_rules" "evdev"
[    20.880] (**) Option "xkb_model" "pc105"
[    20.880] (**) Option "xkb_layout" "de"
[    20.881] (II) evdev: Microsoft SideWinder™ Mouse: initialized for relative axes.
[    20.881] (WW) evdev: Microsoft SideWinder™ Mouse: ignoring absolute axes.
[    20.881] (**) Microsoft SideWinder™ Mouse: (accel) keeping acceleration scheme 1
[    20.881] (**) Microsoft SideWinder™ Mouse: (accel) acceleration profile 0
[    20.881] (**) Microsoft SideWinder™ Mouse: (accel) acceleration factor: 2.000
[    20.881] (**) Microsoft SideWinder™ Mouse: (accel) acceleration threshold: 4
[    20.881] (II) config/udev: Adding input device Microsoft SideWinder™ Mouse (/dev/input/js0)
[    20.881] (II) No input driver specified, ignoring this device.
[    20.881] (II) This device may have been added with another device file.
[    20.882] (II) config/udev: Adding input device Microsoft SideWinder™ Mouse (/dev/input/mouse0)
[    20.882] (II) No input driver specified, ignoring this device.
[    20.882] (II) This device may have been added with another device file.
[    21.525] (II) RADEON(0): EDID vendor "NEC", prod id 26068
[    21.525] (II) RADEON(0): Using EDID range info for horizontal sync
[    21.525] (II) RADEON(0): Using EDID range info for vertical refresh
[    21.525] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.525] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    21.525] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.525] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    21.525] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    21.525] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    21.525] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    21.525] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    21.525] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    21.525] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    21.525] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    21.525] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    21.525] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.525] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    21.525] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    21.525] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    21.526] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    21.526] (II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    21.526] (II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    21.526] (II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    21.526] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz e)
[    22.042] (II) RADEON(0): Allocate new frame buffer 2560x1024 stride 2560
[    22.042] (II) RADEON(0): VRAM usage limit set to 457804K
[    22.186] (II) RADEON(0): EDID vendor "NEC", prod id 26068
[    22.186] (II) RADEON(0): Using hsync ranges from config file
[    22.186] (II) RADEON(0): Using vrefresh ranges from config file
[    22.186] (II) RADEON(0): Printing DDC gathered Modelines:
[    22.186] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    22.186] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.186] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    22.186] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    22.186] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    22.186] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    22.186] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.186] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    22.186] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    22.186] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    22.186] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    22.186] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.186] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    22.186] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    22.186] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    22.186] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    22.186] (II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    22.186] (II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    22.186] (II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    22.186] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz e)
[    27.301] (II) RADEON(0): EDID vendor "NEC", prod id 26068
[    27.301] (II) RADEON(0): Using hsync ranges from config file
[    27.301] (II) RADEON(0): Using vrefresh ranges from config file
[    27.301] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.301] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    27.301] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    27.301] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    27.301] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    27.301] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    27.301] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    27.301] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    27.301] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    27.301] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    27.301] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    27.301] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    27.301] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    27.301] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    27.301] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    27.301] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    27.301] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    27.301] (II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    27.301] (II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    27.301] (II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    27.301] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz e)
[    27.928] (II) XKB: reuse xkmfile /var/lib/xkb/server-F4E9C56B40BF1F2D0070F07A7EA268420DB29EEE.xkm
[    28.053] (II) RADEON(0): EDID vendor "NEC", prod id 26068
[    28.053] (II) RADEON(0): Using hsync ranges from config file
[    28.053] (II) RADEON(0): Using vrefresh ranges from config file
[    28.053] (II) RADEON(0): Printing DDC gathered Modelines:
[    28.053] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    28.053] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    28.053] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    28.053] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    28.053] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    28.053] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    28.053] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    28.053] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    28.053] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    28.053] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    28.053] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    28.053] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    28.053] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    28.053] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    28.053] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    28.053] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    28.053] (II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    28.053] (II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    28.053] (II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    28.053] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz e)
[    50.186] (II) RADEON(0): EDID vendor "NEC", prod id 26068
[    50.186] (II) RADEON(0): Using hsync ranges from config file
[    50.186] (II) RADEON(0): Using vrefresh ranges from config file
[    50.186] (II) RADEON(0): Printing DDC gathered Modelines:
[    50.186] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz eP)
[    50.186] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    50.186] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    50.186] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    50.186] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    50.186] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    50.186] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    50.186] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    50.186] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    50.186] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    50.186] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    50.186] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    50.186] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    50.186] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    50.186] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    50.186] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    50.186] (II) RADEON(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz e)
[    50.186] (II) RADEON(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz e)
[    50.186] (II) RADEON(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz e)
[    50.186] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz e)

```

And glxinfo:
```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_get_proc_address, 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R580
OpenGL version string: 2.1 Mesa 9.0.3
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_MESA_window_pos, 
    GL_NV_packed_depth_stencil, GL_NV_texture_rectangle, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_fog_distance, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_primitive_restart, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_packed_depth_stencil, GL_ARB_vertex_array_object, 
    GL_ATI_separate_stencil, GL_ATI_texture_mirror_once, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_compression_latc, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_ARB_ES2_compatibility, GL_ARB_debug_output, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_shader_texture_lod, 
    GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_NV_texture_barrier, GL_ARB_robustness, 
    GL_ARB_texture_storage, GL_ARB_invalidate_subdata

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0fd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0fe 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ff 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x100 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x101 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x102 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x103 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x104 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x105 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x106 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x107 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x108 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x109 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x110 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x111 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x112 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x113 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x114 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x115 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x116 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x117 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x118 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x119 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x11a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x11b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x11c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x11d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x11e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x11f 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x120 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x121 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x122 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x123 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x124 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x125 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x126 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x127 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x128 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x129 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x12a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x12b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x12c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x12d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x12e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x12f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x130 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x131 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x132 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x133 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x134 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x135 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x136 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x137 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x138 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x139 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x13c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x13d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x13e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x13f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x140 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x141 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x142 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x143 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x144 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x145 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x146 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x147 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x148 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x149 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x14a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x14b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x14c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x14d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x14e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x14f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x150 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x151 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x152 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x153 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x154 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x155 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x156 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x157 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x158 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x159 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x06f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x070 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x071 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x072 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x073 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x074 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x078 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x079 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x081 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x083 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x085 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x086 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x087 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x088 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x089 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x08b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x094 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x095 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x096 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x097 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x09c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x09f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a1  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a3  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a4  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a5  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a6  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a7  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a9  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0aa  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ab  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ac  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ad  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ae  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0af  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b0  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b1  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b3  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b4  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0bb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0bc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0bd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0be 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0bf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0c1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ca 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0cb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0cc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0cd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ce 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0cf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0d8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0d9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0da 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0db 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0dc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0dd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0de 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0df 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ea  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0eb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0ec  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ed  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0ee  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0ef  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0f1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f6  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f8  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fa  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0fc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow

```

---

### Post by Yellow Pasque on 2013-10-13
The logs look fine. :\
The only thing I could think of is installing linux-lts-raring (or something like that) to move to the Ubuntu 12.04.3 kernel and X server.

---

### Post by jogger2 on 2013-10-14
Alright,

So you mean I install Ubuntu 13.04 and then downgrade the kernel to 12.04.3? I'll try that when I've got a little more time. So expect an answer in a month or so ;-)
Thank you very much for the support!

---

### Post by Yellow Pasque on 2013-10-14
> So you mean I install Ubuntu 13.04 and then downgrade the kernel to 12.04.3?
No. I mean you run this in your current install:
```
sudo apt-get install linux-lts-raring xserver-xorg-lts-raring
```

---

### Post by jogger2 on 2013-10-16
hi,

nah, sadly this doesn't seem to have changed anything. But my hardware is like 8yrs old, some parts even older, so I don't know.

---

