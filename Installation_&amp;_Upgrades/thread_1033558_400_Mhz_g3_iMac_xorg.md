---
title: "400 Mhz g3 iMac xorg"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by smkeesle on 2009-01-07
I am getting an error when I start x (No drivers available.) on a PowerPC Intrepid install using the alternate CD.

Here is my xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies Inc Rage 128 Pro Ultra TR"
        Driver          "ati"
        BusID           "PCI:0:10:0"
        Option          "UseFBDev"              "false"
EndSection


Section "Monitor"
        Identifier      "iMac"
        Option          "DPMS"
        HorizSync       58-60
         VertRefresh    50-70

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Rage 128 Pro Ultra TR"
        Monitor         "iMac"
        DefaultDepth    24
        SubSection "Display"
                Modes   "1027x768" "800x600" "640x480"
        EndSubSection
EndSection

```

and the error log:
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux ibeximac 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 24 October 2008  08:07:47AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@ross.buildd) 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  7 13:18:43 2009
(++) Using config file: "/home/smkeesle/xorg.conf.test"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "iMac"
(**) |   |-->Device "ATI Technologies Inc Rage 128 Pro Ultra TR"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0@0:16:0) ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
        [0] -1  2       0xffffffff - 0x00000000 (0xffffffff) MX[B]
        [1] -1  2       0xffffffff - 0x00000000 (0xf0000) MX[B]
        [2] -1  2       0xffffffff - 0x00000000 (0xc0000) MX[B]
        [3] -1  2       0xffffffff - 0x00000000 (0x0) MX[B]
        [4] -1  1       0xffffffff - 0x00000000 (0xffffffff) MX[B]
        [5] -1  1       0xffffffff - 0x00000000 (0xf0000) MX[B]
        [6] -1  1       0xffffffff - 0x00000000 (0xc0000) MX[B]
        [7] -1  1       0xffffffff - 0x00000000 (0x0) MX[B]
        [8] -1  0       0xffffffff - 0x00000000 (0xffffffff) MX[B]
        [9] -1  0       0xffffffff - 0x00000000 (0xf0000) MX[B]
        [10] -1 0       0xffffffff - 0x00000000 (0xc0000) MX[B]
        [11] -1 0       0xffffffff - 0x00000000 (0x0) MX[B]
        [12] -1 2       0xffffffff - 0x00000000 (0xffff) IX[B]
        [13] -1 2       0xffffffff - 0x00000000 (0x0) IX[B]
        [14] -1 1       0xffffffff - 0x00000000 (0xffff) IX[B]
        [15] -1 1       0xffffffff - 0x00000000 (0x0) IX[B]
        [16] -1 0       0xffffffff - 0x00000000 (0xffff) IX[B]
        [17] -1 0       0xffffffff - 0x00000000 (0x0) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.2, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 6.9.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(EE) No drivers available.

Fatal server error:
no screens found

```

---

### Post by stream303 on 2009-01-07
The horizontal and vertical video frequencies are wrong for that iMac.  See this ubuntu wiki to change the values:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

And be sure to disable dri and glx.  It might be likely that you'll want to specify "r128" as your video driver.

Head on over to the Apple forum and maybe we can get you up and running faster...

---

### Post by smkeesle on 2009-01-07
Alright...maybe over one hurdle...

Now I get a message that "No devices detected".

Assuming that it can't find my ATI card.
lspci shows my Display controller has a bus id of 0000:00:10.0

and my Device section of the xorg.conf file:
```
Section "Device"
        Identifier      "ATI Technologies Inc Rage 128 Pro Ultra TR"
        Driver          "r128"
        BusID           "PCI:0:0:10.0"
        Option          "UseFBDev"              "false"
EndSection
```

From the bottom of my log:
```
        ABI class: X.Org XInput driver, version 2.1
(II) R128: Driver for ATI Rage 128 chipsets:
        ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
        ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
        ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
        ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
        ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
        ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
        ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
        ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
        ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
        ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
        ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
        ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
        ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
        ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
        ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
        ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
        ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
        ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
        ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
        ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
        ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
        ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
        ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
        ATI Rage 128 Pro ULTRA TU (AGP?)
(II) Primary Device is: PCI 00@00:10:0
(EE) No devices detected.
```

---

### Post by avtolle on 2009-01-07
You might want to try "16" in place of "10" (10 being hex for 16 in decimal) on the Bus ID.

---

### Post by smkeesle on 2009-01-07
I can change the value of the BusID to anything string at all and it seems to have no effect. 

It ALWAYS says: 
(II) Primary Device is: PCI 00@00:10:0  <-- no matter what string I specify
(EE) No devices detected

---

### Post by emgaron on 2009-07-17
Have you ever found out more about this? I just filed a bug report in launchpad for this very problem (even same machine type): [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/400864](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/400864) :(
If you have anything to add to that bug report, please do - maybe we can get this resolved.

---

