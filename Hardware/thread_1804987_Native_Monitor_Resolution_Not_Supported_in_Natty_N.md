---
title: "Native Monitor Resolution Not Supported in Natty Narwhal"
date: 2011-07-15
forum: Hardware
---

### Post by philliplemky on 2011-07-15
Hi,

I'm running Ubuntu 11.04 (Natty Narwhal) and I have a Samsung SyncMaster 225BW LCD monitor. The native resolution of the monitor is 1680 x 1050. In Natty, when I go into System Settings > Monitors, it shows a series of resolutions, including 1400 x 1050 and 1600 x 1200, but nothing for 1680 x 1050. It also shows "Monitor: Unknown," and I suspect its lack of ability to recognize the monitor may have something to do with it. There's a Detect Monitors button in the window, but when I click on it, it doesn't make a difference.

Any suggestions?

Phil

---

### Post by realzippy on 2011-07-15
Which graphics card/driver do you use?

.... remembering few threads about SyncMaster 225BW with that problem.
The monitor's EDID can't be read correctly.If running
a nvidia card/driver it is possible to feed an EDID file "manually"
or force the driver to ignore it by modifying xorg.conf.

If this is possible with other cards/drivers (AMD/Intel)
I honestly do not know.(in the moment)
Someone else?

---

### Post by philliplemky on 2011-07-15
Video card... If I run:

lspci | grep VGA

...I get:

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]

---

### Post by realzippy on 2011-07-15
Is there an ATI/AMD graphics driver offered in the 'Additional Drivers' GUI ?

---

### Post by philliplemky on 2011-07-15
Yes, the Additional Drivers screen offered "ATI/AMD proprietary FGLRX graphics driver", which I've already installed.

---

### Post by Blasphemist on 2011-07-15
I have seen in other threads that you can read the edid data from a monitor and parse it into a format for a display section in a xorg.conf file. I did a search in a sticky thread on video issues and that is where I'd seen it. I think this post in that thread will help you but if you need, do a search in that thread yourself for more information.
[http://ubuntuforums.org/showpost.php?p=10925558&postcount=310](http://ubuntuforums.org/showpost.php?p=10925558&postcount=310)

---

### Post by rickytikki on 2011-07-15
Hello I have a Samsung SyncMaster T240HD i had similar problems. However i have and nvidia graphics card. my native resolution in 1900x1200. I had to go through my nvidia x server settings and add the resolution manually. hope this somewhat helps.

---

### Post by realzippy on 2011-07-15
> **Blasphemist said:**
> I have seen in other threads that you can read the edid data from a monitor and parse it into a format for a display section in a xorg.conf file. I did a search in a sticky thread on video issues and that is where I'd seen it. I think this post in that thread will help you but if you need, do a search in that thread yourself for more information.
[http://ubuntuforums.org/showpost.php?p=10925558&postcount=310](http://ubuntuforums.org/showpost.php?p=10925558&postcount=310)

Think the link is about nvidia driver,I already mentioned that feeding an EDID is possible there.Since OP has catalyst running,
we had to know if this works with the ATI driver.

So any ATI fellows around?

---

### Post by Blasphemist on 2011-07-15
> **realzippy said:**
> Think the link is about nvidia driver,I already mentioned that feeding an EDID is possible there.Since OP has catalyst running,
we had to know if this works with the ATI driver.

The thread I posted is about a cards. It is not specific to nvidia even if that one post is.

---

### Post by realzippy on 2011-07-15
*philliplemky*,can you post your
/etc/X11/xorg.conf
and your
/var/log/Xorg.0.log
files please?

---

### Post by ajgreeny on 2011-07-15
At one time with my ATI 9200SE card I had to manually edit the xorg.conf file and add my wanted resolution in the format:-
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes       [COLOR=Red]"1680 x 1050"[/COLOR]  "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
Try a similar format in your xorg.conf, but with your own resolution, of course, as shown in red.  Make sure you backup your current xorg.conf first in case it makes matters worse.

---

### Post by philliplemky on 2011-07-15
xorg.conf:
```

--------------------------------------------------

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection
--------------------------------------------------

Xorg.0.log:
--------------------------------------------------
[    12.837] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    12.837] X Protocol Version 11, Revision 0
[    12.837] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    12.837] Current Operating System: Linux plemky-desktop 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    12.837] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=ad0ac270-1a52-4582-8b78-ef944421d466 ro quiet splash vt.handoff=7
[    12.837] Build Date: 21 May 2011  11:38:35AM
[    12.837] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    12.837] Current version of pixman: 0.20.2
[    12.837]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    12.837] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.837] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 15 11:21:56 2011
[    12.837] (==) Using config file: "/etc/X11/xorg.conf"
[    12.837] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.837] (==) No Layout section.  Using the first Screen section.
[    12.837] (**) |-->Screen "Default Screen" (0)
[    12.837] (**) |   |-->Monitor "<default monitor>"
[    12.838] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    12.838] (==) Automatically adding devices
[    12.838] (==) Automatically enabling devices
[    12.838] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.838]     Entry deleted from font path.
[    12.838] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    12.838] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.838] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.838] (II) Loader magic: 0x81ffde0
[    12.838] (II) Module ABI versions:
[    12.838]     X.Org ANSI C Emulation: 0.4
[    12.838]     X.Org Video Driver: 10.0
[    12.838]     X.Org XInput driver : 12.3
[    12.838]     X.Org Server Extension : 5.0
[    12.838] (--) PCI:*(0:1:0:0) 1002:94c1:1458:2190 rev 0, Mem @ 0xe0000000/268435456, 0xf5000000/65536, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[    12.839] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.839] (II) "extmod" will be loaded by default.
[    12.839] (II) "dbe" will be loaded by default.
[    12.839] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    12.839] (II) "record" will be loaded by default.
[    12.839] (II) "dri" will be loaded by default.
[    12.839] (II) "dri2" will be loaded by default.
[    12.839] (II) LoadModule: "glx"
[    12.839] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    12.839] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    12.839]     compiled for 6.9.0, module version = 1.0.0
[    12.839] (II) Loading extension GLX
[    12.839] (II) LoadModule: "extmod"
[    12.897] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.905] (II) Module extmod: vendor="X.Org Foundation"
[    12.905]     compiled for 1.10.1, module version = 1.0.0
[    12.905]     Module class: X.Org Server Extension
[    12.905]     ABI class: X.Org Server Extension, version 5.0
[    12.905] (II) Loading extension MIT-SCREEN-SAVER
[    12.905] (II) Loading extension XFree86-VidModeExtension
[    12.905] (II) Loading extension XFree86-DGA
[    12.905] (II) Loading extension DPMS
[    12.905] (II) Loading extension XVideo
[    12.905] (II) Loading extension XVideo-MotionCompensation
[    12.905] (II) Loading extension X-Resource
[    12.905] (II) LoadModule: "dbe"
[    12.905] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.905] (II) Module dbe: vendor="X.Org Foundation"
[    12.905]     compiled for 1.10.1, module version = 1.0.0
[    12.905]     Module class: X.Org Server Extension
[    12.905]     ABI class: X.Org Server Extension, version 5.0
[    12.905] (II) Loading extension DOUBLE-BUFFER
[    12.905] (II) LoadModule: "record"
[    12.906] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.906] (II) Module record: vendor="X.Org Foundation"
[    12.906]     compiled for 1.10.1, module version = 1.13.0
[    12.906]     Module class: X.Org Server Extension
[    12.906]     ABI class: X.Org Server Extension, version 5.0
[    12.906] (II) Loading extension RECORD
[    12.906] (II) LoadModule: "dri"
[    12.906] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.906] (II) Module dri: vendor="X.Org Foundation"
[    12.906]     compiled for 1.10.1, module version = 1.0.0
[    12.906]     ABI class: X.Org Server Extension, version 5.0
[    12.906] (II) Loading extension XFree86-DRI
[    12.906] (II) LoadModule: "dri2"
[    12.907] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.907] (II) Module dri2: vendor="X.Org Foundation"
[    12.907]     compiled for 1.10.1, module version = 1.2.0
[    12.907]     ABI class: X.Org Server Extension, version 5.0
[    12.907] (II) Loading extension DRI2
[    12.907] (==) Matched fglrx as autoconfigured driver 0
[    12.907] (==) Matched ati as autoconfigured driver 1
[    12.907] (==) Matched vesa as autoconfigured driver 2
[    12.907] (==) Matched fbdev as autoconfigured driver 3
[    12.907] (==) Assigned the driver to the xf86ConfigLayout
[    12.907] (II) LoadModule: "fglrx"
[    12.907] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    12.920] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    12.920]     compiled for 1.4.99.906, module version = 8.84.60
[    12.920]     Module class: X.Org Video Driver
[    12.920] (II) Loading sub module "fglrxdrm"
[    12.920] (II) LoadModule: "fglrxdrm"
[    12.920] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.920] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.920]     compiled for 1.4.99.906, module version = 8.84.60
[    12.920] (II) LoadModule: "ati"
[    12.921] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.921] (II) Module ati: vendor="X.Org Foundation"
[    12.921]     compiled for 1.10.1, module version = 6.14.0
[    12.921]     Module class: X.Org Video Driver
[    12.921]     ABI class: X.Org Video Driver, version 10.0
[    12.921] (II) LoadModule: "radeon"
[    12.921] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    12.921] (II) Module radeon: vendor="X.Org Foundation"
[    12.921]     compiled for 1.10.1, module version = 6.14.0
[    12.921]     Module class: X.Org Video Driver
[    12.921]     ABI class: X.Org Video Driver, version 10.0
[    12.921] (II) LoadModule: "vesa"
[    12.921] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    12.921] (II) Module vesa: vendor="X.Org Foundation"
[    12.921]     compiled for 1.10.0, module version = 2.3.0
[    12.921]     Module class: X.Org Video Driver
[    12.921]     ABI class: X.Org Video Driver, version 10.0
[    12.921] (II) LoadModule: "fbdev"
[    12.922] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.922] (II) Module fbdev: vendor="X.Org Foundation"
[    12.922]     compiled for 1.10.0, module version = 0.4.2
[    12.922]     ABI class: X.Org Video Driver, version 10.0
[    12.922] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    12.922] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    12.922] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    12.922] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
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
    ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS,
    Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS
[    12.927] (II) VESA: driver for VESA chipsets: vesa
[    12.927] (II) FBDEV: driver for framebuffer: fbdev
[    12.927] (++) using VT number 7

[    12.927] (WW) Falling back to old probe method for fglrx
[    12.959] (II) Loading PCS database from /etc/ati/amdpcsdb
[    12.964] (--) Assigning device section with no busID to primary device
[    12.964] (--) Chipset Supported AMD Graphics Processor (0x94C1) found
[    12.964] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    12.964] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    12.964] (II) AMD Video driver is signed
[    12.965] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    12.965] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.965] (II) fglrx(0): pEnt->device->identifier=0x81ec828
[    12.965] (WW) Falling back to old probe method for vesa
[    12.965] (WW) Falling back to old probe method for fbdev
[    12.965] (II) Loading sub module "fbdevhw"
[    12.965] (II) LoadModule: "fbdevhw"
[    12.965] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.965] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.965]     compiled for 1.10.1, module version = 0.0.2
[    12.965]     ABI class: X.Org Video Driver, version 10.0
[    12.965] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    12.965] (II) Loading sub module "vgahw"
[    12.965] (II) LoadModule: "vgahw"
[    12.966] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    12.966] (II) Module vgahw: vendor="X.Org Foundation"
[    12.966]     compiled for 1.10.1, module version = 0.1.0
[    12.966]     ABI class: X.Org Video Driver, version 10.0
[    12.966] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    12.966] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.966] (==) fglrx(0): Default visual is TrueColor
[    12.966] (==) fglrx(0): RGB weight 888
[    12.966] (II) fglrx(0): Using 8 bits per RGB 
[    12.966] (==) fglrx(0): Buffer Tiling is ON
[    12.966] (II) Loading sub module "fglrxdrm"
[    12.966] (II) LoadModule: "fglrxdrm"
[    12.966] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    12.966] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.966]     compiled for 1.4.99.906, module version = 8.84.60
[    12.967] ukiDynamicMajor: found major device number 250
[    12.967] ukiDynamicMajor: found major device number 250
[    12.967] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    12.967] ukiOpenDevice: node name is /dev/ati/card0
[    12.967] ukiOpenDevice: open result is 11, (OK)
[    12.967] ukiOpenByBusid: ukiOpenMinor returns 11
[    12.967] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.967] (==) fglrx(0): NoAccel = NO
[    12.967] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    12.967] (--) fglrx(0): Chipset: "ATI Radeon HD 2400 XT" (Chipset = 0x94c1)
[    12.967] (--) fglrx(0): (PciSubVendor = 0x1458, PciSubDevice = 0x2190)
[    12.967] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    12.967] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    12.967] (--) fglrx(0): MMIO registers at 0xf5000000
[    12.967] (--) fglrx(0): I/O port at 0x0000b000
[    12.967] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    12.968] (II) fglrx(0): AC Adapter is used
[    12.971] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    12.971] (II) Loading sub module "vbe"
[    12.971] (II) LoadModule: "vbe"
[    12.971] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    12.971] (II) Module vbe: vendor="X.Org Foundation"
[    12.971]     compiled for 1.10.1, module version = 1.1.0
[    12.971]     ABI class: X.Org Video Driver, version 10.0
[    12.971] (II) fglrx(0): VESA BIOS detected
[    12.971] (II) fglrx(0): VESA VBE Version 3.0
[    12.971] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    12.971] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    12.971] (II) fglrx(0): VESA VBE OEM Software Rev: 10.63
[    12.971] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    12.971] (II) fglrx(0): VESA VBE OEM Product: RV610
[    12.971] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    13.010] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    13.010] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
[    13.010] (II) fglrx(0): PCIE card detected
[    13.010] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.010] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.013] (II) fglrx(0): Using adapter: 1:0.0.
[    13.043] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
[    13.070] (II) fglrx(0): Interrupt handler installed at IRQ 47.
[    13.070] (II) fglrx(0): RandR 1.2 support is enabled!
[    13.070] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    13.070] (==) fglrx(0): Center Mode is disabled 
[    13.070] (II) Loading sub module "fb"
[    13.070] (II) LoadModule: "fb"
[    13.070] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.070] (II) Module fb: vendor="X.Org Foundation"
[    13.070]     compiled for 1.10.1, module version = 1.0.0
[    13.070]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.070] (II) Loading sub module "ddc"
[    13.070] (II) LoadModule: "ddc"
[    13.070] (II) Module "ddc" already built-in
[    13.808] (II) fglrx(0): Finished Initialize PPLIB!
[    13.810] (II) fglrx(0): Output DFP1 has no monitor section
[    13.810] (II) fglrx(0): Output CRT1 has no monitor section
[    13.810] (II) fglrx(0): Output CRT2 has no monitor section
[    13.810] (II) fglrx(0): Output TV has no monitor section
[    13.810] (II) fglrx(0): Output CV has no monitor section
[    13.810] (II) Loading sub module "ddc"
[    13.810] (II) LoadModule: "ddc"
[    13.810] (II) Module "ddc" already built-in
[    13.810] (II) fglrx(0): Connected Display0: CRT2
[    13.810] (II) fglrx(0):  Display0: Failed to get EDID information. 
[    13.952] (II) fglrx(0): EDID for output DFP1
[    13.952] (II) fglrx(0): EDID for output CRT1
[    13.952] (II) fglrx(0): Cannot get EDID information for CRT2
[    13.952] (II) fglrx(0): EDID for output CRT2
[    13.953] (II) fglrx(0): Not using mode "640x350" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "640x400" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "720x400" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "640x480" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "640x480" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "800x600" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "800x600" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "800x600" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "848x480" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1024x768i" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1024x768" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1024x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1152x864" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x768" (monitor doesn't support reduced blanking)
[    13.953] (II) fglrx(0): Not using mode "1280x768" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x800" (monitor doesn't support reduced blanking)
[    13.953] (II) fglrx(0): Not using mode "1280x800" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x800" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x960" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x960" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x1024" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1280x1024" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1360x768" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1360x768" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1400x1050" (monitor doesn't support reduced blanking)
[    13.953] (II) fglrx(0): Not using mode "1400x1050" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1400x1050" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1440x900" (monitor doesn't support reduced blanking)
[    13.953] (II) fglrx(0): Not using mode "1440x900" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1440x900" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1600x1200" (unknown reason)
[    13.953] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1600x1200" (vrefresh out of range)
[    13.953] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1680x1050" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1792x1344" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1856x1392" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1200" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "1920x1440" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.953] (II) fglrx(0): Not using mode "2560x1600" (width too large for virtual size)
[    13.953] (II) fglrx(0): Printing probed modes for output CRT2
[    13.953] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 -hsync -vsync (75.0 kHz)
[    13.953] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    13.953] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    13.953] (II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync -vsync (50.9 kHz)
[    13.953] (II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync -vsync (46.3 kHz)
[    13.953] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    13.953] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    13.953] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    13.953] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    13.954] (II) fglrx(0): Modeline "1152x864"x47.0   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync -vsync (43.0 kHz)
[    13.954] (II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync -vsync (39.2 kHz)
[    13.954] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    13.954] (II) fglrx(0): Modeline "1280x768"x56.0   73.89  1280 1336 1472 1664  768 769 772 793 +hsync -vsync (44.4 kHz)
[    13.954] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    13.954] (II) fglrx(0): Modeline "1280x720"x50.0   60.46  1280 1328 1456 1632  720 721 724 741 +hsync -vsync (37.0 kHz)
[    13.954] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    13.954] (II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace -hsync -vsync (35.5 kHz)
[    13.954] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    13.954] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    13.954] (II) fglrx(0): Modeline "800x600"x47.0   29.60  800 816 896 992  600 601 604 635 interlace +hsync -vsync (29.8 kHz)
[    13.954] (II) fglrx(0): Modeline "720x576"x50.0   26.56  720 736 808 896  576 577 580 593 +hsync -vsync (29.6 kHz)
[    13.954] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    13.954] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    13.954] (II) fglrx(0): EDID for output TV
[    13.954] (II) fglrx(0): EDID for output CV
[    13.954] (II) fglrx(0): Output DFP1 disconnected
[    13.954] (II) fglrx(0): Output CRT1 disconnected
[    13.954] (II) fglrx(0): Output CRT2 connected
[    13.954] (II) fglrx(0): Output TV disconnected
[    13.954] (II) fglrx(0): Output CV disconnected
[    13.954] (II) fglrx(0): Using exact sizes for initial modes
[    13.954] (II) fglrx(0): Output CRT2 using initial mode 1600x1200
[    13.954] (II) fglrx(0): DPI set to (96, 96)
[    13.954] (II) fglrx(0): Adapter ATI Radeon HD 2400 XT has 2 configurable heads and 1 displays connected.
[    13.954] (==) fglrx(0):  PseudoColor visuals disabled
[    13.954] (II) Loading sub module "ramdac"
[    13.954] (II) LoadModule: "ramdac"
[    13.954] (II) Module "ramdac" already built-in
[    13.954] (==) fglrx(0): NoDRI = NO
[    13.954] (==) fglrx(0): Capabilities: 0x00000000
[    13.954] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    13.954] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    13.954] (==) fglrx(0): UseFastTLS=0
[    13.954] (==) fglrx(0): BlockSignalsOnLock=1
[    13.954] (II) UnloadModule: "radeon"
[    13.954] (II) Unloading radeon
[    13.954] (II) UnloadModule: "vesa"
[    13.954] (II) Unloading vesa
[    13.954] (II) UnloadModule: "fbdev"
[    13.954] (II) Unloading fbdev
[    13.954] (II) UnloadModule: "fbdevhw"
[    13.954] (II) Unloading fbdevhw
[    13.954] (--) Depth 24 pixmap format is 32 bpp
[    13.954] (II) Loading extension ATIFGLRXDRI
[    13.954] (II) fglrx(0): doing swlDriScreenInit
[    13.954] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    13.954] ukiDynamicMajor: found major device number 250
[    13.954] ukiDynamicMajor: found major device number 250
[    13.954] ukiDynamicMajor: found major device number 250
[    13.954] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.954] ukiOpenDevice: node name is /dev/ati/card0
[    13.954] ukiOpenDevice: open result is 16, (OK)
[    13.954] ukiOpenByBusid: ukiOpenMinor returns 16
[    13.954] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.954] (II) fglrx(0): [uki] DRM interface version 1.0
[    13.954] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    13.955] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    13.955] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb77a1000
[    13.955] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    13.955] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    13.955] (II) fglrx(0): swlDriScreenInit done
[    13.955] (II) fglrx(0): Kernel Module Version Information:
[    13.955] (II) fglrx(0):     Name: fglrx
[    13.955] (II) fglrx(0):     Version: 8.84.60
[    13.955] (II) fglrx(0):     Date: Mar 24 2011
[    13.955] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    13.955] (II) fglrx(0): Kernel Module version matches driver.
[    13.955] (II) fglrx(0): Kernel Module Build Time Information:
[    13.955] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-10-generic
[    13.955] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    13.955] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    13.955] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    13.955] (II) fglrx(0): [uki] register handle = 0x00004000
[    13.969] (II) fglrx(0): DRI initialization successfull
[    13.969] (II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01004000
[    13.970] (==) fglrx(0): Backing store disabled
[    13.970] (II) Loading extension FGLRXEXTENSION
[    13.970] (==) fglrx(0): DPMS enabled
[    13.970] (II) fglrx(0): Initialized in-driver Xinerama extension
[    13.970] (**) fglrx(0): Textured Video is enabled.
[    13.970] (II) LoadModule: "glesx"
[    13.970] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    13.971] (II) Module glesx: vendor="X.Org Foundation"
[    13.971]     compiled for 1.4.99.906, module version = 1.0.0
[    13.971] (II) Loading extension GLESX
[    13.971] (II) fglrx(0): GLESX enableFlags = 528
[    13.971] (II) fglrx(0): GLESX is enabled
[    13.971] (II) LoadModule: "amdxmm"
[    13.971] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    13.971] (II) Module amdxmm: vendor="X.Org Foundation"
[    13.971]     compiled for 1.4.99.906, module version = 2.0.0
[    13.971] (II) Loading extension AMDXVOPL
[    13.971] (II) Loading extension AMDXVBA
[    13.972] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    13.974] (II) fglrx(0): Enable composite support successfully
[    13.974] (II) fglrx(0): X context handle = 0x1
[    13.974] (II) fglrx(0): [DRI] installation complete
[    13.974] (==) fglrx(0): Silken mouse enabled
[    13.974] (==) fglrx(0): Using HW cursor of display infrastructure!
[    13.974] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    13.975] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    13.975] (II) fglrx(0): Cannot set TV horizontal size.
[    13.975] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    13.975] (II) fglrx(0): Cannot set TV horizontal position.
[    13.975] (II) fglrx(0): Cannot set TV vertical position.
[    14.026] (--) RandR disabled
[    14.026] (II) Initializing built-in extension Generic Event Extension
[    14.026] (II) Initializing built-in extension SHAPE
[    14.026] (II) Initializing built-in extension MIT-SHM
[    14.026] (II) Initializing built-in extension XInputExtension
[    14.026] (II) Initializing built-in extension XTEST
[    14.026] (II) Initializing built-in extension BIG-REQUESTS
[    14.026] (II) Initializing built-in extension SYNC
[    14.026] (II) Initializing built-in extension XKEYBOARD
[    14.026] (II) Initializing built-in extension XC-MISC
[    14.026] (II) Initializing built-in extension SECURITY
[    14.026] (II) Initializing built-in extension XINERAMA
[    14.026] (II) Initializing built-in extension XFIXES
[    14.026] (II) Initializing built-in extension RENDER
[    14.026] (II) Initializing built-in extension RANDR
[    14.026] (II) Initializing built-in extension COMPOSITE
[    14.026] (II) Initializing built-in extension DAMAGE
[    14.026] (II) Initializing built-in extension GESTURE
[    14.042] ukiDynamicMajor: found major device number 250
[    14.042] ukiDynamicMajor: found major device number 250
[    14.042] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    14.042] ukiOpenDevice: node name is /dev/ati/card0
[    14.042] ukiOpenDevice: open result is 18, (OK)
[    14.042] ukiOpenByBusid: ukiOpenMinor returns 18
[    14.042] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    14.113] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    14.113] (II) fglrx(0): Enable the clock gating!
[    14.113] (II) fglrx(0): Setting screen physical size to 423 x 317
[    14.127] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.135] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.135] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.135] (II) LoadModule: "evdev"
[    14.135] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.135] (II) Module evdev: vendor="X.Org Foundation"
[    14.135]     compiled for 1.10.0.902, module version = 2.6.0
[    14.135]     Module class: X.Org XInput Driver
[    14.135]     ABI class: X.Org XInput driver, version 12.3
[    14.135] (II) Using input driver 'evdev' for 'Power Button'
[    14.135] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.135] (**) Power Button: always reports core events
[    14.135] (**) Power Button: Device: "/dev/input/event1"
[    14.136] (--) Power Button: Found keys
[    14.136] (II) Power Button: Configuring as keyboard
[    14.136] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.136] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.136] (**) Option "xkb_rules" "evdev"
[    14.136] (**) Option "xkb_model" "pc105"
[    14.136] (**) Option "xkb_layout" "us"
[    14.139] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.139] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.139] (II) Using input driver 'evdev' for 'Power Button'
[    14.139] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.139] (**) Power Button: always reports core events
[    14.139] (**) Power Button: Device: "/dev/input/event0"
[    14.139] (--) Power Button: Found keys
[    14.139] (II) Power Button: Configuring as keyboard
[    14.139] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.139] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    14.139] (**) Option "xkb_rules" "evdev"
[    14.139] (**) Option "xkb_model" "pc105"
[    14.139] (**) Option "xkb_layout" "us"
[    14.140] (II) config/udev: Adding input device Microsoft Microsoft Basic Optical Mouse (/dev/input/event3)
[    14.140] (**) Microsoft Microsoft Basic Optical Mouse: Applying InputClass "evdev pointer catchall"
[    14.140] (II) Using input driver 'evdev' for 'Microsoft Microsoft Basic Optical Mouse'
[    14.140] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.140] (**) Microsoft Microsoft Basic Optical Mouse: always reports core events
[    14.140] (**) Microsoft Microsoft Basic Optical Mouse: Device: "/dev/input/event3"
[    14.141] (--) Microsoft Microsoft Basic Optical Mouse: Found 3 mouse buttons
[    14.141] (--) Microsoft Microsoft Basic Optical Mouse: Found scroll wheel(s)
[    14.141] (--) Microsoft Microsoft Basic Optical Mouse: Found relative axes
[    14.141] (--) Microsoft Microsoft Basic Optical Mouse: Found x and y relative axes
[    14.141] (II) Microsoft Microsoft Basic Optical Mouse: Configuring as mouse
[    14.141] (II) Microsoft Microsoft Basic Optical Mouse: Adding scrollwheel support
[    14.141] (**) Microsoft Microsoft Basic Optical Mouse: YAxisMapping: buttons 4 and 5
[    14.141] (**) Microsoft Microsoft Basic Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.141] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input3/event3"
[    14.141] (II) XINPUT: Adding extended input device "Microsoft Microsoft Basic Optical Mouse" (type: MOUSE)
[    14.141] (II) Microsoft Microsoft Basic Optical Mouse: initialized for relative axes.
[    14.141] (**) Microsoft Microsoft Basic Optical Mouse: (accel) keeping acceleration scheme 1
[    14.141] (**) Microsoft Microsoft Basic Optical Mouse: (accel) acceleration profile 0
[    14.141] (**) Microsoft Microsoft Basic Optical Mouse: (accel) acceleration factor: 2.000
[    14.141] (**) Microsoft Microsoft Basic Optical Mouse: (accel) acceleration threshold: 4
[    14.141] (II) config/udev: Adding input device Microsoft Microsoft Basic Optical Mouse (/dev/input/mouse0)
[    14.141] (II) No input driver/identifier specified (ignoring)
[    14.146] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    14.146] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.146] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    14.146] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.146] (**) AT Translated Set 2 keyboard: always reports core events
[    14.146] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    14.146] (--) AT Translated Set 2 keyboard: Found keys
[    14.146] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    14.146] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    14.146] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    14.146] (**) Option "xkb_rules" "evdev"
[    14.146] (**) Option "xkb_model" "pc105"
[    14.146] (**) Option "xkb_layout" "us"
[    14.173] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    14.490] (II) fglrx(0): Cannot get EDID information for CRT2
[    14.630] (WW) fglrx(0): Cannot get updated TV attributes.
[    14.706] (II) fglrx(0): Cannot get EDID information for CRT2
[    14.846] (WW) fglrx(0): Cannot get updated TV attributes.
[    14.923] (II) fglrx(0): Cannot get EDID information for CRT2
[    15.063] (WW) fglrx(0): Cannot get updated TV attributes.
[    15.141] (II) fglrx(0): Cannot get EDID information for CRT2
[    15.281] (WW) fglrx(0): Cannot get updated TV attributes.
[    28.253] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    28.857] (II) fglrx(0): Cannot get EDID information for CRT2
[    28.997] (WW) fglrx(0): Cannot get updated TV attributes.
[    29.084] (II) fglrx(0): Cannot get EDID information for CRT2
[    29.223] (WW) fglrx(0): Cannot get updated TV attributes.
[    29.300] (II) fglrx(0): Cannot get EDID information for CRT2
[    29.439] (WW) fglrx(0): Cannot get updated TV attributes.
[    29.475] (II) fglrx(0): xdl_xs110_atiddxDisplayScreenEnableDisplays
[    29.874] (WW) fglrx(0): Cannot get updated TV attributes.
[    31.059] (II) fglrx(0): Cannot get EDID information for CRT2
[    31.199] (WW) fglrx(0): Cannot get updated TV attributes.
[    31.202] (WW) fglrx(0): Cannot get updated TV attributes.
[    31.276] (WW) fglrx(0): Cannot get updated TV attributes.
[    37.167] (II) fglrx(0): Cannot get EDID information for CRT2
[    37.308] (WW) fglrx(0): Cannot get updated TV attributes.
[    67.057] (II) fglrx(0): Cannot get EDID information for CRT2
[    67.197] (WW) fglrx(0): Cannot get updated TV attributes.
[   500.758] (II) fglrx(0): Cannot get EDID information for CRT2
[   549.068] (II) fglrx(0): Cannot get EDID information for CRT2
[  1960.533] (II) fglrx(0): Cannot get EDID information for CRT2
[  1960.674] (WW) fglrx(0): Cannot get updated TV attributes.
[  2000.499] (II) fglrx(0): Cannot get EDID information for CRT2
[  2000.640] (WW) fglrx(0): Cannot get updated TV attributes.
[  3487.709] (II) fglrx(0): Cannot get EDID information for CRT2
[  3487.851] (WW) fglrx(0): Cannot get updated TV attributes.
--------------------------------------------------
```

---

### Post by philliplemky on 2011-07-15
realzippy, looks like it's what you expected... It can't get the EDID from the monitor.

---

### Post by realzippy on 2011-07-15
Can you please check the xorg.conf again?
Is it really the current one (whole file) ,not
xorg.conf.backup
or
xorg.conf.failsafe
or something?

---

### Post by philliplemky on 2011-07-15
Double-checked. That's the only xorg.conf I have (in /etc/X11). No other similarly named files.

---

### Post by realzippy on 2011-07-15
Ok.
First make a local backup of xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.strange

```
Then run:

```
sudo aticonfig --initial

```
which should create a new one.
Reboot or restart X server.

*If* something goes wrong,press "shift" during boot,
choose the 1rst recovery mode offered,choose low graphics mode
and post the new xorg.conf
If low graphics mode is not possible,drop to shell instead an run
 
```
sudo mv /etc/X11/xorg.conf.strange /etc/X11/xorg.conf
```

reboot

```
sudo reboot now
```

If nothing goes wrong,check if desired resolution is available now.

---

### Post by philliplemky on 2011-07-15
I did what you said. After I ran sudo aticonfig --initial, I received the following message:

Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using xorg.conf
Saving back-up to xorg.conf.original-0

I restarted anyway. Didn't make a difference. Wasn't able to select native resolution. xorg.conf file looked like this afterward:

--------------------------------------------------
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

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
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
--------------------------------------------------

I tried adding a Modes section to the aticonfig-Screen section, and moved the aticonfig-Screen section ahead of the generic screen section, like so:

--------------------------------------------------
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

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
        Viewport   0 0
        Depth     24
        Modes     "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection
--------------------------------------------------

I restarted and it still didn't make a difference. Wasn't able to select the native resolution in Monitor Settings.

---

### Post by realzippy on 2011-07-15
What does 

```
fglrxinfo
```

say? (just to make sure driver is running)

Have to admit I am not an ATI expert.If it was a nvidia-card,
I would suggest to add valid Hsync Vrefresh values to xorg.conf and 
add a modeline made by "cvt"..
The procedure must be similar with catalyst-xorg.confs...
will check this out before suggesting some editing.

---

### Post by realzippy on 2011-07-15
Try this version (Hsync/Vrefresh added):
```
Section "ServerLayout"
Identifier "aticonfig Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
HorizSync       28.0 - 83.0
VertRefresh     56.0 - 75.0
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1680x1050"
EndSubSection
EndSection

```

Not sure if fglrx supports modelines like:
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
...so not added.
Have to stop for today (around midnight here).
Back tomorrow...

---

### Post by realzippy on 2011-07-16
Just re-read thread and stumbled upon
[I]Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
[/I]
when you ran aticonfig --initial.
Found:
[http://ubuntuforums.org/showthread.php?t=1742724](http://ubuntuforums.org/showthread.php?t=1742724)
Anyway run 
```
fglrxinfo
```
to prove this.

---

