---
title: "Screen, Resolution? problems (horizontal lines) [Ubuntu 14.04]"
date: 2015-10-16
forum: Hardware
---

### Post by DRTorrontegi on 2015-10-16
Hello,

I want to move my htpc from windows 7 to linux, and i have selected ubuntu 14.04.03 for do it, because i want to install Kody(aka xbmc)

My first step is to try Ubuntu on a dvd, and i identify my first problem, i don't know how to describe it, is like horizontal lines, it looks blur.

I have attached a picture in order to show the problem.

I have a Athlon II X2 240 + Ati Radeon HD 4200 + Philips TV Full HD, 2 HDD + 1 SSD ( i want to install linux on it)


[ATTACH=CONFIG]264979[/ATTACH]

---

### Post by DRTorrontegi on 2015-10-16
Any ideas? up!

---

### Post by blm-ubunet on 2015-10-16
So the TV is the monitor here ?
Connected with what cable?
Contents (as attachment) of /var/log/Xorg.0.log please..

---

### Post by DRTorrontegi on 2015-10-17
Hello,

The TV is connected by hdmi with an AV between tv and pc.

TV --(hdmi)-->AV-->(hdmi)-->PC

ASAP i will attach the infor of the log

Regards

---

### Post by blm-ubunet on 2015-10-17
FYI
When you run Ubuntu from the Live CD or DVD the video driver is always open source.
For the AMD/Ati h/w this is radeon which is actually very good, better than the AMD closed blob driver (fglx) except for the latest GPU h/w.
The radeon driver has video decode in h/w using VDPAU & supports HDMI & HDA over HDMI.
The AMD driver has to use VA-API & is not as complete.
So do not be tempted to install the proprietary AMD driver unless as a last resort..

Add the output of  "xrandr" to your next post as well.

AVRs/HT-amps can cause problems with messing up ELD/EDID information from the display.

Your video h/w is known as R600 (AFIAU)
[http://xorg.freedesktop.org/wiki/RadeonFeature/#index1h2](http://xorg.freedesktop.org/wiki/RadeonFeature/#index1h2)

---

### Post by DRTorrontegi on 2015-10-19
Thanks  blm-ubunet i will check it afeter install ubuntu, it could be possible that the problem is caused because i'm using a live cd instead of a standard installation.

Regards

---

### Post by DRTorrontegi on 2015-10-20
Hello

I cant upload the xorg.0.log the webs tell me that is too big... so i will copy paste here, snd the xrandr out too.

When i change the display resolution to 1300x768 19x9 the horizontal lines doesnt appear buy the screen doesnt fit all the tv, a black frame appear

thanks 

///////// xrandr /////////

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 1280mm x 720mm
   1920x1080i     50.0*+   60.1     60.0  
   1920x1080      60.0     50.0     59.9     30.0     25.0     24.0     30.0     24.0  
   1600x1200      60.0  
   2880x576       50.0  
   2880x576i      50.1  
   2880x480       60.0     59.9  
   2880x480i      60.1     60.1  
   1280x1024      60.0  
   1360x768       59.8  
   1280x720       60.0     50.0     59.9  
   1440x576       50.0  
   1024x768       60.0  
   1440x480       60.0     59.9  
   800x600        60.3  
   720x576        50.0  
   720x576i       50.1  
   720x480        60.0     59.9  
   720x480i       60.1     60.1  
   640x480        60.0     59.9  


//////// xorg.0.log /////////////////

[     7.432] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     7.432] X Protocol Version 11, Revision 0
[     7.432] Build Operating System: Linux 3.2.0-77-generic x86_64 Ubuntu
[     7.432] Current Operating System: Linux htpc-lnx 3.19.0-30-generic #34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015 x86_64
[     7.432] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-30-generic root=UUID=219e7d64-e3ca-405e-881a-20b143513968 ro quiet splash vt.handoff=7
[     7.432] Build Date: 13 May 2015  04:35:05AM
[     7.432] xorg-server 2:1.17.1-0ubuntu3~trusty1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     7.432] Current version of pixman: 0.30.2
[     7.432]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     7.432] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.432] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 20 14:14:15 2015
[     7.434] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.435] (==) No Layout section.  Using the first Screen section.
[     7.435] (==) No screen section available. Using defaults.
[     7.435] (**) |-->Screen "Default Screen Section" (0)
[     7.435] (**) |   |-->Monitor "<default monitor>"
[     7.435] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     7.435] (==) Automatically adding devices
[     7.435] (==) Automatically enabling devices
[     7.435] (==) Automatically adding GPU devices
[     7.438] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.438]     Entry deleted from font path.
[     7.438] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.438]     Entry deleted from font path.
[     7.438] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.438]     Entry deleted from font path.
[     7.438] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.438]     Entry deleted from font path.
[     7.438] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.438]     Entry deleted from font path.
[     7.438] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     7.438] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     7.438] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.438] (II) Loader magic: 0x7f9e7a417c60
[     7.438] (II) Module ABI versions:
[     7.438]     X.Org ANSI C Emulation: 0.4
[     7.438]     X.Org Video Driver: 19.0
[     7.438]     X.Org XInput driver : 21.0
[     7.438]     X.Org Server Extension : 9.0
[     7.438] (II) xfree86: Adding drm device (/dev/dri/card0)
[     7.439] (--) PCI:*(0:1:5:0) 1002:9710:1458:d000 rev 0, Mem @ 0xd0000000/268435456, 0xfdfe0000/65536, 0xfde00000/1048576, I/O @ 0x0000ee00/256
[     7.440] (II) LoadModule: "glx"
[     7.441] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     7.453] (II) Module glx: vendor="X.Org Foundation"
[     7.453]     compiled for 1.17.1, module version = 1.0.0
[     7.453]     ABI class: X.Org Server Extension, version 9.0
[     7.453] (==) AIGLX enabled
[     7.453] (==) Matched fglrx as autoconfigured driver 0
[     7.453] (==) Matched ati as autoconfigured driver 1
[     7.453] (==) Matched fglrx as autoconfigured driver 2
[     7.453] (==) Matched ati as autoconfigured driver 3
[     7.453] (==) Matched modesetting as autoconfigured driver 4
[     7.453] (==) Matched fbdev as autoconfigured driver 5
[     7.453] (==) Matched vesa as autoconfigured driver 6
[     7.453] (==) Assigned the driver to the xf86ConfigLayout
[     7.453] (II) LoadModule: "fglrx"
[     7.454] (WW) Warning, couldn't open module fglrx
[     7.454] (II) UnloadModule: "fglrx"
[     7.454] (II) Unloading fglrx
[     7.454] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     7.454] (II) LoadModule: "ati"
[     7.454] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     7.454] (II) Module ati: vendor="X.Org Foundation"
[     7.454]     compiled for 1.17.1, module version = 7.5.0
[     7.454]     Module class: X.Org Video Driver
[     7.454]     ABI class: X.Org Video Driver, version 19.0
[     7.454] (II) LoadModule: "radeon"
[     7.454] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     7.458] (II) Module radeon: vendor="X.Org Foundation"
[     7.458]     compiled for 1.17.1, module version = 7.5.0
[     7.458]     Module class: X.Org Video Driver
[     7.458]     ABI class: X.Org Video Driver, version 19.0
[     7.458] (II) LoadModule: "modesetting"
[     7.458] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     7.459] (II) Module modesetting: vendor="X.Org Foundation"
[     7.459]     compiled for 1.17.1, module version = 1.17.1
[     7.459]     Module class: X.Org Video Driver
[     7.459]     ABI class: X.Org Video Driver, version 19.0
[     7.459] (II) LoadModule: "fbdev"
[     7.459] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.460] (II) Module fbdev: vendor="X.Org Foundation"
[     7.460]     compiled for 1.17.1, module version = 0.4.4
[     7.460]     Module class: X.Org Video Driver
[     7.460]     ABI class: X.Org Video Driver, version 19.0
[     7.460] (II) LoadModule: "vesa"
[     7.460] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.460] (II) Module vesa: vendor="X.Org Foundation"
[     7.460]     compiled for 1.17.1, module version = 2.3.3
[     7.460]     Module class: X.Org Video Driver
[     7.460]     ABI class: X.Org Video Driver, version 19.0
[     7.460] (==) Matched fglrx as autoconfigured driver 0
[     7.460] (==) Matched ati as autoconfigured driver 1
[     7.460] (==) Matched fglrx as autoconfigured driver 2
[     7.460] (==) Matched ati as autoconfigured driver 3
[     7.460] (==) Matched modesetting as autoconfigured driver 4
[     7.460] (==) Matched fbdev as autoconfigured driver 5
[     7.460] (==) Matched vesa as autoconfigured driver 6
[     7.460] (==) Assigned the driver to the xf86ConfigLayout
[     7.460] (II) LoadModule: "fglrx"
[     7.461] (WW) Warning, couldn't open module fglrx
[     7.461] (II) UnloadModule: "fglrx"
[     7.461] (II) Unloading fglrx
[     7.461] (EE) Failed to load module "fglrx" (module does not exist, 0)
[     7.461] (II) LoadModule: "ati"
[     7.461] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     7.461] (II) Module ati: vendor="X.Org Foundation"
[     7.461]     compiled for 1.17.1, module version = 7.5.0
[     7.461]     Module class: X.Org Video Driver
[     7.461]     ABI class: X.Org Video Driver, version 19.0
[     7.461] (II) LoadModule: "modesetting"
[     7.461] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     7.461] (II) Module modesetting: vendor="X.Org Foundation"
[     7.461]     compiled for 1.17.1, module version = 1.17.1
[     7.461]     Module class: X.Org Video Driver
[     7.461]     ABI class: X.Org Video Driver, version 19.0
[     7.461] (II) UnloadModule: "modesetting"
[     7.461] (II) Unloading modesetting
[     7.461] (II) Failed to load module "modesetting" (already loaded, 0)
[     7.461] (II) LoadModule: "fbdev"
[     7.461] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.461] (II) Module fbdev: vendor="X.Org Foundation"
[     7.461]     compiled for 1.17.1, module version = 0.4.4
[     7.461]     Module class: X.Org Video Driver
[     7.461]     ABI class: X.Org Video Driver, version 19.0
[     7.461] (II) UnloadModule: "fbdev"
[     7.461] (II) Unloading fbdev
[     7.461] (II) Failed to load module "fbdev" (already loaded, 0)
[     7.461] (II) LoadModule: "vesa"
[     7.461] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.461] (II) Module vesa: vendor="X.Org Foundation"
[     7.461]     compiled for 1.17.1, module version = 2.3.3
[     7.461]     Module class: X.Org Video Driver
[     7.461]     ABI class: X.Org Video Driver, version 19.0
[     7.461] (II) UnloadModule: "vesa"
[     7.461] (II) Unloading vesa
[     7.461] (II) Failed to load module "vesa" (already loaded, 0)
[     7.461] (II) RADEON: Driver for ATI Radeon chipsets:
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
    VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[     7.465] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     7.465] (II) FBDEV: driver for framebuffer: fbdev
[     7.465] (II) VESA: driver for VESA chipsets: vesa
[     7.465] (++) using VT number 7

[     7.466] (II) [KMS] Kernel modesetting enabled.
[     7.466] (WW) Falling back to old probe method for modesetting
[     7.466] (WW) Falling back to old probe method for fbdev
[     7.466] (II) Loading sub module "fbdevhw"
[     7.466] (II) LoadModule: "fbdevhw"
[     7.466] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     7.467] (II) Module fbdevhw: vendor="X.Org Foundation"
[     7.467]     compiled for 1.17.1, module version = 0.0.2
[     7.467]     ABI class: X.Org Video Driver, version 19.0
[     7.467] (WW) Falling back to old probe method for vesa
[     7.467] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     7.467] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[     7.467] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     7.467] (==) RADEON(0): Default visual is TrueColor
[     7.467] (==) RADEON(0): RGB weight 888
[     7.467] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[     7.467] (--) RADEON(0): Chipset: "ATI Radeon HD 4200" (ChipID = 0x9710)
[     7.467] (II) Loading sub module "dri2"
[     7.467] (II) LoadModule: "dri2"
[     7.467] (II) Module "dri2" already built-in
[     7.467] (II) Loading sub module "exa"
[     7.467] (II) LoadModule: "exa"
[     7.467] (II) Loading /usr/lib/xorg/modules/libexa.so
[     7.468] (II) Module exa: vendor="X.Org Foundation"
[     7.468]     compiled for 1.17.1, module version = 2.6.0
[     7.468]     ABI class: X.Org Video Driver, version 19.0
[     7.468] (II) RADEON(0): KMS Color Tiling: enabled
[     7.468] (II) RADEON(0): KMS Color Tiling 2D: enabled
[     7.468] (II) RADEON(0): KMS Pageflipping: enabled
[     7.468] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[     7.492] (II) RADEON(0): Output VGA-0 has no monitor section
[     7.552] (II) RADEON(0): Output HDMI-0 has no monitor section
[     7.576] (II) RADEON(0): EDID for output VGA-0
[     7.638] (II) RADEON(0): EDID for output HDMI-0
[     7.638] (II) RADEON(0): Manufacturer: PHL  Model: 0  Serial#: 16843009
[     7.638] (II) RADEON(0): Year: 2009  Week: 8
[     7.638] (II) RADEON(0): EDID Version: 1.3
[     7.638] (II) RADEON(0): Digital Display Input
[     7.638] (II) RADEON(0): Max Image Size [cm]: horiz.: 128  vert.: 72
[     7.638] (II) RADEON(0): Gamma: 2.20
[     7.638] (II) RADEON(0): No DPMS capabilities specified
[     7.638] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     7.638] (II) RADEON(0): First detailed timing is preferred mode
[     7.638] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.290 greenY: 0.600
[     7.638] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.289 whiteY: 0.299
[     7.638] (II) RADEON(0): Supported established timings:
[     7.638] (II) RADEON(0): 640x480@60Hz
[     7.638] (II) RADEON(0): 800x600@60Hz
[     7.638] (II) RADEON(0): 1024x768@60Hz
[     7.638] (II) RADEON(0): Manufacturer's mask: 0
[     7.638] (II) RADEON(0): Supported standard timings:
[     7.638] (II) RADEON(0): #0: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[     7.638] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     7.638] (II) RADEON(0): #2: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[     7.638] (II) RADEON(0): Supported detailed timing:
[     7.638] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     7.638] (II) RADEON(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[     7.638] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     7.638] (II) RADEON(0): Supported detailed timing:
[     7.638] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     7.638] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     7.638] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     7.638] (II) RADEON(0): Monitor name: Philips FTV
[     7.638] (II) RADEON(0): Ranges: V min: 48 V max: 62 Hz, H min: 15 H max: 70 kHz, PixClock max 155 MHz
[     7.638] (II) RADEON(0): Supported detailed timing:
[     7.638] (II) RADEON(0): clock: 74.2 MHz   Image Size:  1280 x 720 mm
[     7.638] (II) RADEON(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[     7.638] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     7.638] (II) RADEON(0): Supported detailed timing:
[     7.638] (II) RADEON(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
[     7.638] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     7.638] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     7.638] (II) RADEON(0): Number of EDID sections to follow: 1
[     7.638] (II) RADEON(0): EDID (in hex):
[     7.638] (II) RADEON(0):     00ffffffffffff00410c000001010101
[     7.638] (II) RADEON(0):     08130103808048780ae692a3544a9926
[     7.638] (II) RADEON(0):     0f4a4c2108008bc08180a94001010101
[     7.638] (II) RADEON(0):     010101010101011d80d0721c1620102c
[     7.638] (II) RADEON(0):     258000d05200009e011d8018711c1620
[     7.638] (II) RADEON(0):     582c250000d05200009e000000fc0050
[     7.638] (II) RADEON(0):     68696c697073204654560a20000000fd
[     7.638] (II) RADEON(0):     00303e0f460f000a20202020202001e9
[     7.638] (II) RADEON(0):     02034af45e1f10202122140513041203
[     7.638] (II) RADEON(0):     110216071506010e0f1d1e0a0b191a23
[     7.638] (II) RADEON(0):     24252635097f070f7f071507503e1fc0
[     7.638] (II) RADEON(0):     5706006754005f5401834f000068030c
[     7.638] (II) RADEON(0):     001100b82d00e3050301011d00bc52d0
[     7.638] (II) RADEON(0):     1e20b828554000d05200001e011d0072
[     7.638] (II) RADEON(0):     51d01e206e285500c48e2100001e0000
[     7.638] (II) RADEON(0):     000000000000000000000000000000d7
[     7.638] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[     7.638] (II) RADEON(0): Printing probed modes for output HDMI-0
[     7.638] (II) RADEON(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x30.0   74.18  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.7 kHz e)
[     7.638] (II) RADEON(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     7.638] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[     7.638] (II) RADEON(0): Modeline "2880x576"x50.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     7.638] (II) RADEON(0): Modeline "2880x576i"x50.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     7.638] (II) RADEON(0): Modeline "2880x480"x60.0  108.11  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.638] (II) RADEON(0): Modeline "2880x480"x59.9  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.638] (II) RADEON(0): Modeline "2880x480i"x60.0   54.05  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.8 kHz e)
[     7.638] (II) RADEON(0): Modeline "2880x480i"x59.9   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     7.638] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     7.638] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[     7.638] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     7.638] (II) RADEON(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     7.638] (II) RADEON(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     7.638] (II) RADEON(0): Modeline "1440x576"x50.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     7.638] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     7.638] (II) RADEON(0): Modeline "1440x480"x60.0   54.05  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.638] (II) RADEON(0): Modeline "1440x480"x59.9   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.638] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     7.638] (II) RADEON(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     7.638] (II) RADEON(0): Modeline "720x576i"x50.0   13.50  720 732 795 864  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     7.638] (II) RADEON(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.639] (II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     7.639] (II) RADEON(0): Modeline "720x480i"x60.0   13.51  720 739 801 858  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     7.639] (II) RADEON(0): Modeline "720x480i"x59.9   13.50  720 739 801 858  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     7.639] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.639] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     7.639] (II) RADEON(0): Output VGA-0 disconnected
[     7.639] (II) RADEON(0): Output HDMI-0 connected
[     7.639] (II) RADEON(0): Using exact sizes for initial modes
[     7.639] (II) RADEON(0): Output HDMI-0 using initial mode 1920x1080i
[     7.639] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     7.639] (II) RADEON(0): mem size init: gart size :1fdee000 vram size: s:20000000 visible:1f4be000
[     7.639] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[     7.639] (==) RADEON(0): DPI set to (96, 96)
[     7.639] (II) Loading sub module "fb"
[     7.639] (II) LoadModule: "fb"
[     7.639] (II) Loading /usr/lib/xorg/modules/libfb.so
[     7.640] (II) Module fb: vendor="X.Org Foundation"
[     7.640]     compiled for 1.17.1, module version = 1.0.0
[     7.640]     ABI class: X.Org ANSI C Emulation, version 0.4
[     7.640] (II) Loading sub module "ramdac"
[     7.640] (II) LoadModule: "ramdac"
[     7.640] (II) Module "ramdac" already built-in
[     7.640] (II) UnloadModule: "modesetting"
[     7.640] (II) Unloading modesetting
[     7.640] (II) UnloadModule: "fbdev"
[     7.640] (II) Unloading fbdev
[     7.640] (II) UnloadSubModule: "fbdevhw"
[     7.640] (II) Unloading fbdevhw
[     7.640] (II) UnloadModule: "vesa"
[     7.640] (II) Unloading vesa
[     7.640] (--) Depth 24 pixmap format is 32 bpp
[     7.641] (II) RADEON(0): [DRI2] Setup complete
[     7.641] (II) RADEON(0): [DRI2]   DRI driver: r600
[     7.641] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[     7.641] (II) RADEON(0): Front buffer size: 8100K
[     7.641] (II) RADEON(0): VRAM usage limit set to 454165K
[     7.642] (==) RADEON(0): Backing store enabled
[     7.642] (II) RADEON(0): Direct rendering enabled
[     7.642] (II) EXA(0): Driver allocated offscreen pixmaps
[     7.642] (II) EXA(0): Driver registered support for the following operations:
[     7.642] (II)         Solid
[     7.642] (II)         Copy
[     7.642] (II)         Composite (RENDER acceleration)
[     7.642] (II)         UploadToScreen
[     7.642] (II)         DownloadFromScreen
[     7.642] (II) RADEON(0): Acceleration enabled
[     7.642] (==) RADEON(0): DPMS enabled
[     7.642] (==) RADEON(0): Silken mouse enabled
[     7.642] (II) RADEON(0): Set up textured video
[     7.642] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[     7.642] (II) RADEON(0): [XvMC] Extension initialized.
[     7.642] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     7.643] (--) RandR disabled
[     7.726] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     7.726] (II) AIGLX: enabled GLX_ARB_create_context
[     7.726] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     7.726] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     7.726] (II) AIGLX: enabled GLX_INTEL_swap_event
[     7.726] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     7.726] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     7.726] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     7.726] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     7.726] (II) AIGLX: Loaded and initialized r600
[     7.726] (II) GLX: Initialized DRI2 GL provider for screen 0
[     7.776] (II) RADEON(0): Setting screen physical size to 508 x 285
[     7.786] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     7.790] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     7.790] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.790] (II) LoadModule: "evdev"
[     7.790] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     7.792] (II) Module evdev: vendor="X.Org Foundation"
[     7.792]     compiled for 1.17.1, module version = 2.9.0
[     7.792]     Module class: X.Org XInput Driver
[     7.792]     ABI class: X.Org XInput driver, version 21.0
[     7.792] (II) Using input driver 'evdev' for 'Power Button'
[     7.792] (**) Power Button: always reports core events
[     7.792] (**) evdev: Power Button: Device: "/dev/input/event1"
[     7.792] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.793] (--) evdev: Power Button: Found keys
[     7.793] (II) evdev: Power Button: Configuring as keyboard
[     7.793] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     7.793] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     7.793] (**) Option "xkb_rules" "evdev"
[     7.793] (**) Option "xkb_model" "pc105"
[     7.793] (**) Option "xkb_layout" "gb"
[     7.795] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[     7.796] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     7.796] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     7.796] (II) Using input driver 'evdev' for 'Power Button'
[     7.796] (**) Power Button: always reports core events
[     7.796] (**) evdev: Power Button: Device: "/dev/input/event0"
[     7.796] (--) evdev: Power Button: Vendor 0 Product 0x1
[     7.796] (--) evdev: Power Button: Found keys
[     7.796] (II) evdev: Power Button: Configuring as keyboard
[     7.796] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     7.796] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     7.796] (**) Option "xkb_rules" "evdev"
[     7.796] (**) Option "xkb_model" "pc105"
[     7.796] (**) Option "xkb_layout" "gb"
[     7.796] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event13)
[     7.796] (II) No input driver specified, ignoring this device.
[     7.796] (II) This device may have been added with another device file.
[     7.797] (II) config/udev: Adding input device Logitech K400 (/dev/input/event12)
[     7.797] (**) Logitech K400: Applying InputClass "evdev pointer catchall"
[     7.797] (**) Logitech K400: Applying InputClass "evdev keyboard catchall"
[     7.797] (II) Using input driver 'evdev' for 'Logitech K400'
[     7.797] (**) Logitech K400: always reports core events
[     7.797] (**) evdev: Logitech K400: Device: "/dev/input/event12"
[     7.797] (--) evdev: Logitech K400: Vendor 0x46d Product 0x4024
[     7.797] (--) evdev: Logitech K400: Found 20 mouse buttons
[     7.797] (--) evdev: Logitech K400: Found scroll wheel(s)
[     7.797] (--) evdev: Logitech K400: Found relative axes
[     7.797] (--) evdev: Logitech K400: Found x and y relative axes
[     7.797] (--) evdev: Logitech K400: Found absolute axes
[     7.797] (II) evdev: Logitech K400: Forcing absolute x/y axes to exist.
[     7.797] (--) evdev: Logitech K400: Found keys
[     7.797] (II) evdev: Logitech K400: Configuring as mouse
[     7.797] (II) evdev: Logitech K400: Configuring as keyboard
[     7.797] (II) evdev: Logitech K400: Adding scrollwheel support
[     7.797] (**) evdev: Logitech K400: YAxisMapping: buttons 4 and 5
[     7.797] (**) evdev: Logitech K400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.797] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.2/0003:046D:C52B.0003/0003:046D:4024.0004/input/input13/event12"
[     7.797] (II) XINPUT: Adding extended input device "Logitech K400" (type: KEYBOARD, id 8)
[     7.797] (**) Option "xkb_rules" "evdev"
[     7.797] (**) Option "xkb_model" "pc105"
[     7.797] (**) Option "xkb_layout" "gb"
[     7.797] (II) evdev: Logitech K400: initialized for relative axes.
[     7.797] (WW) evdev: Logitech K400: ignoring absolute axes.
[     7.797] (**) Logitech K400: (accel) keeping acceleration scheme 1
[     7.797] (**) Logitech K400: (accel) acceleration profile 0
[     7.797] (**) Logitech K400: (accel) acceleration factor: 2.000
[     7.797] (**) Logitech K400: (accel) acceleration threshold: 4
[     7.798] (II) config/udev: Adding input device Logitech K400 (/dev/input/mouse1)
[     7.798] (II) No input driver specified, ignoring this device.
[     7.798] (II) This device may have been added with another device file.
[     7.798] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:0038) (/dev/input/event2)
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): Applying InputClass "evdev pointer catchall"
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): Applying InputClass "evdev keyboard catchall"
[     7.798] (II) Using input driver 'evdev' for 'iMON Panel, Knob and Mouse(15c2:0038)'
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): always reports core events
[     7.798] (**) evdev: iMON Panel, Knob and Mouse(15c2:0038): Device: "/dev/input/event2"
[     7.798] (--) evdev: iMON Panel, Knob and Mouse(15c2:0038): Vendor 0x15c2 Product 0x38
[     7.798] (--) evdev: iMON Panel, Knob and Mouse(15c2:0038): Found 3 mouse buttons
[     7.798] (--) evdev: iMON Panel, Knob and Mouse(15c2:0038): Found scroll wheel(s)
[     7.798] (--) evdev: iMON Panel, Knob and Mouse(15c2:0038): Found relative axes
[     7.798] (--) evdev: iMON Panel, Knob and Mouse(15c2:0038): Found x and y relative axes
[     7.798] (--) evdev: iMON Panel, Knob and Mouse(15c2:0038): Found keys
[     7.798] (II) evdev: iMON Panel, Knob and Mouse(15c2:0038): Configuring as mouse
[     7.798] (II) evdev: iMON Panel, Knob and Mouse(15c2:0038): Configuring as keyboard
[     7.798] (II) evdev: iMON Panel, Knob and Mouse(15c2:0038): Adding scrollwheel support
[     7.798] (**) evdev: iMON Panel, Knob and Mouse(15c2:0038): YAxisMapping: buttons 4 and 5
[     7.798] (**) evdev: iMON Panel, Knob and Mouse(15c2:0038): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.798] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/input/input3/event2"
[     7.798] (II) XINPUT: Adding extended input device "iMON Panel, Knob and Mouse(15c2:0038)" (type: KEYBOARD, id 9)
[     7.798] (**) Option "xkb_rules" "evdev"
[     7.798] (**) Option "xkb_model" "pc105"
[     7.798] (**) Option "xkb_layout" "gb"
[     7.798] (II) evdev: iMON Panel, Knob and Mouse(15c2:0038): initialized for relative axes.
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): (accel) keeping acceleration scheme 1
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): (accel) acceleration profile 0
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): (accel) acceleration factor: 2.000
[     7.798] (**) iMON Panel, Knob and Mouse(15c2:0038): (accel) acceleration threshold: 4
[     7.799] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:0038) (/dev/input/mouse0)
[     7.799] (II) No input driver specified, ignoring this device.
[     7.799] (II) This device may have been added with another device file.
[     7.799] (II) config/udev: Adding input device iMON Remote (15c2:0038) (/dev/input/event3)
[     7.799] (**) iMON Remote (15c2:0038): Applying InputClass "evdev keyboard catchall"
[     7.799] (II) Using input driver 'evdev' for 'iMON Remote (15c2:0038)'
[     7.799] (**) iMON Remote (15c2:0038): always reports core events
[     7.799] (**) evdev: iMON Remote (15c2:0038): Device: "/dev/input/event3"
[     7.799] (--) evdev: iMON Remote (15c2:0038): Vendor 0x15c2 Product 0x38
[     7.799] (--) evdev: iMON Remote (15c2:0038): Found 3 mouse buttons
[     7.799] (--) evdev: iMON Remote (15c2:0038): Found keys
[     7.799] (II) evdev: iMON Remote (15c2:0038): Forcing relative x/y axes to exist.
[     7.799] (II) evdev: iMON Remote (15c2:0038): Configuring as mouse
[     7.799] (II) evdev: iMON Remote (15c2:0038): Configuring as keyboard
[     7.799] (**) evdev: iMON Remote (15c2:0038): YAxisMapping: buttons 4 and 5
[     7.799] (**) evdev: iMON Remote (15c2:0038): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     7.799] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-3/5-3:1.0/rc/rc0/input4/event3"
[     7.799] (II) XINPUT: Adding extended input device "iMON Remote (15c2:0038)" (type: KEYBOARD, id 10)
[     7.799] (**) Option "xkb_rules" "evdev"
[     7.799] (**) Option "xkb_model" "pc105"
[     7.799] (**) Option "xkb_layout" "gb"
[     7.799] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event9)
[     7.799] (II) No input driver specified, ignoring this device.
[     7.799] (II) This device may have been added with another device file.
[     7.800] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event10)
[     7.800] (II) No input driver specified, ignoring this device.
[     7.800] (II) This device may have been added with another device file.
[     7.800] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event11)
[     7.800] (II) No input driver specified, ignoring this device.
[     7.800] (II) This device may have been added with another device file.
[     7.800] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event4)
[     7.800] (II) No input driver specified, ignoring this device.
[     7.800] (II) This device may have been added with another device file.
[     7.800] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event5)
[     7.800] (II) No input driver specified, ignoring this device.
[     7.800] (II) This device may have been added with another device file.
[     7.800] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event6)
[     7.800] (II) No input driver specified, ignoring this device.
[     7.800] (II) This device may have been added with another device file.
[     7.801] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event7)
[     7.801] (II) No input driver specified, ignoring this device.
[     7.801] (II) This device may have been added with another device file.
[     7.801] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event8)
[     7.801] (II) No input driver specified, ignoring this device.
[     7.801] (II) This device may have been added with another device file.
[     9.143] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.736] (II) RADEON(0): EDID vendor "PHL", prod id 0
[     9.737] (II) RADEON(0): Using EDID range info for horizontal sync
[     9.737] (II) RADEON(0): Using EDID range info for vertical refresh
[     9.737] (II) RADEON(0): Printing DDC gathered Modelines:
[     9.737] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[     9.737] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     9.737] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     9.737] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     9.737] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     9.737] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     9.737] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     9.737] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[     9.737] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     9.737] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[     9.737] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     9.737] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.737] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[     9.737] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[     9.737] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.737] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     9.737] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     9.737] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.737] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     9.737] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     9.737] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.737] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     9.737] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.737] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     9.737] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     9.737] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     9.737] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     9.737] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     9.737] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.737] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[     9.737] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[     9.848] (II) RADEON(0): EDID vendor "PHL", prod id 0
[     9.848] (II) RADEON(0): Using hsync ranges from config file
[     9.848] (II) RADEON(0): Using vrefresh ranges from config file
[     9.848] (II) RADEON(0): Printing DDC gathered Modelines:
[     9.848] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[     9.848] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[     9.848] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[     9.848] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     9.848] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     9.848] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     9.848] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     9.848] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[     9.848] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     9.848] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[     9.848] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[     9.848] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.848] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[     9.848] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[     9.848] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.848] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     9.848] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     9.848] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.848] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     9.848] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     9.848] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[     9.848] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[     9.848] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.848] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[     9.848] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[     9.848] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[     9.848] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[     9.848] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[     9.848] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[     9.848] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[     9.848] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[     9.855] (II) XKB: reuse xkmfile /var/lib/xkb/server-E9EAE3F058EDAC2B794B0BAAB37A671E02945366.xkm
[    10.006] (II) RADEON(0): EDID vendor "PHL", prod id 0
[    10.006] (II) RADEON(0): Using hsync ranges from config file
[    10.006] (II) RADEON(0): Using vrefresh ranges from config file
[    10.006] (II) RADEON(0): Printing DDC gathered Modelines:
[    10.006] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[    10.006] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    10.006] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    10.006] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    10.006] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    10.006] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    10.006] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    10.006] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[    10.006] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    10.006] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    10.006] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    10.006] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    10.006] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    10.006] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    10.006] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    10.006] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    10.006] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    10.006] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    10.006] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    10.006] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    10.006] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    10.006] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    10.006] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    10.006] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    10.006] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    10.006] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    10.006] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    10.006] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    10.006] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    10.006] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[    10.006] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[    10.017] (II) XKB: reuse xkmfile /var/lib/xkb/server-E9EAE3F058EDAC2B794B0BAAB37A671E02945366.xkm
[    10.372] (II) RADEON(0): EDID vendor "PHL", prod id 0
[    10.372] (II) RADEON(0): Using hsync ranges from config file
[    10.372] (II) RADEON(0): Using vrefresh ranges from config file
[    10.372] (II) RADEON(0): Printing DDC gathered Modelines:
[    10.372] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[    10.372] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    10.372] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    10.372] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    10.372] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    10.372] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    10.372] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    10.372] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[    10.372] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    10.372] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    10.372] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    10.372] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    10.372] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    10.372] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    10.372] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    10.372] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    10.372] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    10.372] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    10.372] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    10.372] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    10.372] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    10.372] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    10.372] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    10.372] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    10.372] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    10.372] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    10.372] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    10.372] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    10.372] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    10.372] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[    10.372] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[    11.168] (II) XKB: reuse xkmfile /var/lib/xkb/server-4FD52B51AFE6709DED5AD52EDA784C00B079ECF7.xkm
[    24.676] (II) RADEON(0): EDID vendor "PHL", prod id 0
[    24.676] (II) RADEON(0): Using hsync ranges from config file
[    24.676] (II) RADEON(0): Using vrefresh ranges from config file
[    24.676] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.676] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[    24.676] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    24.676] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    24.676] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    24.676] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    24.676] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    24.676] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    24.676] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[    24.676] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    24.676] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    24.676] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    24.676] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.676] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    24.676] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    24.676] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.676] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    24.676] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    24.676] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.676] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    24.676] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    24.676] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    24.676] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    24.676] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.676] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    24.676] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    24.676] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[    24.676] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    24.676] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[    24.676] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    24.676] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[    24.676] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[   281.200] (II) RADEON(0): EDID vendor "PHL", prod id 0
[   281.201] (II) RADEON(0): Using hsync ranges from config file
[   281.201] (II) RADEON(0): Using vrefresh ranges from config file
[   281.201] (II) RADEON(0): Printing DDC gathered Modelines:
[   281.201] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[   281.201] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   281.201] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   281.201] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   281.201] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   281.201] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   281.201] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   281.201] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[   281.201] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   281.201] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[   281.201] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   281.201] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   281.201] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[   281.201] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[   281.201] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   281.201] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   281.201] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   281.201] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   281.201] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   281.201] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   281.201] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   281.201] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   281.201] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   281.201] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[   281.201] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   281.201] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   281.201] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   281.201] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   281.201] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   281.201] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[   281.201] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[   470.650] (II) XKB: reuse xkmfile /var/lib/xkb/server-B8CD4FE5A1833D7AB4B402792017A55B628FCF2D.xkm
[   498.713] (II) XKB: reuse xkmfile /var/lib/xkb/server-E9EAE3F058EDAC2B794B0BAAB37A671E02945366.xkm
[   711.889] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   777.710] (II) RADEON(0): EDID vendor "PHL", prod id 0
[   777.710] (II) RADEON(0): Using hsync ranges from config file
[   777.710] (II) RADEON(0): Using vrefresh ranges from config file
[   777.710] (II) RADEON(0): Printing DDC gathered Modelines:
[   777.710] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[   777.710] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   777.710] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   777.710] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   777.710] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   777.710] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   777.710] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   777.710] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[   777.710] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   777.710] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[   777.710] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   777.710] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   777.710] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[   777.710] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[   777.710] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   777.710] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   777.710] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   777.710] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   777.710] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   777.710] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   777.710] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   777.710] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   777.710] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   777.710] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[   777.710] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   777.710] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   777.710] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   777.710] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   777.710] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   777.710] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[   777.710] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[   778.014] (II) RADEON(0): EDID vendor "PHL", prod id 0
[   778.015] (II) RADEON(0): Using hsync ranges from config file
[   778.015] (II) RADEON(0): Using vrefresh ranges from config file
[   778.015] (II) RADEON(0): Printing DDC gathered Modelines:
[   778.015] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz eP)
[   778.015] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   778.015] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   778.015] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   778.015] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   778.015] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   778.015] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   778.015] (II) RADEON(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz e)
[   778.015] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   778.015] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[   778.015] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   778.015] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   778.015] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[   778.015] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[   778.015] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   778.015] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   778.015] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   778.015] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   778.015] (II) RADEON(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   778.015] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   778.015] (II) RADEON(0): Modeline "1440x480"x0.0   54.00  1440 1472 1596 1716  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   778.015] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   778.015] (II) RADEON(0): Modeline "1440x576"x0.0   54.00  1440 1464 1592 1728  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   778.015] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[   778.015] (II) RADEON(0): Modeline "2880x480i"x0.0   54.00  2880 2956 3204 3432  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   778.015] (II) RADEON(0): Modeline "2880x240"x0.0   54.00  2880 2956 3204 3432  240 244 247 262 -hsync -vsync (15.7 kHz e)
[   778.015] (II) RADEON(0): Modeline "2880x576i"x0.0   54.00  2880 2928 3180 3456  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   778.015] (II) RADEON(0): Modeline "2880x288"x0.0   54.00  2880 2928 3180 3456  288 290 293 312 -hsync -vsync (15.6 kHz e)
[   778.015] (II) RADEON(0): Modeline "2880x576"x0.0  108.00  2880 2928 3184 3456  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   778.015] (II) RADEON(0): Modeline "1920x1080i"x0.0   72.00  1920 1952 2120 2304  1080 1126 1136 1250 interlace +hsync -vsync (31.2 kHz e)
[   778.016] (--) RADEON(0): HDMI max TMDS frequency 225000KHz
[   788.649] (II) RADEON(0): Allocate new frame buffer 1366x768 stride 1376
[   788.649] (II) RADEON(0): VRAM usage limit set to 457740K
[   818.852] (II) RADEON(0): Allocate new frame buffer 1920x1080 stride 1920
[   818.852] (II) RADEON(0): VRAM usage limit set to 454165K
[   849.555] (II) XKB: generating xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[   849.580] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm

---

### Post by blm-ubunet on 2015-10-21
The exact model of TV is not revealed in the log.
I suspect the TV is not fullHD but has native resolution of 1360(1366/1368)x768 or 1280x720.

What exact video mode is used in windows (as reported by TV & set in GUI app) ?

When you say you changed resolution to 1300x768, you mean 1360x768 ?
And you used xrandr?

The default seems to be i50 (interlaced) but the TV supports 59.9 & 50 progressive scan.
I would still de-interlace (any media requiring it) on the video card as the TV can only accept specific video modes so scaling would be done before de-interlacing.

The Radeon driver supports VDPAU video decode/presentation (in h/w) so worth trying this in kodi etc.

Black frame:
You might have to find the setting in TV menu to force no scaling & direct pixel mapping.. Can be called:-
- one to one mapping
- just scan
- direct pixel mapping
- no scaling
- PC mode/input

---

