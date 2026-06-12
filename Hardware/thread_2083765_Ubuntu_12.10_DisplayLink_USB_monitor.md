---
title: "Ubuntu 12.10 DisplayLink USB monitor"
date: 2012-11-13
forum: Hardware
---

### Post by Madrid1978 on 2012-11-13
Hi all, I have a Lilliput UM70 USB monitor, and I'm trying to make it work with Ubuntu 12.10. 

My other card is an ATI and I have the propietary drivers installed (fglrx-updates). I'm using Gnome Classic.

I've been searching for hours but all the info I found was about installing a package (xserver-xorg-video-displaylink) that is no longer available in 12.10, and making changes to the xorg.conf file which I cannot find in my system.

Anyone has managed to make any DisplayLink USB monitor work in Ubuntu 12.10? Please point me to any info available, thanks very much! 

My lsusb output:

```

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 17e9:02a9 DisplayLink 
Bus 001 Device 004: ID 1e7d:2ced ROCCAT Kone Mouse
Bus 001 Device 005: ID 2040:5500 Hauppauge Windham
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 006: ID 18ec:3299 Arkmicro Technologies Inc. 
Bus 002 Device 007: ID 0572:1329 Conexant Systems (Rockwell), Inc. 
Bus 002 Device 008: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 002 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

```My dmesg output when I plug the monitor:

```

[ 1576.208145] usb 1-1.4: new high-speed USB device number 7 using ehci_hcd
[ 1576.303757] usb 1-1.4: New USB device found, idVendor=17e9, idProduct=02a9
[ 1576.303763] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1576.303768] usb 1-1.4: Product: LILLIPUT USB Monitor
[ 1576.303771] usb 1-1.4: Manufacturer: DisplayLink
[ 1576.303775] usb 1-1.4: SerialNumber: 88841333
[ 1576.305211] [drm] vendor descriptor length:17 data:17 5f 01 0015 05 00 01 03 00 04
[ 1576.388630] open /dev/fb0 user=0 fb_info=ee0cc000 count=1
[ 1576.388726] Console: switching to colour frame buffer device 100x30
[ 1576.388734] fb0: udldrmfb frame buffer device
[ 1576.388737] drm: registered panic notifier
[ 1576.388741] [drm] Initialized udl 0.0.1 20120220 on minor 0


```

---

### Post by d98jh on 2012-11-26
I have one of those UM-70 as well, haven't tried it in 12.10 yet though since I haven't updated any of my computers yet.
Since the driver is now included in the kernel you don't need to install any packages anymore. You just add the necessary information to the xorg.conf file.
None of my computers have AMD graphics but I think this is the command for generating a default xorg.conf with the amdconfig tool.
```
$ sudo amdconfig --initial -f
```

What happens when you connect the UM-70? Does the screen turn green?

---

### Post by Madrid1978 on 2012-11-26
Hi, d98jh, thanks for your reply. No, it doesn't show the green screen, when I turn it on it just displays a black screen, but I can do CTRL-ALT-F1 and get a login screen on it. So somehow Ubuntu knows the monitor is there.

I've tried with the amdconfig command and it creates a xorg.conf file, I've tried adding the monitor to that file using some samples I've found around the web of people that got it working but it still does nothing. 

I'll keep trying and post any updates here.

---

### Post by d98jh on 2012-11-27
Ok, it sounds like you're not too far from your goal then.

I wrote a post two years ago how I got it working here: [http://ubuntuforums.org/showpost.php?p=9537133&postcount=10](http://ubuntuforums.org/showpost.php?p=9537133&postcount=10)

I think you should be able to copy the xorg.conf stuff from that post and merge it with your existing one.
Make sure that the UM-70 is defined as "Screen 0" in the server layout part of your config or it won't work. (At least for me it didn't).

Good luck and let me know if you have any other questions!

---

### Post by Madrid1978 on 2012-11-27
Ok, some updates. This is the xorg.conf file I'm using:

```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen    0    "DisplayLinkScreen"
    Screen  1  "aticonfig-Screen[0]-0" RightOf "DisplayLinkScreen"
    Option    "Xinerama" "on"
EndSection

Section "Module"
EndSection

############## ATI ################
Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

################ DisplayLink Stuff ###################
Section "Device"
       Identifier      "DisplayLinkDevice"
       Driver         "displaylink"
       Option      "fbdev" "/dev/usbvideocard"
EndSection
Section "Monitor"
       Identifier      "DisplayLinkMonitor"
    DisplaySize    152 92
EndSection
Section "Screen"
       Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
       Monitor         "DisplayLinkMonitor"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes   "800x480"
    EndSubSection
EndSection

```With this file I can use the UM70 only as console. I suppose it is because it doesn't support 24 bits.

So I tried changing both depths (the ATI monitor and the UM70) to 16, and with that config Ubuntu boots in the UM70, with a nice warning that the system is running in low graphics mode. But I can log in and use the GUI in the UM70. The big monitor remains black. It was nice to see the UM70 with my desktop :-)

So looking into the X logs I found this to be the problem:

fglrx(0): Given depth (16) is not supported by fglrx driver

I've searched for this problem and it looks that it has no solution, the fglrx driver does not support 16 bits color depth.

Then after some more googling I found there is another driver for ATI cards, called radeon, not propietary, and I tried with that. In the line of the ATI driver I changed "fglrx" for "radeon", made sure that depth for both monitors was 16, and boot up again. Now I can use the big monitor but the UM70 stays black, CTRL-ALT-F1 doesn't show the console on it.

Below is the log from this boot (using the radeon driver). One thing that seems odd is that at [32.275] I see Failed to load module "displaylink" (module does not exist, 0). I thought that it was included in the kernel... 

Anyway, the only way I've managed to display my desktop in the UM70 is by using the flgrx driver and setting both monitors to 16 bits depth, and that with the cost of making the big monitor unusable. Not bad for three hours of work :-)

Maybe I'd have better luck with an NVIDIA card? My ATI is quite old and I wouldn't mind buying a new card, I do some gaming in Windows so I'd put it to good use.

```

[    31.222] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    31.222] X Protocol Version 11, Revision 0
[    31.222] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[    31.222] Current Operating System: Linux MEDION 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:27:31 UTC 2012 i686
[    31.222] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=f462579e-17e7-44ab-980c-add18f9a54e1 ro quiet splash vt.handoff=7
[    31.222] Build Date: 08 October 2012  03:34:08PM
[    31.222] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    31.222] Current version of pixman: 0.26.0
[    31.222]    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    31.222] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.222] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 27 22:09:21 2012
[    31.321] (==) Using config file: "/etc/X11/xorg.conf"
[    31.321] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.530] (==) ServerLayout "aticonfig Layout"
[    31.530] (**) |-->Screen "DisplayLinkScreen" (0)
[    31.530] (**) |   |-->Monitor "DisplayLinkMonitor"
[    31.531] (**) |   |-->Device "DisplayLinkDevice"
[    31.531] (**) |-->Screen "aticonfig-Screen[0]-0" (1)
[    31.531] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    31.531] (**) |   |-->Device "aticonfig-Device[0]-0"
[    31.531] (**) Option "Xinerama" "on"
[    31.531] (==) Automatically adding devices
[    31.531] (==) Automatically enabling devices
[    31.531] (==) Automatically adding GPU devices
[    31.531] (**) Xinerama: enabled
[    31.599] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.599]    Entry deleted from font path.
[    31.599] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.599]    Entry deleted from font path.
[    31.599] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.599]    Entry deleted from font path.
[    31.599] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.599]    Entry deleted from font path.
[    31.599] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.599]    Entry deleted from font path.
[    31.599] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    31.599]    Entry deleted from font path.
[    31.599] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    31.599] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.599] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.599] (II) Loader magic: 0xb77c0640
[    31.599] (II) Module ABI versions:
[    31.599]    X.Org ANSI C Emulation: 0.4
[    31.599]    X.Org Video Driver: 13.0
[    31.599]    X.Org XInput driver : 18.0
[    31.599]    X.Org Server Extension : 7.0
[    31.600] (II) config/udev: Adding drm device (/dev/dri/card1)
[    31.600] (II) config/udev: Adding drm device (/dev/dri/card0)
[    31.601] (--) PCI:*(0:1:0:0) 1002:68d9:174b:e142 rev 0, Mem @ 0xd0000000/268435456, 0xfbee0000/131072, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    31.601] (II) Open ACPI successful (/var/run/acpid.socket)
[    31.876] Initializing built-in extension Generic Event Extension
[    31.876] Initializing built-in extension SHAPE
[    31.876] Initializing built-in extension MIT-SHM
[    31.876] Initializing built-in extension XInputExtension
[    31.876] Initializing built-in extension XTEST
[    31.876] Initializing built-in extension BIG-REQUESTS
[    31.876] Initializing built-in extension SYNC
[    31.876] Initializing built-in extension XKEYBOARD
[    31.876] Initializing built-in extension XC-MISC
[    31.876] Initializing built-in extension SECURITY
[    31.876] Initializing built-in extension XINERAMA
[    31.876] Initializing built-in extension XFIXES
[    31.876] Initializing built-in extension RENDER
[    31.876] Initializing built-in extension RANDR
[    31.876] Initializing built-in extension COMPOSITE
[    31.876] Initializing built-in extension DAMAGE
[    31.876] Initializing built-in extension MIT-SCREEN-SAVER
[    31.876] Initializing built-in extension DOUBLE-BUFFER
[    31.876] Initializing built-in extension RECORD
[    31.876] Initializing built-in extension DPMS
[    31.876] Initializing built-in extension X-Resource
[    31.876] Initializing built-in extension XVideo
[    31.877] Initializing built-in extension XVideo-MotionCompensation
[    31.877] Initializing built-in extension XFree86-VidModeExtension
[    31.877] Initializing built-in extension XFree86-DGA
[    31.877] Initializing built-in extension XFree86-DRI
[    31.877] Initializing built-in extension DRI2
[    31.877] (II) "glx" will be loaded by default.
[    31.877] (II) LoadModule: "glx"
[    32.020] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.251] (II) Module glx: vendor="X.Org Foundation"
[    32.251]    compiled for 1.13.0, module version = 1.0.0
[    32.251]    ABI class: X.Org Server Extension, version 7.0
[    32.251] (==) AIGLX enabled
[    32.251] Loading extension GLX
[    32.251] (II) LoadModule: "displaylink"
[    32.275] (WW) Warning, couldn't open module displaylink
[    32.275] (II) UnloadModule: "displaylink"
[    32.275] (II) Unloading displaylink
[    32.275] (EE) Failed to load module "displaylink" (module does not exist, 0)
[    32.275] (II) LoadModule: "radeon"
[    32.275] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.403] (II) Module radeon: vendor="X.Org Foundation"
[    32.403]    compiled for 1.13.0, module version = 6.99.99
[    32.403]    Module class: X.Org Video Driver
[    32.403]    ABI class: X.Org Video Driver, version 13.0
[    32.403] (==) Matched fglrx as autoconfigured driver 0
[    32.403] (==) Matched ati as autoconfigured driver 1
[    32.403] (==) Matched fglrx as autoconfigured driver 2
[    32.403] (==) Matched ati as autoconfigured driver 3
[    32.403] (==) Matched vesa as autoconfigured driver 4
[    32.403] (==) Matched modesetting as autoconfigured driver 5
[    32.403] (==) Matched fbdev as autoconfigured driver 6
[    32.403] (==) Assigned the driver to the xf86ConfigLayout
[    32.403] (II) LoadModule: "fglrx"
[    32.403] (WW) Warning, couldn't open module fglrx
[    32.403] (II) UnloadModule: "fglrx"
[    32.403] (II) Unloading fglrx
[    32.403] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    32.403] (II) LoadModule: "ati"
[    32.404] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    32.649] (II) Module ati: vendor="X.Org Foundation"
[    32.649]    compiled for 1.13.0, module version = 6.99.99
[    32.649]    Module class: X.Org Video Driver
[    32.649]    ABI class: X.Org Video Driver, version 13.0
[    32.649] (II) LoadModule: "radeon"
[    32.649] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    32.649] (II) Module radeon: vendor="X.Org Foundation"
[    32.649]    compiled for 1.13.0, module version = 6.99.99
[    32.649]    Module class: X.Org Video Driver
[    32.649]    ABI class: X.Org Video Driver, version 13.0
[    32.649] (II) LoadModule: "vesa"
[    32.649] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.697] (II) Module vesa: vendor="X.Org Foundation"
[    32.697]    compiled for 1.12.99.902, module version = 2.3.2
[    32.697]    Module class: X.Org Video Driver
[    32.697]    ABI class: X.Org Video Driver, version 13.0
[    32.697] (II) LoadModule: "modesetting"
[    32.697] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    32.725] (II) Module modesetting: vendor="X.Org Foundation"
[    32.725]    compiled for 1.13.0, module version = 0.5.0
[    32.725]    Module class: X.Org Video Driver
[    32.725]    ABI class: X.Org Video Driver, version 13.0
[    32.725] (II) LoadModule: "fbdev"
[    32.725] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.740] (II) Module fbdev: vendor="X.Org Foundation"
[    32.740]    compiled for 1.12.99.902, module version = 0.4.3
[    32.740]    Module class: X.Org Video Driver
[    32.740]    ABI class: X.Org Video Driver, version 13.0
[    32.740] (II) RADEON: Driver for ATI Radeon chipsets:
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
[    32.742] (II) VESA: driver for VESA chipsets: vesa
[    32.742] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    32.742] (II) FBDEV: driver for framebuffer: fbdev
[    32.742] (++) using VT number 7

[    32.776] (II) [KMS] Kernel modesetting enabled.
[    32.776] (WW) Falling back to old probe method for vesa
[    32.776] (WW) Falling back to old probe method for modesetting
[    32.776] (EE) open /dev/dri/card0: Resource temporarily unavailable
[    32.776] (WW) Falling back to old probe method for fbdev
[    32.776] (II) Loading sub module "fbdevhw"
[    32.776] (II) LoadModule: "fbdevhw"
[    32.777] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.833] (II) Module fbdevhw: vendor="X.Org Foundation"
[    32.833]    compiled for 1.13.0, module version = 0.0.2
[    32.833]    ABI class: X.Org Video Driver, version 13.0
[    32.834] (**) RADEON(0): Depth 16, (--) framebuffer bpp 16
[    32.834] (II) RADEON(0): Pixel depth = 16 bits stored in 2 bytes (16 bpp pixmaps)
[    32.834] (==) RADEON(0): Default visual is TrueColor
[    32.834] (==) RADEON(0): RGB weight 565
[    32.834] (II) RADEON(0): Using 6 bits per RGB (8 bit DAC)
[    32.834] (--) RADEON(0): Chipset: "ATI Radeon HD 5570" (ChipID = 0x68d9)
[    32.834] (II) Loading sub module "dri2"
[    32.834] (II) LoadModule: "dri2"
[    32.834] (II) Module "dri2" already built-in
[    32.834] (II) Loading sub module "exa"
[    32.834] (II) LoadModule: "exa"
[    32.834] (II) Loading /usr/lib/xorg/modules/libexa.so
[    32.876] (II) Module exa: vendor="X.Org Foundation"
[    32.876]    compiled for 1.13.0, module version = 2.6.0
[    32.876]    ABI class: X.Org Video Driver, version 13.0
[    32.876] (II) RADEON(0): KMS Color Tiling: enabled
[    32.876] (II) RADEON(0): KMS Pageflipping: enabled
[    32.876] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    32.878] (II) RADEON(0): Output HDMI-0 using monitor section DisplayLinkMonitor
[    32.910] (II) RADEON(0): Output DVI-1 has no monitor section
[    32.932] (II) RADEON(0): Output VGA-0 has no monitor section
[    32.934] (II) RADEON(0): EDID for output HDMI-0
[    32.966] (II) RADEON(0): EDID for output DVI-1
[    32.966] (II) RADEON(0): Manufacturer: PKB  Model: c1  Serial#: 6313595
[    32.966] (II) RADEON(0): Year: 2010  Week: 6
[    32.966] (II) RADEON(0): EDID Version: 1.3
[    32.966] (II) RADEON(0): Digital Display Input
[    32.966] (II) RADEON(0): Max Image Size [cm]: horiz.: 51  vert.: 28
[    32.966] (II) RADEON(0): Gamma: 2.20
[    32.966] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    32.966] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    32.966] (II) RADEON(0): First detailed timing is preferred mode
[    32.966] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    32.966] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    32.966] (II) RADEON(0): Supported established timings:
[    32.966] (II) RADEON(0): 720x400@70Hz
[    32.966] (II) RADEON(0): 640x480@60Hz
[    32.966] (II) RADEON(0): 640x480@67Hz
[    32.966] (II) RADEON(0): 800x600@56Hz
[    32.966] (II) RADEON(0): 800x600@60Hz
[    32.966] (II) RADEON(0): 1024x768@60Hz
[    32.966] (II) RADEON(0): 1024x768@70Hz
[    32.966] (II) RADEON(0): Manufacturer's mask: 0
[    32.966] (II) RADEON(0): Supported standard timings:
[    32.966] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    32.966] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    32.966] (II) RADEON(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    32.966] (II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    32.966] (II) RADEON(0): Supported detailed timing:
[    32.966] (II) RADEON(0): clock: 148.5 MHz   Image Size:  509 x 286 mm
[    32.966] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    32.966] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    32.966] (II) RADEON(0): Monitor name: Viseo 230Ws
[    32.966] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 185 MHz
[    32.966] (II) RADEON(0): Serial No: D150C0114002
[    32.966] (II) RADEON(0): EDID (in hex):
[    32.966] (II) RADEON(0):    00ffffffffffff004162c1007b566000
[    32.966] (II) RADEON(0):    0614010380331c78eaee95a3544c9926
[    32.966] (II) RADEON(0):    0f5054b30c00714f8180810095000101
[    32.966] (II) RADEON(0):    010101010101023a801871382d40582c
[    32.966] (II) RADEON(0):    4500fd1e1100001e000000fc00566973
[    32.966] (II) RADEON(0):    656f2032333057730a20000000fd0038
[    32.966] (II) RADEON(0):    4c1f5312000a202020202020000000ff
[    32.966] (II) RADEON(0):    004431353043303131343030320a0057
[    32.966] (II) RADEON(0): Printing probed modes for output DVI-1
[    32.966] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    32.966] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    32.966] (II) RADEON(0): Modeline "1680x945"x60.0  131.48  1680 1784 1960 2240  945 946 949 978 -hsync +vsync (58.7 kHz)
[    32.966] (II) RADEON(0): Modeline "1400x1050"x74.9  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    32.966] (II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[    32.966] (II) RADEON(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    32.966] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    32.966] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    32.966] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    32.966] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    32.966] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    32.966] (II) RADEON(0): Modeline "1366x768"x60.0   85.89  1366 1439 1583 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[    32.966] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    32.966] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    32.966] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    32.966] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    32.966] (II) RADEON(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz e)
[    32.966] (II) RADEON(0): Modeline "1280x768"x60.0   68.25  1280 1328 1360 1440  768 771 778 790 +hsync -vsync (47.4 kHz e)
[    32.966] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    32.966] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    32.966] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    32.966] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[    32.966] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    32.966] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    32.966] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    32.966] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    32.966] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    32.966] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    32.966] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    32.966] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    32.966] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    32.966] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    32.988] (II) RADEON(0): EDID for output VGA-0
[    32.988] (II) RADEON(0): Output HDMI-0 disconnected
[    32.988] (II) RADEON(0): Output DVI-1 connected
[    32.988] (II) RADEON(0): Output VGA-0 disconnected
[    32.988] (II) RADEON(0): Using exact sizes for initial modes
[    32.988] (II) RADEON(0): Output DVI-1 using initial mode 1920x1080
[    32.988] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    32.988] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:40000000 visible:f7d7000
[    32.988] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    32.988] (**) RADEON(0): Display dimensions: (152, 92) mm
[    32.988] (**) RADEON(0): DPI set to (320, 298)
[    32.988] (II) Loading sub module "fb"
[    32.988] (II) LoadModule: "fb"
[    32.988] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.988] (II) Module fb: vendor="X.Org Foundation"
[    32.988]    compiled for 1.13.0, module version = 1.0.0
[    32.988]    ABI class: X.Org ANSI C Emulation, version 0.4
[    32.988] (II) Loading sub module "ramdac"
[    32.988] (II) LoadModule: "ramdac"
[    32.988] (II) Module "ramdac" already built-in
[    32.988] (II) UnloadModule: "vesa"
[    32.988] (II) Unloading vesa
[    32.988] (II) UnloadModule: "modesetting"
[    32.988] (II) Unloading modesetting
[    32.988] (II) UnloadModule: "fbdev"
[    32.988] (II) Unloading fbdev
[    32.988] (II) UnloadSubModule: "fbdevhw"
[    32.988] (II) Unloading fbdevhw
[    33.022] (II) RADEON(0): [DRI2] Setup complete
[    33.022] (II) RADEON(0): [DRI2]   DRI driver: r600
[    33.022] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    33.022] (II) RADEON(0): Front buffer size: 4052K
[    33.022] (II) RADEON(0): VRAM usage limit set to 224762K
[    33.045] (==) RADEON(0): Backing store disabled
[    33.045] (II) RADEON(0): Direct rendering enabled
[    33.045] (II) RADEON(0): Setting EXA maxPitchBytes
[    33.045] (II) EXA(0): Driver allocated offscreen pixmaps
[    33.045] (II) EXA(0): Driver registered support for the following operations:
[    33.045] (II)         Solid
[    33.045] (II)         Copy
[    33.045] (II)         Composite (RENDER acceleration)
[    33.045] (II)         UploadToScreen
[    33.045] (II)         DownloadFromScreen
[    33.045] (II) RADEON(0): Acceleration enabled
[    33.045] (==) RADEON(0): DPMS enabled
[    33.045] (==) RADEON(0): Silken mouse enabled
[    33.046] (II) RADEON(0): Set up textured video
[    33.046] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    33.046] (II) RADEON(0): [XvMC] Extension initialized.
[    33.046] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    33.046] (WW) RADEON(0): Option "fbdev" is not used
[    33.046] (--) RandR disabled
[    35.721] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.721] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.721] (II) AIGLX: enabled GLX_ARB_create_context
[    35.721] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    35.721] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    35.721] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.721] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.722] (II) AIGLX: Loaded and initialized r600
[    35.722] (II) GLX: Initialized DRI2 GL provider for screen 0
[    36.361] (II) RADEON(0): Setting screen physical size to 507 x 285
[    36.594] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.734] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    36.734] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.734] (II) LoadModule: "evdev"
[    36.734] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.979] (II) Module evdev: vendor="X.Org Foundation"
[    36.979]    compiled for 1.13.0, module version = 2.7.3
[    36.979]    Module class: X.Org XInput Driver
[    36.979]    ABI class: X.Org XInput driver, version 18.0
[    36.979] (II) Using input driver 'evdev' for 'Power Button'
[    36.979] (**) Power Button: always reports core events
[    36.979] (**) evdev: Power Button: Device: "/dev/input/event1"
[    36.979] (--) evdev: Power Button: Vendor 0 Product 0x1
[    36.979] (--) evdev: Power Button: Found keys
[    36.979] (II) evdev: Power Button: Configuring as keyboard
[    36.979] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    36.979] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    36.979] (**) Option "xkb_rules" "evdev"
[    36.979] (**) Option "xkb_model" "pc105"
[    36.979] (**) Option "xkb_layout" "es"
[    36.981] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[    37.016] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    37.016] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.016] (II) Using input driver 'evdev' for 'Power Button'
[    37.016] (**) Power Button: always reports core events
[    37.016] (**) evdev: Power Button: Device: "/dev/input/event0"
[    37.016] (--) evdev: Power Button: Vendor 0 Product 0x1
[    37.016] (--) evdev: Power Button: Found keys
[    37.016] (II) evdev: Power Button: Configuring as keyboard
[    37.016] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    37.016] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    37.016] (**) Option "xkb_rules" "evdev"
[    37.016] (**) Option "xkb_model" "pc105"
[    37.016] (**) Option "xkb_layout" "es"
[    37.017] (II) config/udev: Adding drm device (/dev/dri/card1)
[    37.017] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event10)
[    37.017] (II) No input driver specified, ignoring this device.
[    37.017] (II) This device may have been added with another device file.
[    37.017] (II) config/udev: Adding drm device (/dev/dri/card0)
[    37.017] (II) config/udev: Adding drm device (/dev/dri/card0)
[    37.017] (II) config/udev: Adding input device ROCCAT ROCCAT Kone (/dev/input/event3)
[    37.017] (**) ROCCAT ROCCAT Kone: Applying InputClass "evdev pointer catchall"
[    37.017] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Kone'
[    37.017] (**) ROCCAT ROCCAT Kone: always reports core events
[    37.017] (**) evdev: ROCCAT ROCCAT Kone: Device: "/dev/input/event3"
[    37.017] (--) evdev: ROCCAT ROCCAT Kone: Vendor 0x1e7d Product 0x2ced
[    37.017] (--) evdev: ROCCAT ROCCAT Kone: Found 9 mouse buttons
[    37.017] (--) evdev: ROCCAT ROCCAT Kone: Found scroll wheel(s)
[    37.017] (--) evdev: ROCCAT ROCCAT Kone: Found relative axes
[    37.017] (--) evdev: ROCCAT ROCCAT Kone: Found x and y relative axes
[    37.017] (II) evdev: ROCCAT ROCCAT Kone: Configuring as mouse
[    37.017] (II) evdev: ROCCAT ROCCAT Kone: Adding scrollwheel support
[    37.017] (**) evdev: ROCCAT ROCCAT Kone: YAxisMapping: buttons 4 and 5
[    37.017] (**) evdev: ROCCAT ROCCAT Kone: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.017] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input3/event3"
[    37.017] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Kone" (type: MOUSE, id 8)
[    37.017] (II) evdev: ROCCAT ROCCAT Kone: initialized for relative axes.
[    37.017] (**) ROCCAT ROCCAT Kone: (accel) keeping acceleration scheme 1
[    37.017] (**) ROCCAT ROCCAT Kone: (accel) acceleration profile 0
[    37.017] (**) ROCCAT ROCCAT Kone: (accel) acceleration factor: 2.000
[    37.017] (**) ROCCAT ROCCAT Kone: (accel) acceleration threshold: 4
[    37.018] (II) config/udev: Adding input device ROCCAT ROCCAT Kone (/dev/input/mouse0)
[    37.018] (II) No input driver specified, ignoring this device.
[    37.018] (II) This device may have been added with another device file.
[    37.018] (II) config/udev: Adding input device ROCCAT ROCCAT Kone (/dev/input/event4)
[    37.018] (**) ROCCAT ROCCAT Kone: Applying InputClass "evdev keyboard catchall"
[    37.018] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Kone'
[    37.018] (**) ROCCAT ROCCAT Kone: always reports core events
[    37.018] (**) evdev: ROCCAT ROCCAT Kone: Device: "/dev/input/event4"
[    37.018] (--) evdev: ROCCAT ROCCAT Kone: Vendor 0x1e7d Product 0x2ced
[    37.018] (--) evdev: ROCCAT ROCCAT Kone: Found keys
[    37.018] (II) evdev: ROCCAT ROCCAT Kone: Configuring as keyboard
[    37.018] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/input/input4/event4"
[    37.018] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Kone" (type: KEYBOARD, id 9)
[    37.018] (**) Option "xkb_rules" "evdev"
[    37.018] (**) Option "xkb_model" "pc105"
[    37.018] (**) Option "xkb_layout" "es"
[    37.018] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event5)
[    37.018] (II) No input driver specified, ignoring this device.
[    37.018] (II) This device may have been added with another device file.
[    37.018] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event6)
[    37.018] (II) No input driver specified, ignoring this device.
[    37.018] (II) This device may have been added with another device file.
[    37.018] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event7)
[    37.018] (II) No input driver specified, ignoring this device.
[    37.018] (II) This device may have been added with another device file.
[    37.019] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event8)
[    37.019] (II) No input driver specified, ignoring this device.
[    37.019] (II) This device may have been added with another device file.
[    37.019] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event9)
[    37.019] (II) No input driver specified, ignoring this device.
[    37.019] (II) This device may have been added with another device file.
[    37.019] (II) config/udev: Adding input device USB2.0 PC CAMERA (/dev/input/event11)
[    37.019] (**) USB2.0 PC CAMERA: Applying InputClass "evdev keyboard catchall"
[    37.019] (II) Using input driver 'evdev' for 'USB2.0 PC CAMERA'
[    37.019] (**) USB2.0 PC CAMERA: always reports core events
[    37.019] (**) evdev: USB2.0 PC CAMERA: Device: "/dev/input/event11"
[    37.019] (--) evdev: USB2.0 PC CAMERA: Vendor 0x18ec Product 0x3299
[    37.019] (--) evdev: USB2.0 PC CAMERA: Found keys
[    37.019] (II) evdev: USB2.0 PC CAMERA: Configuring as keyboard
[    37.019] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.4/2-1.6.4.1/2-1.6.4.1:1.0/input/input11/event11"
[    37.019] (II) XINPUT: Adding extended input device "USB2.0 PC CAMERA" (type: KEYBOARD, id 10)
[    37.019] (**) Option "xkb_rules" "evdev"
[    37.019] (**) Option "xkb_model" "pc105"
[    37.019] (**) Option "xkb_layout" "es"
[    37.019] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    37.019] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    37.019] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    37.019] (**) AT Translated Set 2 keyboard: always reports core events
[    37.019] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    37.019] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    37.019] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    37.019] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    37.020] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    37.020] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    37.020] (**) Option "xkb_rules" "evdev"
[    37.020] (**) Option "xkb_model" "pc105"
[    37.020] (**) Option "xkb_layout" "es"
[    40.732] (II) RADEON(0): EDID vendor "PKB", prod id 193
[    40.732] (II) RADEON(0): Using EDID range info for horizontal sync
[    40.732] (II) RADEON(0): Using EDID range info for vertical refresh
[    40.732] (II) RADEON(0): Printing DDC gathered Modelines:
[    40.732] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    40.732] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.732] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    40.732] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    40.732] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.732] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.732] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    40.732] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.732] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.732] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.732] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    40.732] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    43.500] (II) RADEON(0): EDID vendor "PKB", prod id 193
[    43.500] (II) RADEON(0): Using hsync ranges from config file
[    43.500] (II) RADEON(0): Using vrefresh ranges from config file
[    43.500] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.500] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    43.500] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    43.500] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    43.500] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    43.500] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    43.500] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    43.500] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    43.500] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    43.500] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    43.500] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    43.500] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    43.500] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.541] (II) RADEON(0): EDID vendor "PKB", prod id 193
[    49.541] (II) RADEON(0): Using hsync ranges from config file
[    49.541] (II) RADEON(0): Using vrefresh ranges from config file
[    49.541] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.541] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.541] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.541] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.541] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.541] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.541] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.541] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.541] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.541] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.541] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.541] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.541] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.836] (II) RADEON(0): EDID vendor "PKB", prod id 193
[    49.836] (II) RADEON(0): Using hsync ranges from config file
[    49.836] (II) RADEON(0): Using vrefresh ranges from config file
[    49.836] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.836] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.836] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.836] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.836] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.836] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.836] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.836] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.836] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.836] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    49.836] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.836] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    49.836] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    49.891] (II) XKB: reuse xkmfile /var/lib/xkb/server-1EEA8A8B5282F1A1C5B4CDBD09D3AB33A69761C2.xkm
[    74.013] (II) RADEON(0): EDID vendor "PKB", prod id 193
[    74.013] (II) RADEON(0): Using hsync ranges from config file
[    74.013] (II) RADEON(0): Using vrefresh ranges from config file
[    74.013] (II) RADEON(0): Printing DDC gathered Modelines:
[    74.013] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    74.013] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    74.013] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    74.013] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    74.013] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    74.013] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    74.013] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    74.013] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    74.013] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    74.013] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    74.013] (II) RADEON(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    74.013] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)

```

---

