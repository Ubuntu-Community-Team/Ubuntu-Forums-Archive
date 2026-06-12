---
title: "I think my GPU is overheating"
date: 2014-10-16
forum: Hardware
---

### Post by ozanji345 on 2014-10-16
I am currently running Ubuntu 14.04. My graphics card is an Asus Radeon 6670. My monitor goes black and then my fans spin faster and louder and I can't turn off the tower; I have to unplug it. This happens usually between 20-40 minutes of running Ubuntu. I have tried switching to the proprietary "flgrx-updates" driver, but that made it last until 1-2 hours before "overheating". This doesn't happen when I run Windows 8.1. Any help is greatly appreciated!

---

### Post by marcodasilva26 on 2014-10-16
You need to know for sure if you are overheating. What temperatures do you have?

---

### Post by ozanji345 on 2014-10-16
How do I check my temp?

---

### Post by marcodasilva26 on 2014-10-16
You can install lm-sensors or you can use this app [http://sourceforge.net/projects/amdovdrvctrl/](http://sourceforge.net/projects/amdovdrvctrl/)

---

### Post by ozanji345 on 2014-10-17
It's at 56 degrees C.

---

### Post by marcodasilva26 on 2014-10-17
If that's idle temperature....that's really high. I have an HD6670 2gb by saphire and i have arround 38°c@idle and arround 50° under full load. 

Does your card have a fan por it's Passive cooled?

Do you have the same temperatures under windows?

---

### Post by ozanji345 on 2014-10-17
My temp in windows is around 36 degrees C. 
My GPU is an Asus Radeon 6670 1GB to be exact if you wanna look it up. I just unplugged it and I'm using my intergrated graphics (Radeon HD 7560D), and I'll see if the computer crashes or not.

---

### Post by mörgæs on 2014-10-17
If you are using Radeon drivers then the setting radeon.dpm=1 might help. More here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Some Radeon-relevant changes are coming in 14.10, but I don't know if they are significant. Did you try it?

---

### Post by ozanji345 on 2014-10-17
My computer still goes into the "monitor off with CPU and GPU fans spinning really fast," even with my intergrated graphics that i switched to. I put my Radeon 6670 back in so I can try and fix this problem. I'll try and set the dpm to 1 and let you know if anything happens!

---

### Post by ozanji345 on 2014-10-17
Okay so I changed the grub file to radeon.dpm=1 and the crash is still happening... any other suggestions?

---

### Post by tgalati4 on 2014-10-17
The dpm switch just turns on the dynamic clock so that the GPU clock speed goes up and down with load--like Intel Speedstep.  If you have a GPU chip problem or heat sink problem, then more drastic measures are needed.  Take everything out of the machine.  Put in one hard disk, minimum RAM, remove graphics card.  See if you can boot with this minimum condition.  You might have a failed motherboard.  Any bulging or leaking capacitors?

---

### Post by ozanji345 on 2014-10-17
It's not a hardware problem because everything works fine in Windows. This is a problem with my build on Ubuntu 14.04.

---

### Post by tgalati4 on 2014-10-17
Sorry, missed that in your first post.  What's in your log file:

```
more /var/log/Xorg.0.log
```

---

### Post by ozanji345 on 2014-10-17
```
[    28.880] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    28.880] X Protocol Version 11, Revision 0
[    28.880] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    28.880] Current Operating System: Linux OMAR-UBUNTU 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    28.880] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic.efi.signed root=UUID=ef0a2d99-2b0d-4a48-a76f-3e8a1ea80b30 ro quiet splash radeon.dpm=1 vt.handoff=7
[    28.880] Build Date: 30 July 2014  12:21:54AM
[    28.880] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.880] Current version of pixman: 0.30.2
[    28.880]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    28.880] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.880] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 17 18:40:26 2014
[    28.931] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.931] (==) No Layout section.  Using the first Screen section.
[    28.931] (==) No screen section available. Using defaults.
[    28.931] (**) |-->Screen "Default Screen Section" (0)
[    28.931] (**) |   |-->Monitor "<default monitor>"
[    28.931] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.931] (==) Automatically adding devices
[    28.932] (==) Automatically enabling devices
[    28.932] (==) Automatically adding GPU devices
[    28.932] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.932]     Entry deleted from font path.
[    28.932] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.932]     Entry deleted from font path.
[    28.932] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.932]     Entry deleted from font path.
[    28.932] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.932]     Entry deleted from font path.
[    28.932] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.932]     Entry deleted from font path.
[    28.932] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    28.932] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.932] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.932] (II) Loader magic: 0x7fc77b484d40
[    28.932] (II) Module ABI versions:
[    28.932]     X.Org ANSI C Emulation: 0.4
[    28.932]     X.Org Video Driver: 15.0
[    28.932]     X.Org XInput driver : 20.0
[    28.932]     X.Org Server Extension : 8.0
[    28.933] (--) PCI:*(0:1:0:0) 1002:6758:1043:03ea rev 0, Mem @ 0xd0000000/268435456, 0xfea20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    28.933] Initializing built-in extension Generic Event Extension
[    28.933] Initializing built-in extension SHAPE
[    28.933] Initializing built-in extension MIT-SHM
[    28.933] Initializing built-in extension XInputExtension
[    28.933] Initializing built-in extension XTEST
[    28.933] Initializing built-in extension BIG-REQUESTS
[    28.933] Initializing built-in extension SYNC
[    28.933] Initializing built-in extension XKEYBOARD
[    28.933] Initializing built-in extension XC-MISC
[    28.933] Initializing built-in extension SECURITY
[    28.933] Initializing built-in extension XINERAMA
[    28.933] Initializing built-in extension XFIXES
[    28.933] Initializing built-in extension RENDER
[    28.933] Initializing built-in extension RANDR
[    28.933] Initializing built-in extension COMPOSITE
[    28.933] Initializing built-in extension DAMAGE
[    28.933] Initializing built-in extension MIT-SCREEN-SAVER
[    28.933] Initializing built-in extension DOUBLE-BUFFER
[    28.933] Initializing built-in extension RECORD
[    28.933] Initializing built-in extension DPMS
[    28.933] Initializing built-in extension Present
[    28.933] Initializing built-in extension DRI3
[    28.933] Initializing built-in extension X-Resource
[    28.933] Initializing built-in extension XVideo
[    28.933] Initializing built-in extension XVideo-MotionCompensation
[    28.933] Initializing built-in extension SELinux
[    28.933] Initializing built-in extension XFree86-VidModeExtension
[    28.933] Initializing built-in extension XFree86-DGA
[    28.933] Initializing built-in extension XFree86-DRI
[    28.933] Initializing built-in extension DRI2
[    28.933] (II) LoadModule: "glx"
[    28.942] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    28.942] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    28.942]     compiled for 6.9.0, module version = 1.0.0
[    28.943] Loading extension GLX
[    28.943] (==) Matched fglrx as autoconfigured driver 0
[    28.943] (==) Matched ati as autoconfigured driver 1
[    28.943] (==) Matched modesetting as autoconfigured driver 2
[    28.943] (==) Matched fbdev as autoconfigured driver 3
[    28.943] (==) Matched vesa as autoconfigured driver 4
[    28.943] (==) Assigned the driver to the xf86ConfigLayout
[    28.943] (II) LoadModule: "fglrx"
[    28.943] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    28.963] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    28.963]     compiled for 1.4.99.906, module version = 13.35.5
[    28.963]     Module class: X.Org Video Driver
[    28.963] (II) Loading sub module "fglrxdrm"
[    28.963] (II) LoadModule: "fglrxdrm"
[    28.964] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    29.077] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    29.077]     compiled for 1.4.99.906, module version = 13.35.5
[    29.077] (II) LoadModule: "ati"
[    29.095] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    29.095] (II) Module ati: vendor="X.Org Foundation"
[    29.095]     compiled for 1.15.1, module version = 7.3.0
[    29.095]     Module class: X.Org Video Driver
[    29.095]     ABI class: X.Org Video Driver, version 15.0
[    29.095] (II) LoadModule: "radeon"
[    29.096] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    29.232] (II) Module radeon: vendor="X.Org Foundation"
[    29.232]     compiled for 1.15.1, module version = 7.3.0
[    29.232]     Module class: X.Org Video Driver
[    29.232]     ABI class: X.Org Video Driver, version 15.0
[    29.232] (II) LoadModule: "modesetting"
[    29.232] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.232] (II) Module modesetting: vendor="X.Org Foundation"
[    29.232]     compiled for 1.15.0, module version = 0.8.1
[    29.232]     Module class: X.Org Video Driver
[    29.232]     ABI class: X.Org Video Driver, version 15.0
[    29.232] (II) LoadModule: "fbdev"
[    29.232] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.232] (II) Module fbdev: vendor="X.Org Foundation"
[    29.232]     compiled for 1.15.0, module version = 0.4.4
[    29.232]     Module class: X.Org Video Driver
[    29.232]     ABI class: X.Org Video Driver, version 15.0
[    29.232] (II) LoadModule: "vesa"
[    29.233] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.233] (II) Module vesa: vendor="X.Org Foundation"
[    29.233]     compiled for 1.15.0, module version = 2.3.3
[    29.233]     Module class: X.Org Video Driver
[    29.233]     ABI class: X.Org Video Driver, version 15.0
[    29.233] (II) AMD Proprietary Linux Driver Version Identifier:13.35.5
[    29.233] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.35.1005               
[    29.233] (II) AMD Proprietary Linux Driver Build Date: Mar 12 2014 10:32:23
[    29.233] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    29.239] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.239] (II) FBDEV: driver for framebuffer: fbdev
[    29.239] (II) VESA: driver for VESA chipsets: vesa
[    29.239] (++) using VT number 7

[    29.239] (WW) Falling back to old probe method for fglrx
[    29.245] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    29.257] ukiDynamicMajor: found major device number 250
[    29.258] (--) Assigning device section with no busID to primary device
[    29.258] (--) Chipset Supported AMD Graphics Processor (0x6758) found
[    29.259] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    29.259] (II) fglrx(0): pEnt->device->identifier=0x7fc77b21ff57
[    29.259] (WW) Falling back to old probe method for modesetting
[    29.259] (EE) open /dev/dri/card0: No such file or directory
[    29.259] (WW) Falling back to old probe method for fbdev
[    29.259] (II) Loading sub module "fbdevhw"
[    29.259] (II) LoadModule: "fbdevhw"
[    29.259] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.259] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.259]     compiled for 1.15.1, module version = 0.0.2
[    29.259]     ABI class: X.Org Video Driver, version 15.0
[    29.259] (WW) Falling back to old probe method for vesa
[    29.259] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    29.260] (II) Loading sub module "vgahw"
[    29.260] (II) LoadModule: "vgahw"
[    29.260] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    29.260] (II) Module vgahw: vendor="X.Org Foundation"
[    29.260]     compiled for 1.15.1, module version = 0.1.0
[    29.260]     ABI class: X.Org Video Driver, version 15.0
[    29.260] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.261] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[    29.261] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    29.261] (==) fglrx(0): Default visual is TrueColor
[    29.261] (==) fglrx(0): RGB weight 888
[    29.261] (II) fglrx(0): Using 8 bits per RGB 
[    29.261] (==) fglrx(0): Buffer Tiling is ON
[    29.261] (II) Loading sub module "fglrxdrm"
[    29.261] (II) LoadModule: "fglrxdrm"
[    29.261] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    29.261] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    29.261]     compiled for 1.4.99.906, module version = 13.35.5
[    29.272] ukiDynamicMajor: found major device number 250
[    29.273] ukiDynamicMajor: found major device number 250
[    29.273] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.273] ukiOpenDevice: node name is /dev/ati/card0
[    29.273] ukiOpenDevice: open result is 11, (OK)
[    29.419] ukiOpenByBusid: ukiOpenMinor returns 11
[    29.419] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.419] (**) fglrx(0): NoAccel = NO
[    29.419] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    29.419] (--) fglrx(0): Chipset: "AMD Radeon HD 6670" (Chipset = 0x6758)
[    29.419] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x03ea)
[    29.419] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    29.419] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    29.419] (--) fglrx(0): MMIO registers at 0xfea20000
[    29.419] (--) fglrx(0): I/O port at 0x0000e000
[    29.419] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    29.419] (II) fglrx(0): AC Adapter is used
[    29.420] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    29.420] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    29.420] (II) fglrx(0): PCIE card detected
[    29.420] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    29.420] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    29.420] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    29.420] (II) fglrx(0): RandR 1.2 support is enabled!
[    29.420] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    29.420] (II) Loading sub module "fb"
[    29.420] (II) LoadModule: "fb"
[    29.420] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.420] (II) Module fb: vendor="X.Org Foundation"
[    29.420]     compiled for 1.15.1, module version = 1.0.0
[    29.420]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.420] (II) fglrx(0): EDID Management option: EDID Management is enabled
[    29.420] (II) Loading sub module "ddc"
[    29.420] (II) LoadModule: "ddc"
[    29.420] (II) Module "ddc" already built-in
[    29.505] (II) fglrx(0): Output DFP1 has no monitor section
[    29.505] (II) fglrx(0): Output DFP2 has no monitor section
[    29.505] (II) fglrx(0): Output DFP3 has no monitor section
[    29.506] (II) fglrx(0): Output DFP4 has no monitor section
[    29.506] (II) fglrx(0): Output DFP5 has no monitor section
[    29.506] (II) fglrx(0): Output DFP6 has no monitor section
[    29.506] (II) fglrx(0): Output CRT1 has no monitor section
[    29.506] (II) Loading sub module "ddc"
[    29.506] (II) LoadModule: "ddc"
[    29.506] (II) Module "ddc" already built-in
[    29.506] (II) fglrx(0): Connected Display0: DFP5
[    29.506] (II) fglrx(0): Display0 EDID data ---------------------------
[    29.506] (II) fglrx(0): Manufacturer: DEL  Model: d04a  Serial#: 825379668
[    29.506] (II) fglrx(0): Year: 2012  Week: 31
[    29.506] (II) fglrx(0): EDID Version: 1.3
[    29.506] (II) fglrx(0): Digital Display Input
[    29.506] (II) fglrx(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    29.506] (II) fglrx(0): Gamma: 2.20
[    29.506] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    29.506] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.506] (II) fglrx(0): First detailed timing is preferred mode
[    29.506] (II) fglrx(0): redX: 0.638 redY: 0.331   greenX: 0.310 greenY: 0.624
[    29.506] (II) fglrx(0): blueX: 0.155 blueY: 0.066   whiteX: 0.313 whiteY: 0.329
[    29.506] (II) fglrx(0): Supported established timings:
[    29.506] (II) fglrx(0): 720x400@70Hz
[    29.506] (II) fglrx(0): 640x480@60Hz
[    29.506] (II) fglrx(0): 640x480@75Hz
[    29.506] (II) fglrx(0): 800x600@60Hz
[    29.506] (II) fglrx(0): 800x600@75Hz
[    29.506] (II) fglrx(0): 1024x768@60Hz
[    29.506] (II) fglrx(0): 1024x768@75Hz
[    29.506] (II) fglrx(0): 1280x1024@75Hz
[    29.506] (II) fglrx(0): Manufacturer's mask: 0
[    29.506] (II) fglrx(0): Supported standard timings:
[    29.506] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    29.506] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    29.506] (II) fglrx(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    29.506] (II) fglrx(0): Supported detailed timing:
[    29.506] (II) fglrx(0): clock: 148.5 MHz   Image Size:  509 x 286 mm
[    29.506] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    29.506] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    29.506] (II) fglrx(0): Serial No: VWXFG28412KT
[    29.506] (II) fglrx(0): Monitor name: DELL S2330MX
[    29.506] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    29.506] (II) fglrx(0): EDID (in hex):
[    29.506] (II) fglrx(0):     00ffffffffffff0010ac4ad0544b3231
[    29.506] (II) fglrx(0):     1f16010380331d78ea77c5a3544f9f27
[    29.506] (II) fglrx(0):     115054a54b00714f8180d1c001010101
[    29.506] (II) fglrx(0):     010101010101023a801871382d40582c
[    29.506] (II) fglrx(0):     4500fd1e1100001e000000ff00565758
[    29.506] (II) fglrx(0):     464732383431324b540a000000fc0044
[    29.506] (II) fglrx(0):     454c4c2053323333304d580a000000fd
[    29.506] (II) fglrx(0):     00384c1e5311000a202020202020006e
[    29.506] (II) fglrx(0): End of Display0 EDID data --------------------
[    29.506] (II) fglrx(0): Dynamic Surface Resizing Enabled
[    29.507] (II) fglrx(0): EDID for output DFP1
[    29.507] (II) fglrx(0): EDID for output DFP2
[    29.507] (II) fglrx(0): EDID for output DFP3
[    29.507] (II) fglrx(0): EDID for output DFP4
[    29.507] (II) fglrx(0): EDID for output DFP5
[    29.507] (II) fglrx(0): Manufacturer: DEL  Model: d04a  Serial#: 825379668
[    29.507] (II) fglrx(0): Year: 2012  Week: 31
[    29.507] (II) fglrx(0): EDID Version: 1.3
[    29.507] (II) fglrx(0): Digital Display Input
[    29.507] (II) fglrx(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    29.507] (II) fglrx(0): Gamma: 2.20
[    29.507] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    29.507] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.507] (II) fglrx(0): First detailed timing is preferred mode
[    29.507] (II) fglrx(0): redX: 0.638 redY: 0.331   greenX: 0.310 greenY: 0.624
[    29.507] (II) fglrx(0): blueX: 0.155 blueY: 0.066   whiteX: 0.313 whiteY: 0.329
[    29.507] (II) fglrx(0): Supported established timings:
[    29.507] (II) fglrx(0): 720x400@70Hz
[    29.507] (II) fglrx(0): 640x480@60Hz
[    29.507] (II) fglrx(0): 640x480@75Hz
[    29.507] (II) fglrx(0): 800x600@60Hz
[    29.507] (II) fglrx(0): 800x600@75Hz
[    29.507] (II) fglrx(0): 1024x768@60Hz
[    29.507] (II) fglrx(0): 1024x768@75Hz
[    29.507] (II) fglrx(0): 1280x1024@75Hz
[    29.507] (II) fglrx(0): Manufacturer's mask: 0
[    29.507] (II) fglrx(0): Supported standard timings:
[    29.507] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    29.507] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    29.507] (II) fglrx(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    29.507] (II) fglrx(0): Supported detailed timing:
[    29.507] (II) fglrx(0): clock: 148.5 MHz   Image Size:  509 x 286 mm
[    29.507] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    29.507] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    29.507] (II) fglrx(0): Serial No: VWXFG28412KT
[    29.507] (II) fglrx(0): Monitor name: DELL S2330MX
[    29.507] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    29.507] (II) fglrx(0): EDID (in hex):
[    29.507] (II) fglrx(0):     00ffffffffffff0010ac4ad0544b3231
[    29.507] (II) fglrx(0):     1f16010380331d78ea77c5a3544f9f27
[    29.507] (II) fglrx(0):     115054a54b00714f8180d1c001010101
[    29.507] (II) fglrx(0):     010101010101023a801871382d40582c
[    29.507] (II) fglrx(0):     4500fd1e1100001e000000ff00565758
[    29.507] (II) fglrx(0):     464732383431324b540a000000fc0044
[    29.507] (II) fglrx(0):     454c4c2053323333304d580a000000fd
[    29.507] (II) fglrx(0):     00384c1e5311000a202020202020006e
[    29.507] (II) fglrx(0): Printing probed modes for output DFP5
[    29.507] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    29.507] (II) fglrx(0): Modeline "1680x1050"x60.0  148.50  1680 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1400x1050"x60.0  148.50  1400 2008 2052 2200  1050 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1600x900"x60.0  148.50  1600 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1360x1024"x60.0  148.50  1360 2008 2052 2200  1024 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1440x900"x60.0  148.50  1440 2008 2052 2200  900 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1152x864"x60.0  148.50  1152 2008 2052 2200  864 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.507] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.507] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.507] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.507] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.507] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.507] (II) fglrx(0): EDID for output DFP6
[    29.507] (II) fglrx(0): EDID for output CRT1
[    29.507] (II) fglrx(0): Output DFP1 disconnected
[    29.507] (II) fglrx(0): Output DFP2 disconnected
[    29.508] (II) fglrx(0): Output DFP3 disconnected
[    29.508] (II) fglrx(0): Output DFP4 disconnected
[    29.508] (II) fglrx(0): Output DFP5 connected
[    29.508] (II) fglrx(0): Output DFP6 disconnected
[    29.508] (II) fglrx(0): Output CRT1 disconnected
[    29.508] (II) fglrx(0): Using exact sizes for initial modes
[    29.508] (II) fglrx(0): Output DFP5 using initial mode 1920x1080
[    29.508] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.508] (II) fglrx(0): DPI set to (96, 96)
[    29.508] (II) fglrx(0): Eyefinity capable adapter detected.
[    29.508] (II) fglrx(0): Adapter AMD Radeon HD 6670 has 6 configurable heads and 1 displays connected.
[    29.508] (==) fglrx(0):  PseudoColor visuals disabled
[    29.508] (II) Loading sub module "ramdac"
[    29.508] (II) LoadModule: "ramdac"
[    29.508] (II) Module "ramdac" already built-in
[    29.508] (==) fglrx(0): NoDRI = NO
[    29.508] (==) fglrx(0): Capabilities: 0x00000000
[    29.508] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    29.508] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    29.508] (==) fglrx(0): UseFastTLS=0
[    29.508] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[    29.508] (II) UnloadModule: "radeon"
[    29.508] (II) Unloading radeon
[    29.540] (II) UnloadModule: "modesetting"
[    29.540] (II) Unloading modesetting
[    29.540] (II) UnloadModule: "fbdev"
[    29.540] (II) Unloading fbdev
[    29.540] (II) UnloadSubModule: "fbdevhw"
[    29.540] (II) Unloading fbdevhw
[    29.540] (II) UnloadModule: "vesa"
[    29.541] (II) Unloading vesa
[    29.541] (--) Depth 24 pixmap format is 32 bpp
[    29.541] Loading extension ATIFGLRXDRI
[    29.541] (II) fglrx(0): doing swlDriScreenInit
[    29.541] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    29.541] ukiDynamicMajor: found major device number 250
[    29.541] ukiDynamicMajor: found major device number 250
[    29.541] ukiDynamicMajor: found major device number 250
[    29.541] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.541] ukiOpenDevice: node name is /dev/ati/card0
[    29.541] ukiOpenDevice: open result is 12, (OK)
[    29.541] ukiOpenByBusid: ukiOpenMinor returns 12
[    29.541] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.541] (II) fglrx(0): [uki] DRM interface version 1.0
[    29.541] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    29.541] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    29.541] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7fc77b042000
[    29.541] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    29.541] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    29.541] (II) fglrx(0): swlDriScreenInit done
[    29.541] (II) fglrx(0): Kernel Module Version Information:
[    29.541] (II) fglrx(0):     Name: fglrx
[    29.541] (II) fglrx(0):     Version: 13.35.5
[    29.541] (II) fglrx(0):     Date: Mar 12 2014
[    29.541] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    29.541] (II) fglrx(0): Kernel Module version matches driver.
[    29.541] (II) fglrx(0): Kernel Module Build Time Information:
[    29.541] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.13.0-37-generic
[    29.541] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    29.541] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    29.541] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    29.541] (II) fglrx(0): [uki] register handle = 0x00004000
[    29.542] (II) fglrx(0): DRI initialization successfull
[    29.542] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    29.542] (==) fglrx(0): Backing store enabled
[    29.542] Loading extension FGLRXEXTENSION
[    29.542] (==) fglrx(0): DPMS enabled
[    29.542] (II) fglrx(0): Initialized in-driver Xinerama extension
[    29.542] (**) fglrx(0): Textured Video is enabled.
[    29.542] (II) LoadModule: "glesx"
[    29.542] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    29.543] (II) Module glesx: vendor="X.Org Foundation"
[    29.543]     compiled for 1.4.99.906, module version = 1.0.0
[    29.543] Loading extension GLESX
[    29.543] (II) fglrx(0): GLESX enableFlags = 8784
[    29.543] (II) fglrx(0): GLESX is enabled
[    29.543] (II) LoadModule: "amdxmm"
[    29.543] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    29.543] (II) Module amdxmm: vendor="X.Org Foundation"
[    29.543]     compiled for 1.4.99.906, module version = 2.0.0
[    29.567] Loading extension AMDXVOPL
[    29.567] Loading extension AMDXVBA
[    29.628] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    29.630] (II) fglrx(0): Enable composite support successfully
[    29.630] (II) fglrx(0): X context handle = 0x1
[    29.630] (II) fglrx(0): [DRI] installation complete
[    29.630] (==) fglrx(0): Silken mouse enabled
[    29.630] (==) fglrx(0): Using HW cursor of display infrastructure!
[    29.630] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.679] (--) RandR disabled
[    29.684] (II) SELinux: Disabled on system
[    29.685] ukiDynamicMajor: found major device number 250
[    29.685] ukiDynamicMajor: found major device number 250
[    29.685] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.685] ukiOpenDevice: node name is /dev/ati/card0
[    29.685] ukiOpenDevice: open result is 13, (OK)
[    29.685] ukiOpenByBusid: ukiOpenMinor returns 13
[    29.685] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.685] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    29.685] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    29.685] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    29.709] ukiDynamicMajor: found major device number 250
[    29.709] ukiDynamicMajor: found major device number 250
[    29.709] ukiDynamicMajor: found major device number 250
[    29.709] ukiOpenDevice: node name is /dev/ati/card0
[    29.709] ukiOpenDevice: open result is 14, (OK)
[    29.709] ukiGetBusid returned 'PCI:1:0:0'
[    29.709] ukiOpenDevice: node name is /dev/ati/card1
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card2
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card3
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card4
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card5
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card6
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card7
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card8
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card9
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card10
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card11
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card12
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: open result is -1, (No such device)
[    29.709] ukiOpenDevice: Open failed
[    29.709] ukiOpenDevice: node name is /dev/ati/card13
[    29.710] ukiOpenDevice: open result is -1, (No such device)
[    29.710] ukiOpenDevice: open result is -1, (No such device)
[    29.710] ukiOpenDevice: Open failed
[    29.710] ukiOpenDevice: node name is /dev/ati/card14
[    29.710] ukiOpenDevice: open result is -1, (No such device)
[    29.710] ukiOpenDevice: open result is -1, (No such device)
[    29.710] ukiOpenDevice: Open failed
[    29.710] ukiOpenDevice: node name is /dev/ati/card15
[    29.710] ukiOpenDevice: open result is -1, (No such device)
[    29.710] ukiOpenDevice: open result is -1, (No such device)
[    29.710] ukiOpenDevice: Open failed
[    29.710] ukiDynamicMajor: found major device number 250
[    29.710] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.710] ukiOpenDevice: node name is /dev/ati/card0
[    29.710] ukiOpenDevice: open result is 14, (OK)
[    29.710] ukiOpenByBusid: ukiOpenMinor returns 14
[    29.710] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.745] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    29.745] ukiDynamicMajor: found major device number 250
[    29.745] ukiDynamicMajor: found major device number 250
[    29.745] ukiDynamicMajor: found major device number 250
[    29.745] ukiOpenDevice: node name is /dev/ati/card0
[    29.745] ukiOpenDevice: open result is 15, (OK)
[    29.745] ukiGetBusid returned 'PCI:1:0:0'
[    29.746] ukiOpenDevice: node name is /dev/ati/card1
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card2
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card3
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card4
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card5
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card6
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card7
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card8
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card9
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card10
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card11
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card12
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card13
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card14
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiOpenDevice: node name is /dev/ati/card15
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: open result is -1, (No such device)
[    29.746] ukiOpenDevice: Open failed
[    29.746] ukiDynamicMajor: found major device number 250
[    29.746] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.746] ukiOpenDevice: node name is /dev/ati/card0
[    29.746] ukiOpenDevice: open result is 15, (OK)
[    29.746] ukiOpenByBusid: ukiOpenMinor returns 15
[    29.746] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.755] (II) fglrx(0): OverDrive5 Detected!
[    29.759] (II) fglrx(0): Setting screen physical size to 508 x 285
[    29.766] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.769] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.769] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.769] (II) LoadModule: "evdev"
[    29.769] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.795] (II) Module evdev: vendor="X.Org Foundation"
[    29.795]     compiled for 1.15.0, module version = 2.8.2
[    29.795]     Module class: X.Org XInput Driver
[    29.795]     ABI class: X.Org XInput driver, version 20.0
[    29.795] (II) Using input driver 'evdev' for 'Power Button'
[    29.795] (**) Power Button: always reports core events
[    29.795] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.795] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.795] (--) evdev: Power Button: Found keys
[    29.795] (II) evdev: Power Button: Configuring as keyboard
[    29.795] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.796] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.796] (**) Option "xkb_rules" "evdev"
[    29.796] (**) Option "xkb_model" "pc105"
[    29.796] (**) Option "xkb_layout" "us"
[    29.796] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.796] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.796] (II) Using input driver 'evdev' for 'Power Button'
[    29.796] (**) Power Button: always reports core events
[    29.796] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.796] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.796] (--) evdev: Power Button: Found keys
[    29.796] (II) evdev: Power Button: Configuring as keyboard
[    29.796] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    29.796] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.796] (**) Option "xkb_rules" "evdev"
[    29.796] (**) Option "xkb_model" "pc105"
[    29.796] (**) Option "xkb_layout" "us"
[    29.797] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[    29.797] (II) No input driver specified, ignoring this device.
[    29.797] (II) This device may have been added with another device file.
[    29.797] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:402d (/dev/input/event2)
[    29.797] (**) Logitech Unifying Device. Wireless PID:402d: Applying InputClass "evdev pointer catchall"
[    29.797] (**) Logitech Unifying Device. Wireless PID:402d: Applying InputClass "evdev keyboard catchall"
[    29.797] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:402d'
[    29.797] (**) Logitech Unifying Device. Wireless PID:402d: always reports core events
[    29.797] (**) evdev: Logitech Unifying Device. Wireless PID:402d: Device: "/dev/input/event2"
[    29.797] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Vendor 0x46d Product 0xc52b
[    29.797] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found 20 mouse buttons
[    29.797] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found scroll wheel(s)
[    29.797] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found relative axes
[    29.797] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found x and y relative axes
[    29.797] (--) evdev: Logitech Unifying Device. Wireless PID:402d: Found keys
[    29.797] (II) evdev: Logitech Unifying Device. Wireless PID:402d: Configuring as mouse
[    29.797] (II) evdev: Logitech Unifying Device. Wireless PID:402d: Configuring as keyboard
[    29.797] (II) evdev: Logitech Unifying Device. Wireless PID:402d: Adding scrollwheel support
[    29.797] (**) evdev: Logitech Unifying Device. Wireless PID:402d: YAxisMapping: buttons 4 and 5
[    29.797] (**) evdev: Logitech Unifying Device. Wireless PID:402d: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.797] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb6/6-1/6-1:1.2/0003:046D:C52B.0003/input/input6/event2"
[    29.797] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:402d" (type: KEYBOARD, id 8)
[    29.797] (**) Option "xkb_rules" "evdev"
[    29.797] (**) Option "xkb_model" "pc105"
[    29.797] (**) Option "xkb_layout" "us"
[    29.797] (II) evdev: Logitech Unifying Device. Wireless PID:402d: initialized for relative axes.
[    29.798] (**) Logitech Unifying Device. Wireless PID:402d: (accel) keeping acceleration scheme 1
[    29.798] (**) Logitech Unifying Device. Wireless PID:402d: (accel) acceleration profile 0
[    29.798] (**) Logitech Unifying Device. Wireless PID:402d: (accel) acceleration factor: 2.000
[    29.798] (**) Logitech Unifying Device. Wireless PID:402d: (accel) acceleration threshold: 4
[    29.798] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:402d (/dev/input/mouse0)
[    29.798] (II) No input driver specified, ignoring this device.
[    29.798] (II) This device may have been added with another device file.
[    29.798] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event3)
[    29.798] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[    29.798] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[    29.798] (**) USB USB Keykoard: always reports core events
[    29.798] (**) evdev: USB USB Keykoard: Device: "/dev/input/event3"
[    29.798] (--) evdev: USB USB Keykoard: Vendor 0x1a2c Product 0x21
[    29.798] (--) evdev: USB USB Keykoard: Found keys
[    29.798] (II) evdev: USB USB Keykoard: Configuring as keyboard
[    29.798] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-5/3-5:1.0/input/input7/event3"
[    29.798] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 9)
[    29.798] (**) Option "xkb_rules" "evdev"
[    29.798] (**) Option "xkb_model" "pc105"
[    29.798] (**) Option "xkb_layout" "us"
[    29.799] (II) config/udev: Adding input device USB USB Keykoard (/dev/input/event4)
[    29.799] (**) USB USB Keykoard: Applying InputClass "evdev keyboard catchall"
[    29.799] (II) Using input driver 'evdev' for 'USB USB Keykoard'
[    29.799] (**) USB USB Keykoard: always reports core events
[    29.799] (**) evdev: USB USB Keykoard: Device: "/dev/input/event4"
[    29.799] (--) evdev: USB USB Keykoard: Vendor 0x1a2c Product 0x21
[    29.799] (--) evdev: USB USB Keykoard: Found 1 mouse buttons
[    29.799] (--) evdev: USB USB Keykoard: Found scroll wheel(s)
[    29.799] (--) evdev: USB USB Keykoard: Found relative axes
[    29.799] (II) evdev: USB USB Keykoard: Forcing relative x/y axes to exist.
[    29.799] (--) evdev: USB USB Keykoard: Found absolute axes
[    29.799] (II) evdev: USB USB Keykoard: Forcing absolute x/y axes to exist.
[    29.799] (--) evdev: USB USB Keykoard: Found keys
[    29.799] (II) evdev: USB USB Keykoard: Configuring as mouse
[    29.799] (II) evdev: USB USB Keykoard: Configuring as keyboard
[    29.799] (II) evdev: USB USB Keykoard: Adding scrollwheel support
[    29.799] (**) evdev: USB USB Keykoard: YAxisMapping: buttons 4 and 5
[    29.799] (**) evdev: USB USB Keykoard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.799] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-5/3-5:1.1/input/input8/event4"
[    29.799] (II) XINPUT: Adding extended input device "USB USB Keykoard" (type: KEYBOARD, id 10)
[    29.799] (**) Option "xkb_rules" "evdev"
[    29.799] (**) Option "xkb_model" "pc105"
[    29.799] (**) Option "xkb_layout" "us"
[    29.799] (II) evdev: USB USB Keykoard: initialized for relative axes.
[    29.799] (WW) evdev: USB USB Keykoard: ignoring absolute axes.
[    29.799] (**) USB USB Keykoard: (accel) keeping acceleration scheme 1
[    29.799] (**) USB USB Keykoard: (accel) acceleration profile 0
[    29.799] (**) USB USB Keykoard: (accel) acceleration factor: 2.000
[    29.799] (**) USB USB Keykoard: (accel) acceleration threshold: 4
[    29.799] (II) config/udev: Adding input device UVC Camera (046d:0990) (/dev/input/event14)
[    29.799] (**) UVC Camera (046d:0990): Applying InputClass "evdev keyboard catchall"
[    29.800] (II) Using input driver 'evdev' for 'UVC Camera (046d:0990)'
[    29.800] (**) UVC Camera (046d:0990): always reports core events
[    29.800] (**) evdev: UVC Camera (046d:0990): Device: "/dev/input/event14"
[    29.800] (--) evdev: UVC Camera (046d:0990): Vendor 0x46d Product 0x990
[    29.800] (--) evdev: UVC Camera (046d:0990): Found keys
[    29.800] (II) evdev: UVC Camera (046d:0990): Configuring as keyboard
[    29.800] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/input/input18/event14"
[    29.800] (II) XINPUT: Adding extended input device "UVC Camera (046d:0990)" (type: KEYBOARD, id 11)
[    29.800] (**) Option "xkb_rules" "evdev"
[    29.800] (**) Option "xkb_model" "pc105"
[    29.800] (**) Option "xkb_layout" "us"
[    29.800] (II) config/udev: Adding input device HD-Audio Generic Rear Mic (/dev/input/event11)
[    29.800] (II) No input driver specified, ignoring this device.
[    29.800] (II) This device may have been added with another device file.
[    29.800] (II) config/udev: Adding input device HD-Audio Generic Line (/dev/input/event10)
[    29.800] (II) No input driver specified, ignoring this device.
[    29.800] (II) This device may have been added with another device file.
[    29.800] (II) config/udev: Adding input device HD-Audio Generic Speaker Front (/dev/input/event9)
[    29.800] (II) No input driver specified, ignoring this device.
[    29.800] (II) This device may have been added with another device file.
[    29.801] (II) config/udev: Adding input device HD-Audio Generic Speaker Surround (/dev/input/event8)
[    29.801] (II) No input driver specified, ignoring this device.
[    29.801] (II) This device may have been added with another device file.
[    29.801] (II) config/udev: Adding input device HD-Audio Generic Speaker CLFE (/dev/input/event7)
[    29.801] (II) No input driver specified, ignoring this device.
[    29.801] (II) This device may have been added with another device file.
[    29.801] (II) config/udev: Adding input device HD-Audio Generic Speaker Side (/dev/input/event6)
[    29.801] (II) No input driver specified, ignoring this device.
[    29.801] (II) This device may have been added with another device file.
[    29.801] (II) config/udev: Adding input device HD-Audio Generic Front Headphone (/dev/input/event5)
[    29.801] (II) No input driver specified, ignoring this device.
[    29.801] (II) This device may have been added with another device file.
[    29.801] (II) config/udev: Adding input device HD-Audio Generic Front Mic (/dev/input/event12)
[    29.801] (II) No input driver specified, ignoring this device.
[    29.801] (II) This device may have been added with another device file.
[    29.806] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    31.538] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    31.575] (II) fglrx(0): Using EDID range info for horizontal sync
[    31.575] (II) fglrx(0): Using EDID range info for vertical refresh
[    31.575] (II) fglrx(0): Printing DDC gathered Modelines:
[    31.575] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    31.575] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    31.575] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    31.575] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    31.575] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    31.575] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    31.575] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    31.575] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    31.575] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    31.575] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    31.575] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    31.575] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    38.795] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    38.795] (II) fglrx(0): Using hsync ranges from config file
[    38.795] (II) fglrx(0): Using vrefresh ranges from config file
[    38.795] (II) fglrx(0): Printing DDC gathered Modelines:
[    38.795] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    38.795] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    38.795] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    38.795] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    38.795] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    38.795] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    38.795] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    38.795] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    38.795] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    38.795] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    38.795] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    38.795] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    39.162] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.200] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    39.200] (II) fglrx(0): Using hsync ranges from config file
[    39.200] (II) fglrx(0): Using vrefresh ranges from config file
[    39.200] (II) fglrx(0): Printing DDC gathered Modelines:
[    39.200] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    39.200] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    39.200] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    39.200] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    39.200] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    39.200] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    39.200] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    39.200] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    39.200] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    39.200] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    39.200] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    39.200] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    39.679] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.874] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.878] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    39.878] (II) fglrx(0): Using hsync ranges from config file
[    39.878] (II) fglrx(0): Using vrefresh ranges from config file
[    39.878] (II) fglrx(0): Printing DDC gathered Modelines:
[    39.878] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    39.878] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    39.878] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    39.878] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    39.878] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    39.878] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    39.878] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    39.878] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    39.878] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    39.878] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    39.878] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    39.878] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    40.854] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    40.854] (II) fglrx(0): Using hsync ranges from config file
[    40.854] (II) fglrx(0): Using vrefresh ranges from config file
[    40.854] (II) fglrx(0): Printing DDC gathered Modelines:
[    40.854] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    40.854] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.854] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    40.854] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.854] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.854] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    40.854] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    40.854] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.854] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    40.854] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.854] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.854] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    40.975] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    40.976] (II) fglrx(0): Using hsync ranges from config file
[    40.976] (II) fglrx(0): Using vrefresh ranges from config file
[    40.976] (II) fglrx(0): Printing DDC gathered Modelines:
[    40.976] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    40.976] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.976] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    40.976] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.976] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.976] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    40.976] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    40.976] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.976] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    40.976] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.976] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.976] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    43.814] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    57.883] (II) fglrx(0): EDID vendor "DEL", prod id 53322
[    57.883] (II) fglrx(0): Using hsync ranges from config file
[    57.883] (II) fglrx(0): Using vrefresh ranges from config file
[    57.883] (II) fglrx(0): Printing DDC gathered Modelines:
[    57.883] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    57.883] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    57.883] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    57.883] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    57.883] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    57.883] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    57.883] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    57.883] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    57.883] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    57.883] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    57.883] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    57.883] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
```

---

### Post by tgalati4 on 2014-10-18
Let's try again.  Remove the previous log file from the previous post:

```
grep EE /var/log/Xorg.0.log
```

and 

```
grep WW /var/log/Xorg.0.log
```

---

### Post by Senaka_Amarakoon on 2015-01-15
i had the similar problem with a duel core processor, i also changed the graphics card but nothing happend. But when i replaced the RAM with a new RAM the issue was solved, hope this works for you

---

