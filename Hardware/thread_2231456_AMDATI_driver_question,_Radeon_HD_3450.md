---
title: "AMD/ATI driver question, Radeon HD 3450"
date: 2014-06-25
forum: Hardware
---

### Post by sparky741pa on 2014-06-25
Hello!

I am in the process of weening everyone off of Windows xp and moving over to Linux.  I have used it at work and like it a lot.  I have installed Ubuntu 14.04 and it loaded with relatively little trouble. I do, however, seem to be having some trouble with the video driver.  My video card is a Radeon HD 3450.  After the install, the driver that was shown in the About this Computer window was VESA:RV620, which I am not sure is the open source driver or just a generic driver. So, I went to AMD's website, and after some reading, downloaded Catalyst 13.1(the last version that supported my card) and proceeded to install. Bad idea. Afterwards, I could only get the login screen, and after putting in my password, would briefly get a black screen and would kick me back to the login screen.  Did a reboot, and a ctrl-alt-F1 and was able to purge the fglrx drivers.  Now, when i login, the driver that is listed is a Gallium 0.4 on llvmpipe(LLVM 3.4 128 bits).  According to what I have read, this is software rendering driver.  What can I do to get the appropriate open source driver installed? I can tell it is taxing my system somewhat as windows open slowly and scrolling in a browser window can be slow sometimes as well.

---

### Post by vmweenie on 2014-06-25
In [http://askubuntu.com/questions/209876/upgraded-ubuntu-from-12-04-to-12-10-ati-radeon-hd-3450-catastrophe](http://askubuntu.com/questions/209876/upgraded-ubuntu-from-12-04-to-12-10-ati-radeon-hd-3450-catastrophe) nit says *Ati has removed support for Radeon 2xxx, 3xxx and 4xxx series of graphic cards for their newest drivers, which Ubuntu 12.10 now uses. *  There's a blog post linked there [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/) that might be useful to you.

---

### Post by Yellow Pasque on 2014-06-25
Yes, llvmpipe is software rendering. First, make sure fglrx is completely purged (these commands may fail, but just keep going):
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo rm -rf /etc/ati
```

Next, fix files that fglrx may have overwritten:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

Log out (or reboot) to restart X. If it's still not working, post the /var/log/Xorg.0.log (and use code tags).

---

### Post by mörgæs on 2014-06-25
Correct, AMD support their cards for only a few years. Nvidia does a better job. 

If you are struggling with low performance using Ubuntu you could try X/Lubuntu regardless of drivers.

---

### Post by sparky741pa on 2014-06-26
Temujin, no change, here is my log file

```
[    21.089] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    21.089] X Protocol Version 11, Revision 0
[    21.089] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    21.089] Current Operating System: Linux MyComputer 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64
[    21.089] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=e927788d-5d85-4d99-be6b-bfd9d3d4fdb5 ro nomodeset quiet splash radeon.dpm=1 vt.handoff=7
[    21.090] Build Date: 16 April 2014  01:36:29PM
[    21.090] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    21.090] Current version of pixman: 0.30.2
[    21.090]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.090] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.090] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 26 02:47:29 2014
[    21.139] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.257] (==) No Layout section.  Using the first Screen section.
[    21.257] (==) No screen section available. Using defaults.
[    21.257] (**) |-->Screen "Default Screen Section" (0)
[    21.257] (**) |   |-->Monitor "<default monitor>"
[    21.257] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.257] (==) Automatically adding devices
[    21.257] (==) Automatically enabling devices
[    21.257] (==) Automatically adding GPU devices
[    21.281] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.281]     Entry deleted from font path.
[    21.281] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.281]     Entry deleted from font path.
[    21.281] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.281]     Entry deleted from font path.
[    21.296] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.296]     Entry deleted from font path.
[    21.296] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.296]     Entry deleted from font path.
[    21.296] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    21.296] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.296] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.296] (II) Loader magic: 0x7fc53050ad60
[    21.296] (II) Module ABI versions:
[    21.296]     X.Org ANSI C Emulation: 0.4
[    21.296]     X.Org Video Driver: 15.0
[    21.296]     X.Org XInput driver : 20.0
[    21.296]     X.Org Server Extension : 8.0
[    21.296] (II) xfree86: Adding drm device (/dev/dri/card0)
[    21.298] (--) PCI:*(0:1:0:0) 1002:95c5:1787:2252 rev 0, Mem @ 0xe0000000/268435456, 0xfdfe0000/65536, I/O @ 0x0000bc00/256, BIOS @ 0x????????/131072
[    21.319] Initializing built-in extension Generic Event Extension
[    21.319] Initializing built-in extension SHAPE
[    21.319] Initializing built-in extension MIT-SHM
[    21.319] Initializing built-in extension XInputExtension
[    21.319] Initializing built-in extension XTEST
[    21.319] Initializing built-in extension BIG-REQUESTS
[    21.319] Initializing built-in extension SYNC
[    21.319] Initializing built-in extension XKEYBOARD
[    21.319] Initializing built-in extension XC-MISC
[    21.319] Initializing built-in extension SECURITY
[    21.319] Initializing built-in extension XINERAMA
[    21.319] Initializing built-in extension XFIXES
[    21.319] Initializing built-in extension RENDER
[    21.319] Initializing built-in extension RANDR
[    21.319] Initializing built-in extension COMPOSITE
[    21.319] Initializing built-in extension DAMAGE
[    21.319] Initializing built-in extension MIT-SCREEN-SAVER
[    21.319] Initializing built-in extension DOUBLE-BUFFER
[    21.319] Initializing built-in extension RECORD
[    21.319] Initializing built-in extension DPMS
[    21.319] Initializing built-in extension Present
[    21.319] Initializing built-in extension DRI3
[    21.319] Initializing built-in extension X-Resource
[    21.319] Initializing built-in extension XVideo
[    21.319] Initializing built-in extension XVideo-MotionCompensation
[    21.319] Initializing built-in extension SELinux
[    21.319] Initializing built-in extension XFree86-VidModeExtension
[    21.319] Initializing built-in extension XFree86-DGA
[    21.319] Initializing built-in extension XFree86-DRI
[    21.319] Initializing built-in extension DRI2
[    21.319] (II) LoadModule: "glx"
[    21.403] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.567] (II) Module glx: vendor="X.Org Foundation"
[    21.567]     compiled for 1.15.1, module version = 1.0.0
[    21.567]     ABI class: X.Org Server Extension, version 8.0
[    21.567] (==) AIGLX enabled
[    21.567] Loading extension GLX
[    21.567] (==) Matched fglrx as autoconfigured driver 0
[    21.567] (==) Matched ati as autoconfigured driver 1
[    21.567] (==) Matched fglrx as autoconfigured driver 2
[    21.567] (==) Matched ati as autoconfigured driver 3
[    21.567] (==) Matched modesetting as autoconfigured driver 4
[    21.567] (==) Matched fbdev as autoconfigured driver 5
[    21.567] (==) Matched vesa as autoconfigured driver 6
[    21.567] (==) Assigned the driver to the xf86ConfigLayout
[    21.567] (II) LoadModule: "fglrx"
[    21.568] (WW) Warning, couldn't open module fglrx
[    21.568] (II) UnloadModule: "fglrx"
[    21.568] (II) Unloading fglrx
[    21.568] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.568] (II) LoadModule: "ati"
[    21.568] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.591] (II) Module ati: vendor="X.Org Foundation"
[    21.591]     compiled for 1.15.1, module version = 7.3.0
[    21.591]     Module class: X.Org Video Driver
[    21.591]     ABI class: X.Org Video Driver, version 15.0
[    21.591] (II) LoadModule: "radeon"
[    21.591] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    21.711] (II) Module radeon: vendor="X.Org Foundation"
[    21.711]     compiled for 1.15.1, module version = 7.3.0
[    21.711]     Module class: X.Org Video Driver
[    21.711]     ABI class: X.Org Video Driver, version 15.0
[    21.711] (II) LoadModule: "modesetting"
[    21.711] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.731] (II) Module modesetting: vendor="X.Org Foundation"
[    21.731]     compiled for 1.15.0, module version = 0.8.1
[    21.731]     Module class: X.Org Video Driver
[    21.731]     ABI class: X.Org Video Driver, version 15.0
[    21.731] (II) LoadModule: "fbdev"
[    21.731] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.737] (II) Module fbdev: vendor="X.Org Foundation"
[    21.737]     compiled for 1.15.0, module version = 0.4.4
[    21.737]     Module class: X.Org Video Driver
[    21.737]     ABI class: X.Org Video Driver, version 15.0
[    21.737] (II) LoadModule: "vesa"
[    21.738] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.745] (II) Module vesa: vendor="X.Org Foundation"
[    21.745]     compiled for 1.15.0, module version = 2.3.3
[    21.745]     Module class: X.Org Video Driver
[    21.745]     ABI class: X.Org Video Driver, version 15.0
[    21.745] (==) Matched fglrx as autoconfigured driver 0
[    21.745] (==) Matched ati as autoconfigured driver 1
[    21.745] (==) Matched fglrx as autoconfigured driver 2
[    21.745] (==) Matched ati as autoconfigured driver 3
[    21.745] (==) Matched modesetting as autoconfigured driver 4
[    21.745] (==) Matched fbdev as autoconfigured driver 5
[    21.745] (==) Matched vesa as autoconfigured driver 6
[    21.745] (==) Assigned the driver to the xf86ConfigLayout
[    21.745] (II) LoadModule: "fglrx"
[    21.746] (WW) Warning, couldn't open module fglrx
[    21.746] (II) UnloadModule: "fglrx"
[    21.746] (II) Unloading fglrx
[    21.746] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    21.746] (II) LoadModule: "ati"
[    21.746] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    21.746] (II) Module ati: vendor="X.Org Foundation"
[    21.746]     compiled for 1.15.1, module version = 7.3.0
[    21.746]     Module class: X.Org Video Driver
[    21.746]     ABI class: X.Org Video Driver, version 15.0
[    21.746] (II) LoadModule: "modesetting"
[    21.746] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.746] (II) Module modesetting: vendor="X.Org Foundation"
[    21.746]     compiled for 1.15.0, module version = 0.8.1
[    21.746]     Module class: X.Org Video Driver
[    21.746]     ABI class: X.Org Video Driver, version 15.0
[    21.746] (II) UnloadModule: "modesetting"
[    21.746] (II) Unloading modesetting
[    21.746] (II) Failed to load module "modesetting" (already loaded, 0)
[    21.746] (II) LoadModule: "fbdev"
[    21.747] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.747] (II) Module fbdev: vendor="X.Org Foundation"
[    21.747]     compiled for 1.15.0, module version = 0.4.4
[    21.747]     Module class: X.Org Video Driver
[    21.747]     ABI class: X.Org Video Driver, version 15.0
[    21.747] (II) UnloadModule: "fbdev"
[    21.747] (II) Unloading fbdev
[    21.747] (II) Failed to load module "fbdev" (already loaded, 0)
[    21.747] (II) LoadModule: "vesa"
[    21.747] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.747] (II) Module vesa: vendor="X.Org Foundation"
[    21.747]     compiled for 1.15.0, module version = 2.3.3
[    21.747]     Module class: X.Org Video Driver
[    21.747]     ABI class: X.Org Video Driver, version 15.0
[    21.747] (II) UnloadModule: "vesa"
[    21.747] (II) Unloading vesa
[    21.747] (II) Failed to load module "vesa" (already loaded, 0)
[    21.747] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    21.755] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    21.755] (II) FBDEV: driver for framebuffer: fbdev
[    21.755] (II) VESA: driver for VESA chipsets: vesa
[    21.755] (++) using VT number 7

[    21.773] (II) [KMS] drm report modesetting isn't supported.
[    21.773] (II) [KMS] drm report modesetting isn't supported.
[    21.773] (II) [KMS] drm report modesetting isn't supported.
[    21.773] (II) [KMS] drm report modesetting isn't supported.
[    21.773] (II) [KMS] drm report modesetting isn't supported.
[    21.774] (WW) Falling back to old probe method for modesetting
[    21.774] (II) Loading sub module "fbdevhw"
[    21.774] (II) LoadModule: "fbdevhw"
[    21.774] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.795] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.795]     compiled for 1.15.1, module version = 0.0.2
[    21.795]     ABI class: X.Org Video Driver, version 15.0
[    21.795] (**) FBDEV(6): claimed PCI slot 1@0:0:0
[    21.795] (II) FBDEV(6): using default device
[    21.795] (WW) Falling back to old probe method for vesa
[    21.795] (EE) Screen 0 deleted because of no matching config section.
[    21.796] (II) UnloadModule: "radeon"
[    21.796] (EE) Screen 0 deleted because of no matching config section.
[    21.796] (II) UnloadModule: "radeon"
[    21.796] (EE) Screen 0 deleted because of no matching config section.
[    21.796] (II) UnloadModule: "radeon"
[    21.796] (EE) Screen 0 deleted because of no matching config section.
[    21.796] (II) UnloadModule: "radeon"
[    21.796] (EE) Screen 0 deleted because of no matching config section.
[    21.796] (II) UnloadModule: "modesetting"
[    21.796] (EE) Screen 0 deleted because of no matching config section.
[    21.796] (II) UnloadModule: "modesetting"
[    21.796] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.796] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    21.796] (==) FBDEV(0): RGB weight 888
[    21.796] (==) FBDEV(0): Default visual is TrueColor
[    21.796] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.796] (II) FBDEV(0): hardware: VESA VGA (video memory: 5120kB)
[    21.796] (II) FBDEV(0): checking modes against framebuffer device...
[    21.796] (II) FBDEV(0): checking modes against monitor...
[    21.796] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    21.796] (**) FBDEV(0):  Built-in mode "current": 131.1 MHz, 80.3 kHz, 76.6 Hz
[    21.796] (II) FBDEV(0): Modeline "current"x0.0  131.09  1280 1312 1472 1632  1024 1028 1032 1048 -hsync -vsync -csync (80.3 kHz b)
[    21.796] (==) FBDEV(0): DPI set to (96, 96)
[    21.796] (II) Loading sub module "fb"
[    21.796] (II) LoadModule: "fb"
[    21.796] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.815] (II) Module fb: vendor="X.Org Foundation"
[    21.815]     compiled for 1.15.1, module version = 1.0.0
[    21.815]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.815] (**) FBDEV(0): using shadow framebuffer
[    21.815] (II) Loading sub module "shadow"
[    21.815] (II) LoadModule: "shadow"
[    21.815] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.816] (II) Module shadow: vendor="X.Org Foundation"
[    21.816]     compiled for 1.15.1, module version = 1.1.0
[    21.816]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.816] (II) UnloadModule: "radeon"
[    21.816] (II) UnloadModule: "vesa"
[    21.816] (II) Unloading vesa
[    21.816] (==) Depth 24 pixmap format is 32 bpp
[    21.816] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    21.822] (==) FBDEV(0): Backing store enabled
[    21.822] (==) FBDEV(0): DPMS enabled
[    21.822] (==) RandR enabled
[    21.828] (II) SELinux: Disabled on system
[    21.829] (II) AIGLX: Screen 0 is not DRI2 capable
[    21.829] (EE) AIGLX: reverting to software rendering
[    22.231] (II) AIGLX: Loaded and initialized swrast
[    22.231] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    22.310] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.323] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.323] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.323] (II) LoadModule: "evdev"
[    22.323] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.355] (II) Module evdev: vendor="X.Org Foundation"
[    22.355]     compiled for 1.15.0, module version = 2.8.2
[    22.355]     Module class: X.Org XInput Driver
[    22.355]     ABI class: X.Org XInput driver, version 20.0
[    22.355] (II) Using input driver 'evdev' for 'Power Button'
[    22.355] (**) Power Button: always reports core events
[    22.355] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.355] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.355] (--) evdev: Power Button: Found keys
[    22.355] (II) evdev: Power Button: Configuring as keyboard
[    22.355] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.355] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.355] (**) Option "xkb_rules" "evdev"
[    22.355] (**) Option "xkb_model" "pc105"
[    22.355] (**) Option "xkb_layout" "us"
[    22.356] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.356] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.356] (II) Using input driver 'evdev' for 'Power Button'
[    22.356] (**) Power Button: always reports core events
[    22.356] (**) evdev: Power Button: Device: "/dev/input/event0"
[    22.356] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.356] (--) evdev: Power Button: Found keys
[    22.356] (II) evdev: Power Button: Configuring as keyboard
[    22.356] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.356] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    22.356] (**) Option "xkb_rules" "evdev"
[    22.356] (**) Option "xkb_model" "pc105"
[    22.356] (**) Option "xkb_layout" "us"
[    22.356] (II) config/udev: Adding drm device (/dev/dri/card0)
[    22.356] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    22.357] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[    22.357] (II) No input driver specified, ignoring this device.
[    22.357] (II) This device may have been added with another device file.
[    22.357] (II) config/udev: Adding input device HID 0b38:0010 (/dev/input/event3)
[    22.357] (**) HID 0b38:0010: Applying InputClass "evdev keyboard catchall"
[    22.357] (II) Using input driver 'evdev' for 'HID 0b38:0010'
[    22.357] (**) HID 0b38:0010: always reports core events
[    22.357] (**) evdev: HID 0b38:0010: Device: "/dev/input/event3"
[    22.357] (--) evdev: HID 0b38:0010: Vendor 0xb38 Product 0x10
[    22.357] (--) evdev: HID 0b38:0010: Found keys
[    22.357] (II) evdev: HID 0b38:0010: Configuring as keyboard
[    22.357] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input6/event3"
[    22.357] (II) XINPUT: Adding extended input device "HID 0b38:0010" (type: KEYBOARD, id 8)
[    22.357] (**) Option "xkb_rules" "evdev"
[    22.357] (**) Option "xkb_model" "pc105"
[    22.357] (**) Option "xkb_layout" "us"
[    22.358] (II) config/udev: Adding input device HID 0b38:0010 (/dev/input/event4)
[    22.358] (**) HID 0b38:0010: Applying InputClass "evdev keyboard catchall"
[    22.358] (II) Using input driver 'evdev' for 'HID 0b38:0010'
[    22.358] (**) HID 0b38:0010: always reports core events
[    22.358] (**) evdev: HID 0b38:0010: Device: "/dev/input/event4"
[    22.358] (--) evdev: HID 0b38:0010: Vendor 0xb38 Product 0x10
[    22.358] (--) evdev: HID 0b38:0010: Found 1 mouse buttons
[    22.358] (--) evdev: HID 0b38:0010: Found scroll wheel(s)
[    22.358] (--) evdev: HID 0b38:0010: Found relative axes
[    22.358] (II) evdev: HID 0b38:0010: Forcing relative x/y axes to exist.
[    22.358] (--) evdev: HID 0b38:0010: Found absolute axes
[    22.358] (II) evdev: HID 0b38:0010: Forcing absolute x/y axes to exist.
[    22.358] (--) evdev: HID 0b38:0010: Found keys
[    22.358] (II) evdev: HID 0b38:0010: Configuring as mouse
[    22.358] (II) evdev: HID 0b38:0010: Configuring as keyboard
[    22.358] (II) evdev: HID 0b38:0010: Adding scrollwheel support
[    22.358] (**) evdev: HID 0b38:0010: YAxisMapping: buttons 4 and 5
[    22.358] (**) evdev: HID 0b38:0010: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.358] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.1/input/input7/event4"
[    22.358] (II) XINPUT: Adding extended input device "HID 0b38:0010" (type: KEYBOARD, id 9)
[    22.358] (**) Option "xkb_rules" "evdev"
[    22.358] (**) Option "xkb_model" "pc105"
[    22.358] (**) Option "xkb_layout" "us"
[    22.358] (II) evdev: HID 0b38:0010: initialized for relative axes.
[    22.358] (WW) evdev: HID 0b38:0010: ignoring absolute axes.
[    22.359] (**) HID 0b38:0010: (accel) keeping acceleration scheme 1
[    22.359] (**) HID 0b38:0010: (accel) acceleration profile 0
[    22.359] (**) HID 0b38:0010: (accel) acceleration factor: 2.000
[    22.359] (**) HID 0b38:0010: (accel) acceleration threshold: 4
[    22.359] (II) config/udev: Adding input device Microsoft Microsoft® Comfort Mouse 4500 (/dev/input/event2)
[    22.359] (**) Microsoft Microsoft® Comfort Mouse 4500: Applying InputClass "evdev pointer catchall"
[    22.359] (**) Microsoft Microsoft® Comfort Mouse 4500: Applying InputClass "evdev keyboard catchall"
[    22.359] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Comfort Mouse 4500'
[    22.359] (**) Microsoft Microsoft® Comfort Mouse 4500: always reports core events
[    22.359] (**) evdev: Microsoft Microsoft® Comfort Mouse 4500: Device: "/dev/input/event2"
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Vendor 0x45e Product 0x76c
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found 9 mouse buttons
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found scroll wheel(s)
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found relative axes
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found x and y relative axes
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found absolute axes
[    22.359] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Forcing absolute x/y axes to exist.
[    22.359] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found keys
[    22.359] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Configuring as mouse
[    22.359] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Configuring as keyboard
[    22.359] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Adding scrollwheel support
[    22.359] (**) evdev: Microsoft Microsoft® Comfort Mouse 4500: YAxisMapping: buttons 4 and 5
[    22.359] (**) evdev: Microsoft Microsoft® Comfort Mouse 4500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.359] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input5/event2"
[    22.359] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Comfort Mouse 4500" (type: KEYBOARD, id 10)
[    22.359] (**) Option "xkb_rules" "evdev"
[    22.359] (**) Option "xkb_model" "pc105"
[    22.359] (**) Option "xkb_layout" "us"
[    22.360] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: initialized for relative axes.
[    22.360] (WW) evdev: Microsoft Microsoft® Comfort Mouse 4500: ignoring absolute axes.
[    22.360] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) keeping acceleration scheme 1
[    22.360] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) acceleration profile 0
[    22.360] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) acceleration factor: 2.000
[    22.360] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) acceleration threshold: 4
[    22.360] (II) config/udev: Adding input device Microsoft Microsoft® Comfort Mouse 4500 (/dev/input/mouse0)
[    22.360] (II) No input driver specified, ignoring this device.
[    22.360] (II) This device may have been added with another device file.
[    22.360] (II) config/udev: Adding input device HDA NVidia Line Out (/dev/input/event5)
[    22.361] (II) No input driver specified, ignoring this device.
[    22.361] (II) This device may have been added with another device file.
[    22.361] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event7)
[    22.361] (II) No input driver specified, ignoring this device.
[    22.361] (II) This device may have been added with another device file.
[    22.361] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event6)
[    22.361] (II) No input driver specified, ignoring this device.
[    22.361] (II) This device may have been added with another device file.
[    22.368] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    52.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    52.133] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    52.276] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    53.164] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
```

---

### Post by Yellow Pasque on 2014-06-28
```
[KMS] drm report modesetting isn't supported.
```
That's not good. How did you install the fglrx driver? Did you build a package or did you just run the installer (aka "Yes, please overwrite my important files and clobber my system" mode)?

---

### Post by sparky741pa on 2014-06-28
Temujin

Since I had to use a legacy version of Catalyst, I downloaded the .run file and had to do some commands to make a bunch of .deb files which I then installed.  It did not work, so I then purged all the fglrx stuff.  Any way to fix it?

---

### Post by Yellow Pasque on 2014-06-28
Okay, so you built a package. I can't see how it would still be interfering after purging the package. Are you sure the open-source radeon driver actually worked correctly before installing Catalyst?

Try to reinstall the kernel:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```

---

### Post by sparky741pa on 2014-06-29
Temujin,
 
Reinstalled the kernel per your instructions, but still no change.  I recall when I first installed 14.04, I was getting the black screen after startup, so I put the "nomodeset xforcevesa" in the grub config to be able to get to the login screen.  I think I removed the xforcevesa part later, but would still get the VESA:RV620 shown as the driver when I would check it.  That's when i tried putting the Catalyst driver on and then it didn't let me login at all. So no I don't know for sure if I was ever using the open source driver.

Here's a fresh log file since re-installing the kernel if it helps you at all.  Thank you for your help so far.

```
[    13.448] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    13.448] X Protocol Version 11, Revision 0
[    13.448] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    13.448] Current Operating System: Linux MyComputer 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64
[    13.448] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=e927788d-5d85-4d99-be6b-bfd9d3d4fdb5 ro nomodeset quiet splash radeon.dpm=1 vt.handoff=7
[    13.448] Build Date: 16 April 2014  01:36:29PM
[    13.448] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    13.448] Current version of pixman: 0.30.2
[    13.448] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    13.448] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.448] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 29 01:34:52 2014
[    13.535] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.535] (==) No Layout section.  Using the first Screen section.
[    13.535] (==) No screen section available. Using defaults.
[    13.535] (**) |-->Screen "Default Screen Section" (0)
[    13.535] (**) |   |-->Monitor "<default monitor>"
[    13.535] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    13.535] (==) Automatically adding devices
[    13.535] (==) Automatically enabling devices
[    13.535] (==) Automatically adding GPU devices
[    13.536] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.536] 	Entry deleted from font path.
[    13.536] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.536] 	Entry deleted from font path.
[    13.536] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.536] 	Entry deleted from font path.
[    13.536] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.536] 	Entry deleted from font path.
[    13.536] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.536] 	Entry deleted from font path.
[    13.536] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    13.536] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.536] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.536] (II) Loader magic: 0x7fc3a1872d60
[    13.536] (II) Module ABI versions:
[    13.536] 	X.Org ANSI C Emulation: 0.4
[    13.536] 	X.Org Video Driver: 15.0
[    13.536] 	X.Org XInput driver : 20.0
[    13.536] 	X.Org Server Extension : 8.0
[    13.536] (II) xfree86: Adding drm device (/dev/dri/card0)
[    13.538] (--) PCI:*(0:1:0:0) 1002:95c5:1787:2252 rev 0, Mem @ 0xe0000000/268435456, 0xfdfe0000/65536, I/O @ 0x0000bc00/256, BIOS @ 0x????????/131072
[    13.538] Initializing built-in extension Generic Event Extension
[    13.538] Initializing built-in extension SHAPE
[    13.538] Initializing built-in extension MIT-SHM
[    13.538] Initializing built-in extension XInputExtension
[    13.538] Initializing built-in extension XTEST
[    13.538] Initializing built-in extension BIG-REQUESTS
[    13.538] Initializing built-in extension SYNC
[    13.538] Initializing built-in extension XKEYBOARD
[    13.538] Initializing built-in extension XC-MISC
[    13.538] Initializing built-in extension SECURITY
[    13.538] Initializing built-in extension XINERAMA
[    13.538] Initializing built-in extension XFIXES
[    13.538] Initializing built-in extension RENDER
[    13.538] Initializing built-in extension RANDR
[    13.538] Initializing built-in extension COMPOSITE
[    13.538] Initializing built-in extension DAMAGE
[    13.538] Initializing built-in extension MIT-SCREEN-SAVER
[    13.538] Initializing built-in extension DOUBLE-BUFFER
[    13.538] Initializing built-in extension RECORD
[    13.538] Initializing built-in extension DPMS
[    13.538] Initializing built-in extension Present
[    13.538] Initializing built-in extension DRI3
[    13.538] Initializing built-in extension X-Resource
[    13.538] Initializing built-in extension XVideo
[    13.538] Initializing built-in extension XVideo-MotionCompensation
[    13.539] Initializing built-in extension SELinux
[    13.539] Initializing built-in extension XFree86-VidModeExtension
[    13.539] Initializing built-in extension XFree86-DGA
[    13.539] Initializing built-in extension XFree86-DRI
[    13.539] Initializing built-in extension DRI2
[    13.539] (II) LoadModule: "glx"
[    13.649] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.862] (II) Module glx: vendor="X.Org Foundation"
[    13.862] 	compiled for 1.15.1, module version = 1.0.0
[    13.862] 	ABI class: X.Org Server Extension, version 8.0
[    13.862] (==) AIGLX enabled
[    13.862] Loading extension GLX
[    13.862] (==) Matched fglrx as autoconfigured driver 0
[    13.862] (==) Matched ati as autoconfigured driver 1
[    13.862] (==) Matched fglrx as autoconfigured driver 2
[    13.862] (==) Matched ati as autoconfigured driver 3
[    13.862] (==) Matched modesetting as autoconfigured driver 4
[    13.862] (==) Matched fbdev as autoconfigured driver 5
[    13.862] (==) Matched vesa as autoconfigured driver 6
[    13.862] (==) Assigned the driver to the xf86ConfigLayout
[    13.862] (II) LoadModule: "fglrx"
[    13.863] (WW) Warning, couldn't open module fglrx
[    13.863] (II) UnloadModule: "fglrx"
[    13.863] (II) Unloading fglrx
[    13.863] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    13.863] (II) LoadModule: "ati"
[    13.863] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    13.863] (II) Module ati: vendor="X.Org Foundation"
[    13.863] 	compiled for 1.15.1, module version = 7.3.0
[    13.863] 	Module class: X.Org Video Driver
[    13.863] 	ABI class: X.Org Video Driver, version 15.0
[    13.863] (II) LoadModule: "radeon"
[    13.863] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    13.910] (II) Module radeon: vendor="X.Org Foundation"
[    13.910] 	compiled for 1.15.1, module version = 7.3.0
[    13.910] 	Module class: X.Org Video Driver
[    13.910] 	ABI class: X.Org Video Driver, version 15.0
[    13.910] (II) LoadModule: "modesetting"
[    13.910] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    13.910] (II) Module modesetting: vendor="X.Org Foundation"
[    13.910] 	compiled for 1.15.0, module version = 0.8.1
[    13.910] 	Module class: X.Org Video Driver
[    13.911] 	ABI class: X.Org Video Driver, version 15.0
[    13.911] (II) LoadModule: "fbdev"
[    13.911] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.911] (II) Module fbdev: vendor="X.Org Foundation"
[    13.911] 	compiled for 1.15.0, module version = 0.4.4
[    13.911] 	Module class: X.Org Video Driver
[    13.911] 	ABI class: X.Org Video Driver, version 15.0
[    13.911] (II) LoadModule: "vesa"
[    13.911] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.911] (II) Module vesa: vendor="X.Org Foundation"
[    13.911] 	compiled for 1.15.0, module version = 2.3.3
[    13.911] 	Module class: X.Org Video Driver
[    13.911] 	ABI class: X.Org Video Driver, version 15.0
[    13.911] (==) Matched fglrx as autoconfigured driver 0
[    13.911] (==) Matched ati as autoconfigured driver 1
[    13.911] (==) Matched fglrx as autoconfigured driver 2
[    13.911] (==) Matched ati as autoconfigured driver 3
[    13.911] (==) Matched modesetting as autoconfigured driver 4
[    13.911] (==) Matched fbdev as autoconfigured driver 5
[    13.911] (==) Matched vesa as autoconfigured driver 6
[    13.911] (==) Assigned the driver to the xf86ConfigLayout
[    13.911] (II) LoadModule: "fglrx"
[    13.912] (WW) Warning, couldn't open module fglrx
[    13.912] (II) UnloadModule: "fglrx"
[    13.912] (II) Unloading fglrx
[    13.912] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    13.912] (II) LoadModule: "ati"
[    13.912] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    13.912] (II) Module ati: vendor="X.Org Foundation"
[    13.912] 	compiled for 1.15.1, module version = 7.3.0
[    13.912] 	Module class: X.Org Video Driver
[    13.912] 	ABI class: X.Org Video Driver, version 15.0
[    13.912] (II) LoadModule: "modesetting"
[    13.912] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    13.912] (II) Module modesetting: vendor="X.Org Foundation"
[    13.912] 	compiled for 1.15.0, module version = 0.8.1
[    13.912] 	Module class: X.Org Video Driver
[    13.912] 	ABI class: X.Org Video Driver, version 15.0
[    13.912] (II) UnloadModule: "modesetting"
[    13.912] (II) Unloading modesetting
[    13.913] (II) Failed to load module "modesetting" (already loaded, 0)
[    13.913] (II) LoadModule: "fbdev"
[    13.913] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.913] (II) Module fbdev: vendor="X.Org Foundation"
[    13.913] 	compiled for 1.15.0, module version = 0.4.4
[    13.913] 	Module class: X.Org Video Driver
[    13.913] 	ABI class: X.Org Video Driver, version 15.0
[    13.913] (II) UnloadModule: "fbdev"
[    13.913] (II) Unloading fbdev
[    13.913] (II) Failed to load module "fbdev" (already loaded, 0)
[    13.913] (II) LoadModule: "vesa"
[    13.913] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.913] (II) Module vesa: vendor="X.Org Foundation"
[    13.913] 	compiled for 1.15.0, module version = 2.3.3
[    13.913] 	Module class: X.Org Video Driver
[    13.913] 	ABI class: X.Org Video Driver, version 15.0
[    13.913] (II) UnloadModule: "vesa"
[    13.913] (II) Unloading vesa
[    13.913] (II) Failed to load module "vesa" (already loaded, 0)
[    13.913] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    13.921] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    13.921] (II) FBDEV: driver for framebuffer: fbdev
[    13.921] (II) VESA: driver for VESA chipsets: vesa
[    13.921] (++) using VT number 7


[    13.957] (II) [KMS] drm report modesetting isn't supported.
[    13.957] (II) [KMS] drm report modesetting isn't supported.
[    13.957] (II) [KMS] drm report modesetting isn't supported.
[    13.957] (II) [KMS] drm report modesetting isn't supported.
[    13.957] (II) [KMS] drm report modesetting isn't supported.
[    13.958] (WW) Falling back to old probe method for modesetting
[    13.958] (II) Loading sub module "fbdevhw"
[    13.958] (II) LoadModule: "fbdevhw"
[    13.958] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.958] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.958] 	compiled for 1.15.1, module version = 0.0.2
[    13.958] 	ABI class: X.Org Video Driver, version 15.0
[    13.958] (**) FBDEV(6): claimed PCI slot 1@0:0:0
[    13.958] (II) FBDEV(6): using default device
[    13.958] (WW) Falling back to old probe method for vesa
[    13.958] (EE) Screen 0 deleted because of no matching config section.
[    13.958] (II) UnloadModule: "radeon"
[    13.958] (EE) Screen 0 deleted because of no matching config section.
[    13.958] (II) UnloadModule: "radeon"
[    13.958] (EE) Screen 0 deleted because of no matching config section.
[    13.958] (II) UnloadModule: "radeon"
[    13.958] (EE) Screen 0 deleted because of no matching config section.
[    13.958] (II) UnloadModule: "radeon"
[    13.958] (EE) Screen 0 deleted because of no matching config section.
[    13.958] (II) UnloadModule: "modesetting"
[    13.958] (EE) Screen 0 deleted because of no matching config section.
[    13.958] (II) UnloadModule: "modesetting"
[    13.958] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    13.958] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    13.958] (==) FBDEV(0): RGB weight 888
[    13.958] (==) FBDEV(0): Default visual is TrueColor
[    13.958] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    13.958] (II) FBDEV(0): hardware: VESA VGA (video memory: 5120kB)
[    13.958] (II) FBDEV(0): checking modes against framebuffer device...
[    13.958] (II) FBDEV(0): checking modes against monitor...
[    13.958] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    13.958] (**) FBDEV(0):  Built-in mode "current": 131.1 MHz, 80.3 kHz, 76.6 Hz
[    13.958] (II) FBDEV(0): Modeline "current"x0.0  131.09  1280 1312 1472 1632  1024 1028 1032 1048 -hsync -vsync -csync (80.3 kHz b)
[    13.958] (==) FBDEV(0): DPI set to (96, 96)
[    13.958] (II) Loading sub module "fb"
[    13.959] (II) LoadModule: "fb"
[    13.959] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.959] (II) Module fb: vendor="X.Org Foundation"
[    13.959] 	compiled for 1.15.1, module version = 1.0.0
[    13.959] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.959] (**) FBDEV(0): using shadow framebuffer
[    13.959] (II) Loading sub module "shadow"
[    13.959] (II) LoadModule: "shadow"
[    13.959] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    13.959] (II) Module shadow: vendor="X.Org Foundation"
[    13.959] 	compiled for 1.15.1, module version = 1.1.0
[    13.959] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.959] (II) UnloadModule: "radeon"
[    13.959] (II) UnloadModule: "vesa"
[    13.959] (II) Unloading vesa
[    13.959] (==) Depth 24 pixmap format is 32 bpp
[    13.959] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    13.959] (==) FBDEV(0): Backing store enabled
[    13.960] (==) FBDEV(0): DPMS enabled
[    13.960] (==) RandR enabled
[    13.966] (II) SELinux: Disabled on system
[    13.966] (II) AIGLX: Screen 0 is not DRI2 capable
[    13.966] (EE) AIGLX: reverting to software rendering
[    14.047] (II) AIGLX: Loaded and initialized swrast
[    14.047] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    14.060] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.064] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.064] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.064] (II) LoadModule: "evdev"
[    14.064] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.071] (II) Module evdev: vendor="X.Org Foundation"
[    14.071] 	compiled for 1.15.0, module version = 2.8.2
[    14.071] 	Module class: X.Org XInput Driver
[    14.071] 	ABI class: X.Org XInput driver, version 20.0
[    14.071] (II) Using input driver 'evdev' for 'Power Button'
[    14.071] (**) Power Button: always reports core events
[    14.071] (**) evdev: Power Button: Device: "/dev/input/event1"
[    14.071] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.071] (--) evdev: Power Button: Found keys
[    14.071] (II) evdev: Power Button: Configuring as keyboard
[    14.071] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.071] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    14.071] (**) Option "xkb_rules" "evdev"
[    14.071] (**) Option "xkb_model" "pc105"
[    14.071] (**) Option "xkb_layout" "us"
[    14.071] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.071] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.071] (II) Using input driver 'evdev' for 'Power Button'
[    14.071] (**) Power Button: always reports core events
[    14.071] (**) evdev: Power Button: Device: "/dev/input/event0"
[    14.072] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.072] (--) evdev: Power Button: Found keys
[    14.072] (II) evdev: Power Button: Configuring as keyboard
[    14.072] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.072] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    14.072] (**) Option "xkb_rules" "evdev"
[    14.072] (**) Option "xkb_model" "pc105"
[    14.072] (**) Option "xkb_layout" "us"
[    14.072] (II) config/udev: Adding drm device (/dev/dri/card0)
[    14.072] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    14.072] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event8)
[    14.072] (II) No input driver specified, ignoring this device.
[    14.072] (II) This device may have been added with another device file.
[    14.073] (II) config/udev: Adding input device Microsoft Microsoft® Comfort Mouse 4500 (/dev/input/event2)
[    14.073] (**) Microsoft Microsoft® Comfort Mouse 4500: Applying InputClass "evdev pointer catchall"
[    14.073] (**) Microsoft Microsoft® Comfort Mouse 4500: Applying InputClass "evdev keyboard catchall"
[    14.073] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Comfort Mouse 4500'
[    14.073] (**) Microsoft Microsoft® Comfort Mouse 4500: always reports core events
[    14.073] (**) evdev: Microsoft Microsoft® Comfort Mouse 4500: Device: "/dev/input/event2"
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Vendor 0x45e Product 0x76c
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found 9 mouse buttons
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found scroll wheel(s)
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found relative axes
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found x and y relative axes
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found absolute axes
[    14.073] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Forcing absolute x/y axes to exist.
[    14.073] (--) evdev: Microsoft Microsoft® Comfort Mouse 4500: Found keys
[    14.073] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Configuring as mouse
[    14.073] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Configuring as keyboard
[    14.073] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: Adding scrollwheel support
[    14.073] (**) evdev: Microsoft Microsoft® Comfort Mouse 4500: YAxisMapping: buttons 4 and 5
[    14.073] (**) evdev: Microsoft Microsoft® Comfort Mouse 4500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.073] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input5/event2"
[    14.073] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Comfort Mouse 4500" (type: KEYBOARD, id 8)
[    14.073] (**) Option "xkb_rules" "evdev"
[    14.073] (**) Option "xkb_model" "pc105"
[    14.073] (**) Option "xkb_layout" "us"
[    14.073] (II) evdev: Microsoft Microsoft® Comfort Mouse 4500: initialized for relative axes.
[    14.073] (WW) evdev: Microsoft Microsoft® Comfort Mouse 4500: ignoring absolute axes.
[    14.073] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) keeping acceleration scheme 1
[    14.073] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) acceleration profile 0
[    14.074] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) acceleration factor: 2.000
[    14.074] (**) Microsoft Microsoft® Comfort Mouse 4500: (accel) acceleration threshold: 4
[    14.074] (II) config/udev: Adding input device Microsoft Microsoft® Comfort Mouse 4500 (/dev/input/mouse0)
[    14.074] (II) No input driver specified, ignoring this device.
[    14.074] (II) This device may have been added with another device file.
[    14.074] (II) config/udev: Adding input device HID 0b38:0010 (/dev/input/event3)
[    14.074] (**) HID 0b38:0010: Applying InputClass "evdev keyboard catchall"
[    14.074] (II) Using input driver 'evdev' for 'HID 0b38:0010'
[    14.074] (**) HID 0b38:0010: always reports core events
[    14.074] (**) evdev: HID 0b38:0010: Device: "/dev/input/event3"
[    14.074] (--) evdev: HID 0b38:0010: Vendor 0xb38 Product 0x10
[    14.074] (--) evdev: HID 0b38:0010: Found keys
[    14.074] (II) evdev: HID 0b38:0010: Configuring as keyboard
[    14.074] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.0/input/input6/event3"
[    14.074] (II) XINPUT: Adding extended input device "HID 0b38:0010" (type: KEYBOARD, id 9)
[    14.074] (**) Option "xkb_rules" "evdev"
[    14.075] (**) Option "xkb_model" "pc105"
[    14.075] (**) Option "xkb_layout" "us"
[    14.075] (II) config/udev: Adding input device HID 0b38:0010 (/dev/input/event4)
[    14.075] (**) HID 0b38:0010: Applying InputClass "evdev keyboard catchall"
[    14.075] (II) Using input driver 'evdev' for 'HID 0b38:0010'
[    14.075] (**) HID 0b38:0010: always reports core events
[    14.075] (**) evdev: HID 0b38:0010: Device: "/dev/input/event4"
[    14.075] (--) evdev: HID 0b38:0010: Vendor 0xb38 Product 0x10
[    14.075] (--) evdev: HID 0b38:0010: Found 1 mouse buttons
[    14.075] (--) evdev: HID 0b38:0010: Found scroll wheel(s)
[    14.075] (--) evdev: HID 0b38:0010: Found relative axes
[    14.075] (II) evdev: HID 0b38:0010: Forcing relative x/y axes to exist.
[    14.075] (--) evdev: HID 0b38:0010: Found absolute axes
[    14.075] (II) evdev: HID 0b38:0010: Forcing absolute x/y axes to exist.
[    14.075] (--) evdev: HID 0b38:0010: Found keys
[    14.075] (II) evdev: HID 0b38:0010: Configuring as mouse
[    14.075] (II) evdev: HID 0b38:0010: Configuring as keyboard
[    14.075] (II) evdev: HID 0b38:0010: Adding scrollwheel support
[    14.075] (**) evdev: HID 0b38:0010: YAxisMapping: buttons 4 and 5
[    14.075] (**) evdev: HID 0b38:0010: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.075] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2:1.1/input/input7/event4"
[    14.075] (II) XINPUT: Adding extended input device "HID 0b38:0010" (type: KEYBOARD, id 10)
[    14.075] (**) Option "xkb_rules" "evdev"
[    14.075] (**) Option "xkb_model" "pc105"
[    14.075] (**) Option "xkb_layout" "us"
[    14.076] (II) evdev: HID 0b38:0010: initialized for relative axes.
[    14.076] (WW) evdev: HID 0b38:0010: ignoring absolute axes.
[    14.076] (**) HID 0b38:0010: (accel) keeping acceleration scheme 1
[    14.076] (**) HID 0b38:0010: (accel) acceleration profile 0
[    14.076] (**) HID 0b38:0010: (accel) acceleration factor: 2.000
[    14.076] (**) HID 0b38:0010: (accel) acceleration threshold: 4
[    14.076] (II) config/udev: Adding input device HDA NVidia Line Out (/dev/input/event5)
[    14.076] (II) No input driver specified, ignoring this device.
[    14.076] (II) This device may have been added with another device file.
[    14.077] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event7)
[    14.077] (II) No input driver specified, ignoring this device.
[    14.077] (II) This device may have been added with another device file.
[    14.077] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event6)
[    14.077] (II) No input driver specified, ignoring this device.
[    14.077] (II) This device may have been added with another device file.
[    14.084] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    30.566] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.578] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.730] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.760] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.770] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.773] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.776] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.780] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.782] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.794] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    30.797] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

```

---

### Post by Yellow Pasque on 2014-06-29
Okay, that makes sense. The nomodeset option would cause that error message. If you remove nomodeset and radeon.dpm=1 (and then run sudo update-grub), do you still get a black screen?

---

### Post by sp40140 on 2014-06-29
As to your issue about being kicked back to log-in screen.
The easiest fix: go to tty1- command line. Rename ~/.xauthority to ~/.xauthority_backup. And Reboot. Some config files in that folder are messed up. The .xauthority will be re-created when you boot next time.
I had this issue while dealing with follwing issue.

OK. I just went through this mess with my HD7770 card.
My Issue:
OpengGL drivers worked for vid. BUT hdmi Audio not available. Due to it being disabled in kernel.
Suggested fixes: 
1] use ATI prop drivers. 
Result: Didn't work. Crashed my Unity. (even with couple diff versions of drivers including beta).
2]Enable the ATI audio in kernel using grub so it can be used with OpenGL. 
Result:This didn't work either. eventhough I can see that the paramerter is being passed.
3] upgrade Kernel to latest or 1.13 or newer.
EUREKA. This worked. I upgraded to 3.14 (latest stable in mainline). No need to prop ati drivers. OpenGL works as the audio has been enabled in 13.3.

Cheers,

---

### Post by sparky741pa on 2014-06-30
Temujin,

I removed the nomodeset and radeon.dpm=1 from the grub cfg and it comes up to my login screen, but it is all garbled and I cannot make out any text.  I can kind of see the mouse pointer as I move it around the screen, but something still isn't right.  So for now, I put nomodeset back in until hopefully we figure this out.

---

### Post by sparky741pa on 2014-07-01
Temujin,

Just wanted to add that since I put the nomodeset back in the startup file, it rebooted once and then came up OK.  When I checked what driver it is using, the Gallium 0.4 is gone and the VESA:RV620 is there again.  What should it actually say when the opensource driver is correctly loaded?  If you would like a fresh log file since it has changed, let me know and I will gladly post it.

---

### Post by Yellow Pasque on 2014-07-02
> What should it actually say when the opensource driver is correctly loaded? 
Something like "Gallium 0.4 on AMD RV620" would be what you want to see from glxinfo (but it's not going to work correctly with 'nomodeset').

I would try blacklisting radeon kernel module, rebooting and then loading it manually (and also then look at dmesg): [http://www.x.org/wiki/radeonBuildHowTo/#index2h1](http://www.x.org/wiki/radeonBuildHowTo/#index2h1)
```
echo "blacklist radeon" | sudo tee /etc/modprobe.d/radeon.conf
```

---

### Post by sparky741pa on 2014-07-03
Temujin,

Most of that compiling code is beyond the scope of my Linux knowledge/ability at this point and I would rather not delve into it.  Yes it looks to be copy and paste, but I don't want to mess anything up.  I don't know if a reinstall would help me or not because I had previously tried installing Mint and the garbled video was something that happened with it as well.  That's what prompted me to use Ubuntu as it installed cleanly and I was able to get a login screen at least, whereas I could not with Mint.  Eventually the same video issue occured on Ubuntu(probably after the first or second reboot when it decided to use the open source driver), but with some Googling, I found that if I added the nomodeset xforcevesa to the startup, I could get back to a legible login screen.  Should I perhaps roll back to 12.04 or 12.10 LTS?  I don't know what else to try.

---

### Post by Yellow Pasque on 2014-07-03
> Most of that compiling code is beyond the scope of my Linux knowledge/ability
I was referring specifically to the section "Hints to dig deeper into radeon-KMS problems on startup" so that you could get specific error messages to google/report.

Your options:
1. Use an older version (if it works).
2. Stay with current version, use nomodeset, and call it a day.
3. Try latest kernel to see if your issue has been fixed  (and if it hasn't been fixed, report it)
[https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Installing_upstream_kernels)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-rc3-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16-rc3-utopic/)

---

### Post by sparky741pa on 2014-07-03
Temujin,

My bad.  For some reason, that link doesn't open correctly in Chrome, but does in Firefox.  I didn't initially see the section you were referring to.  I tried the steps listed there to no avail.  I found an Nvidia Geforce 8400 GS sitting around in its box, so I googled it and found it works fairly problem free with Ubuntu, so I installed the drivers, put the card in and it works like a dream.  I did notice, however, when I did an update, that there were some ATI/AMD drivers on the list, so I may throw the Radeon back in and see if it will work now, but if not, it seems I found a card that suits my needs for the time being.  Thank you again for your help.

---

### Post by Yellow Pasque on 2014-07-04
You're welcome. Please mark thread solved.

---

### Post by mastablasta on 2014-07-04
heh, good to know i guess i will be staying on WinXP on main PC afterall. it's ridiculous sicne both Xorg and UButnu claim these chips work and they clearly do not work propperly. so devs shoudl i etiehr fix it or remove the note that it is all working nice and dandy. i can't get 9200 to work with 3D and i know radeon 3650 HD is loading Ubuntu and other linux live session only with nomodeseting (this is where i was thinking of loading Linux to). i haven't tried manjaro or fedora yet. in any case claims that these chips work should be removed forom wiki under "these chips have full hardware acceleration" if they don't.

so yeah i guess i will be extendting the NTFS through whole empty disk space..

---

### Post by mörgæs on 2014-07-04
Radeon 9200 is more than ten years old. Demanding that it works with the latest Ubuntu is not realistic. Go for Lubuntu.

Where did you see that there is 3D support for a 9200?

---

### Post by mastablasta on 2014-07-04
yeah i am not too worried about 9200 it is used mostly for internet...still kind of makes you wonder - one can play morrowind normally on old WindowsXP on that mashcine. at the moment it has kubuntu installed with effects turned off. it is fast and responsive. haven't tried morrowind yet in wine. it would need more disk space and even more of my time.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> [h=2]Fully Supported[/h]
All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list: 
R100                        Radeon 7200
RV100                       Radeon 7000(VE), M6, RN50/ES1000 (2D only)
RS100                       Radeon IGP320(M)
RV200                       Radeon 7500, M7, FireGL 7800
RS200                       Radeon IGP330(M)/IGP340(M)
RS250                       Radeon Mobility 7000 IGP
R200                        Radeon 8500, 9100, FireGL 8800/8700
RV250                       Radeon 9000PRO/9000, M9
RV280                       Radeon 9200PRO/9200/9200SE/9250, M9+
RS300                       Radeon 9100 IGP
RS350                       Radeon 9200 IGP


---

### Post by mörgæs on 2014-07-04
Yes, the page does need some corrections. I hope someone with more ATI knowledge than me is aware of it.

---

### Post by Yellow Pasque on 2014-07-04
> **mastablasta said:**
> It's ridiculous since both Xorg and Ubuntu claim these chips work and they clearly do not work properly. so devs should either fix it or remove the note that it is all working nice and dandy.

The problem may have already been fixed upstream in kernel, and if it isn't, devs can't fix a problem if they can't access logs. They don't have access to every card made.

> i can't get 9200 to work with 3D
As for the Radeon 9200, mesa does support 3D to the extent of the hardware's capability (OpenGL 1.4). With 3D desktops like Unity requiring OpenGL 2.x, I can see why a user would consider the card unsupported. I will add a not to the doc.

> One can play morrowind normally on old WindowsXP
Morrowind is a DirectX 8.x title, so I don't think it's a good comparison point.

---

### Post by mastablasta on 2014-07-06
well i did some test today on my home PC - can't believe i had about 30 minutes of time...

Radeon 3650 seems to be working ( i mean i couldn't test it with a game or something), sound works (though only as analog stereo no software 3D sound...), scaner works kind of. the scans are really bad and preview crashed it (this might improve with official scan program that i didn't have time to install), printing wokrs, i could test the mic - no matter what input i chose in audacity nothing was recorded - funny how same program in windows has no issue finding one or two audio inputs), camera works, mouse works but only 3 buttons are recognised. that's about as much as i could test in a short time.

yeah the 9200 is old. so i guess the half-life should run well in wine then with open gl? i just gave morrowing as comparison as i think it's the most demanding game i played on that PC. hmm another one that could propperly test it is return to castle wolfenstein or better yet the opensource enemy territory. just to see if it runs as well as it did on windows. and if it doesn't then it's time to rethink "the strategy" and try to get that disk with windows XP working or replace it with a new one and extend the life of that maschine a bit. but i have to be hones that computer is not at my house so i rarely have time to tinker with it. seems it is workign fine for non graphic stuff though it did once loose the sound.

---

