---
title: "Please help me make xorg.conf"
date: 2011-03-07
forum: Hardware
---

### Post by hreichgott on 2011-03-07
Hi,

I just got an Acer Aspire laptop with ATI 9802 graphics card.
The driver Linux is using by default displays the wrong resolution: 1024x768 only. It's the wrong aspect ratio and everything looks squashed and stretched. No additional options in System > Preferences > Monitors. 
If I enable the AMD proprietary driver, I get the correct 1366x768 resolution, but an annoying "unsupported hardware" watermark on the screen.

According to another user on this thread ([http://ubuntuforums.org/showthread.php?p=10517964](http://ubuntuforums.org/showthread.php?p=10517964)) I have the correct open-source radeon driver installed, but X is not using it. I do not have an xorg.conf file right now, and would like to know how to create one that will tell X to use the radeon driver with 1366x768 resolution.

thanks
hreichgott

---

### Post by khelben1979 on 2011-03-07
```
sudo Xorg -configure
```

---

### Post by fjgaude on 2011-03-07
I wonder what that command does if you are running Ubuntu 10.10?

---

### Post by Yellow Pasque on 2011-03-07
What video card do you have?
```
lspci -vv
```
/var/log/Xorg.0.log might help too

---

### Post by hreichgott on 2011-03-07
^ Temujin helped me before and got me to the point of understanding I needed to create xorg.conf!

khelben1979 and fjgaude, turns out sudo Xorg -configure gives a fatal server error. Joy. Says "server is already active for display 0"

Here is the portion of lspci -vv that deals with the graphics card
```
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802 (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0520
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at 80000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at 4000 [size=256]
    Region 2: Memory at 90500000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v2) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Not Supported, TimeoutDis-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [100 v1] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>

```

---

### Post by Afishionado on 2011-03-08
As fjgaude pointed out, "Xorg -configure" may not be very helpful under recent versions of Ubuntu. The new Xorg has migrated away from using xorg.conf, and I'm pretty lost trying to debug problems without it. :(

Can you post the file /var/log/Xorg.0.log like Temujin asked? That log will tell you what drivers Xorg is trying to use, and (hopefully) how they failed.

**If** you are feeling brave, you can still play with "Xorg -configure", but you'll have to kill the instance of Xorg that's already running. (Xorg is what lets you have windows and a point-and-click interface on Linux. If you kill it, you'll be trapped at the command line.)

To kill it (again, **if** you're feeling brave) run *sudo /etc/init.d/gdm stop* (substitute "kdm" for "gdm" if you run Kubuntu). (This will kill whatever web browser you have open, so write everything down first!)

After you're done fiddling, you can bring your desktop back with *sudo /etc/init.d/gdm start* (again, substitute "kdm" for "gdm" if you run Kubuntu). (Or, if you panic, just run *reboot*. :) )

---

### Post by khelben1979 on 2011-03-08
[Xorg.conf in Ubuntu 10.10 docs]("http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there") - askubuntu.com.

---

### Post by hreichgott on 2011-03-08
Here is Xorg.0.log

```
[    14.871] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.871] X Protocol Version 11, Revision 0
[    14.871] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    14.871] Current Operating System: Linux Data 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[    14.871] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=8769c21a-9b5e-4e6b-8ddf-22882e559d6e ro quiet splash
[    14.871] Build Date: 09 January 2011  12:14:58PM
[    14.871] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    14.871] Current version of pixman: 0.18.4
[    14.871]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.871] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.872] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  8 11:11:30 2011
[    14.882] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.882] (==) No Layout section.  Using the first Screen section.
[    14.882] (==) No screen section available. Using defaults.
[    14.882] (**) |-->Screen "Default Screen Section" (0)
[    14.882] (**) |   |-->Monitor "<default monitor>"
[    14.882] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.883] (==) Automatically adding devices
[    14.883] (==) Automatically enabling devices
[    14.883] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.883]     Entry deleted from font path.
[    14.883] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.883] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.883] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.883] (II) Loader magic: 0x81f9b00
[    14.883] (II) Module ABI versions:
[    14.883]     X.Org ANSI C Emulation: 0.4
[    14.883]     X.Org Video Driver: 8.0
[    14.883]     X.Org XInput driver : 11.0
[    14.883]     X.Org Server Extension : 4.0
[    14.885] (--) PCI:*(0:0:1:0) 1002:9802:1025:0520 rev 0, Mem @ 0x80000000/268435456, 0x90500000/262144, I/O @ 0x00004000/256
[    14.885] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.885] (II) LoadModule: "extmod"
[    14.911] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.911] (II) Module extmod: vendor="X.Org Foundation"
[    14.911]     compiled for 1.9.0, module version = 1.0.0
[    14.911]     Module class: X.Org Server Extension
[    14.911]     ABI class: X.Org Server Extension, version 4.0
[    14.912] (II) Loading extension MIT-SCREEN-SAVER
[    14.912] (II) Loading extension XFree86-VidModeExtension
[    14.912] (II) Loading extension XFree86-DGA
[    14.912] (II) Loading extension DPMS
[    14.912] (II) Loading extension XVideo
[    14.912] (II) Loading extension XVideo-MotionCompensation
[    14.912] (II) Loading extension X-Resource
[    14.912] (II) LoadModule: "dbe"
[    14.912] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.912] (II) Module dbe: vendor="X.Org Foundation"
[    14.912]     compiled for 1.9.0, module version = 1.0.0
[    14.912]     Module class: X.Org Server Extension
[    14.912]     ABI class: X.Org Server Extension, version 4.0
[    14.913] (II) Loading extension DOUBLE-BUFFER
[    14.913] (II) LoadModule: "glx"
[    14.913] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.913] (II) Module glx: vendor="X.Org Foundation"
[    14.913]     compiled for 1.9.0, module version = 1.0.0
[    14.913]     ABI class: X.Org Server Extension, version 4.0
[    14.913] (==) AIGLX enabled
[    14.913] (II) Loading extension GLX
[    14.913] (II) LoadModule: "record"
[    14.914] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.914] (II) Module record: vendor="X.Org Foundation"
[    14.914]     compiled for 1.9.0, module version = 1.13.0
[    14.914]     Module class: X.Org Server Extension
[    14.914]     ABI class: X.Org Server Extension, version 4.0
[    14.914] (II) Loading extension RECORD
[    14.914] (II) LoadModule: "dri"
[    14.915] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.915] (II) Module dri: vendor="X.Org Foundation"
[    14.915]     compiled for 1.9.0, module version = 1.0.0
[    14.915]     ABI class: X.Org Server Extension, version 4.0
[    14.915] (II) Loading extension XFree86-DRI
[    14.915] (II) LoadModule: "dri2"
[    14.916] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.916] (II) Module dri2: vendor="X.Org Foundation"
[    14.916]     compiled for 1.9.0, module version = 1.2.0
[    14.916]     ABI class: X.Org Server Extension, version 4.0
[    14.916] (II) Loading extension DRI2
[    14.916] (==) Matched ati as autoconfigured driver 0
[    14.916] (==) Matched vesa as autoconfigured driver 1
[    14.916] (==) Matched fbdev as autoconfigured driver 2
[    14.916] (==) Assigned the driver to the xf86ConfigLayout
[    14.916] (II) LoadModule: "ati"
[    14.917] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    14.917] (II) Module ati: vendor="X.Org Foundation"
[    14.917]     compiled for 1.9.0, module version = 6.13.2
[    14.917]     Module class: X.Org Video Driver
[    14.917]     ABI class: X.Org Video Driver, version 8.0
[    14.917] (II) LoadModule: "radeon"
[    14.917] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.917] (II) Module radeon: vendor="X.Org Foundation"
[    14.917]     compiled for 1.9.0, module version = 6.13.2
[    14.917]     Module class: X.Org Video Driver
[    14.918]     ABI class: X.Org Video Driver, version 8.0
[    14.918] (II) LoadModule: "vesa"
[    14.918] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.918] (II) Module vesa: vendor="X.Org Foundation"
[    14.918]     compiled for 1.8.99.905, module version = 2.3.0
[    14.918]     Module class: X.Org Video Driver
[    14.918]     ABI class: X.Org Video Driver, version 8.0
[    14.918] (II) LoadModule: "fbdev"
[    14.918] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.918] (II) Module fbdev: vendor="X.Org Foundation"
[    14.918]     compiled for 1.8.99.905, module version = 0.4.2
[    14.919]     ABI class: X.Org Video Driver, version 8.0
[    14.919] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
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
    ATI Radeon HD 5450, CEDAR
[    14.930] (II) VESA: driver for VESA chipsets: vesa
[    14.930] (II) FBDEV: driver for framebuffer: fbdev
[    14.930] (++) using VT number 7

[    14.931] (WW) Falling back to old probe method for fbdev
[    14.931] (II) Loading sub module "fbdevhw"
[    14.931] (II) LoadModule: "fbdevhw"
[    14.931] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.932] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.932]     compiled for 1.9.0, module version = 0.0.2
[    14.932]     ABI class: X.Org Video Driver, version 8.0
[    14.932] (EE) open /dev/fb0: No such file or directory
[    14.932] (II) Loading sub module "vbe"
[    14.932] (II) LoadModule: "vbe"
[    14.932] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.932] (II) Module vbe: vendor="X.Org Foundation"
[    14.933]     compiled for 1.9.0, module version = 1.1.0
[    14.933]     ABI class: X.Org Video Driver, version 8.0
[    14.933] (II) Loading sub module "int10"
[    14.933] (II) LoadModule: "int10"
[    14.933] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.933] (II) Module int10: vendor="X.Org Foundation"
[    14.933]     compiled for 1.9.0, module version = 1.0.0
[    14.933]     ABI class: X.Org Video Driver, version 8.0
[    14.933] (II) VESA(0): initializing int10
[    14.939] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.940] (II) VESA(0): VESA BIOS detected
[    14.940] (II) VESA(0): VESA VBE Version 3.0
[    14.940] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    14.940] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    14.940] (II) VESA(0): VESA VBE OEM Software Rev: 12.37
[    14.940] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    14.940] (II) VESA(0): VESA VBE OEM Product: WRESTLER
[    14.940] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    15.009] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    15.009] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    15.009] (==) VESA(0): RGB weight 888
[    15.009] (==) VESA(0): Default visual is TrueColor
[    15.009] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.009] (II) Loading sub module "ddc"
[    15.009] (II) LoadModule: "ddc"
[    15.009] (II) Module "ddc" already built-in
[    15.009] (II) VESA(0): VESA VBE DDC supported
[    15.009] (II) VESA(0): VESA VBE DDC Level 2
[    15.009] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    15.277] (II) VESA(0): VESA VBE DDC read successfully
[    15.277] (II) VESA(0): Manufacturer: LGD  Model: 250  Serial#: 0
[    15.278] (II) VESA(0): Year: 2010  Week: 0
[    15.278] (II) VESA(0): EDID Version: 1.3
[    15.278] (II) VESA(0): Digital Display Input
[    15.278] (II) VESA(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    15.278] (II) VESA(0): Gamma: 2.20
[    15.278] (II) VESA(0): No DPMS capabilities specified
[    15.278] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.278] (II) VESA(0): First detailed timing is preferred mode
[    15.278] (II) VESA(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[    15.278] (II) VESA(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[    15.278] (II) VESA(0): Manufacturer's mask: 0
[    15.278] (II) VESA(0): Supported detailed timing:
[    15.278] (II) VESA(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[    15.278] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    15.278] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    15.278] (II) VESA(0):  LG Display
[    15.278] (II) VESA(0):  LP156WH2-TLEA
[    15.278] (II) VESA(0): EDID (in hex):
[    15.278] (II) VESA(0):     00ffffffffffff0030e4500200000000
[    15.278] (II) VESA(0):     00140103802313780ac2d59c60559e26
[    15.278] (II) VESA(0):     19505400000001010101010101010101
[    15.278] (II) VESA(0):     0101010101013e1c56a0500016303020
[    15.278] (II) VESA(0):     350059c2100000190000000000000000
[    15.278] (II) VESA(0):     00000000000000000000000000fe004c
[    15.278] (II) VESA(0):     4720446973706c61790a2020000000fe
[    15.278] (II) VESA(0):     004c503135365748322d544c454100fd
[    15.278] (II) VESA(0): EDID vendor "LGD", prod id 592
[    15.278] (II) VESA(0): Printing DDC gathered Modelines:
[    15.278] (II) VESA(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    15.278] (II) VESA(0): Searching for matching VESA mode(s):
[    15.280] Mode: 100 (640x400)
[    15.280]     ModeAttributes: 0xbb
[    15.280]     WinAAttributes: 0x7
[    15.280]     WinBAttributes: 0x0
[    15.280]     WinGranularity: 64
[    15.280]     WinSize: 64
[    15.280]     WinASegment: 0xa000
[    15.280]     WinBSegment: 0x0
[    15.280]     WinFuncPtr: 0xc0005543
[    15.280]     BytesPerScanline: 640
[    15.280]     XResolution: 640
[    15.280]     YResolution: 400
[    15.280]     XCharSize: 8
[    15.280]     YCharSize: 16
[    15.280]     NumberOfPlanes: 1
[    15.280]     BitsPerPixel: 8
[    15.280]     NumberOfBanks: 1
[    15.280]     MemoryModel: 4
[    15.280]     BankSize: 0
[    15.280]     NumberOfImages: 63
[    15.280]     RedMaskSize: 0
[    15.280]     RedFieldPosition: 0
[    15.280]     GreenMaskSize: 0
[    15.280]     GreenFieldPosition: 0
[    15.280]     BlueMaskSize: 0
[    15.280]     BlueFieldPosition: 0
[    15.280]     RsvdMaskSize: 0
[    15.280]     RsvdFieldPosition: 0
[    15.280]     DirectColorModeInfo: 0
[    15.280]     PhysBasePtr: 0x80000000
[    15.280]     LinBytesPerScanLine: 640
[    15.280]     BnkNumberOfImagePages: 63
[    15.280]     LinNumberOfImagePages: 63
[    15.280]     LinRedMaskSize: 0
[    15.280]     LinRedFieldPosition: 0
[    15.280]     LinGreenMaskSize: 0
[    15.280]     LinGreenFieldPosition: 0
[    15.280]     LinBlueMaskSize: 0
[    15.280]     LinBlueFieldPosition: 0
[    15.280]     LinRsvdMaskSize: 0
[    15.280]     LinRsvdFieldPosition: 0
[    15.280]     MaxPixelClock: 400000000
[    15.281] Mode: 101 (640x480)
[    15.281]     ModeAttributes: 0xbb
[    15.281]     WinAAttributes: 0x7
[    15.281]     WinBAttributes: 0x0
[    15.281]     WinGranularity: 64
[    15.281]     WinSize: 64
[    15.281]     WinASegment: 0xa000
[    15.281]     WinBSegment: 0x0
[    15.281]     WinFuncPtr: 0xc0005543
[    15.281]     BytesPerScanline: 640
[    15.281]     XResolution: 640
[    15.281]     YResolution: 480
[    15.281]     XCharSize: 8
[    15.282]     YCharSize: 16
[    15.282]     NumberOfPlanes: 1
[    15.282]     BitsPerPixel: 8
[    15.282]     NumberOfBanks: 1
[    15.282]     MemoryModel: 4
[    15.282]     BankSize: 0
[    15.282]     NumberOfImages: 50
[    15.282]     RedMaskSize: 0
[    15.282]     RedFieldPosition: 0
[    15.282]     GreenMaskSize: 0
[    15.282]     GreenFieldPosition: 0
[    15.282]     BlueMaskSize: 0
[    15.282]     BlueFieldPosition: 0
[    15.282]     RsvdMaskSize: 0
[    15.282]     RsvdFieldPosition: 0
[    15.282]     DirectColorModeInfo: 0
[    15.282]     PhysBasePtr: 0x80000000
[    15.282]     LinBytesPerScanLine: 640
[    15.282]     BnkNumberOfImagePages: 50
[    15.282]     LinNumberOfImagePages: 50
[    15.282]     LinRedMaskSize: 0
[    15.282]     LinRedFieldPosition: 0
[    15.282]     LinGreenMaskSize: 0
[    15.282]     LinGreenFieldPosition: 0
[    15.282]     LinBlueMaskSize: 0
[    15.282]     LinBlueFieldPosition: 0
[    15.282]     LinRsvdMaskSize: 0
[    15.282]     LinRsvdFieldPosition: 0
[    15.282]     MaxPixelClock: 400000000
[    15.283] Mode: 103 (800x600)
[    15.283]     ModeAttributes: 0xbb
[    15.283]     WinAAttributes: 0x7
[    15.283]     WinBAttributes: 0x0
[    15.283]     WinGranularity: 64
[    15.283]     WinSize: 64
[    15.283]     WinASegment: 0xa000
[    15.283]     WinBSegment: 0x0
[    15.283]     WinFuncPtr: 0xc0005543
[    15.283]     BytesPerScanline: 832
[    15.283]     XResolution: 800
[    15.283]     YResolution: 600
[    15.283]     XCharSize: 8
[    15.283]     YCharSize: 14
[    15.283]     NumberOfPlanes: 1
[    15.283]     BitsPerPixel: 8
[    15.283]     NumberOfBanks: 1
[    15.283]     MemoryModel: 4
[    15.283]     BankSize: 0
[    15.283]     NumberOfImages: 31
[    15.283]     RedMaskSize: 0
[    15.283]     RedFieldPosition: 0
[    15.283]     GreenMaskSize: 0
[    15.283]     GreenFieldPosition: 0
[    15.283]     BlueMaskSize: 0
[    15.283]     BlueFieldPosition: 0
[    15.283]     RsvdMaskSize: 0
[    15.283]     RsvdFieldPosition: 0
[    15.283]     DirectColorModeInfo: 0
[    15.283]     PhysBasePtr: 0x80000000
[    15.284]     LinBytesPerScanLine: 832
[    15.284]     BnkNumberOfImagePages: 31
[    15.284]     LinNumberOfImagePages: 31
[    15.284]     LinRedMaskSize: 0
[    15.284]     LinRedFieldPosition: 0
[    15.284]     LinGreenMaskSize: 0
[    15.284]     LinGreenFieldPosition: 0
[    15.284]     LinBlueMaskSize: 0
[    15.284]     LinBlueFieldPosition: 0
[    15.284]     LinRsvdMaskSize: 0
[    15.284]     LinRsvdFieldPosition: 0
[    15.284]     MaxPixelClock: 400000000
[    15.285] Mode: 105 (1024x768)
[    15.285]     ModeAttributes: 0xbb
[    15.285]     WinAAttributes: 0x7
[    15.285]     WinBAttributes: 0x0
[    15.285]     WinGranularity: 64
[    15.285]     WinSize: 64
[    15.285]     WinASegment: 0xa000
[    15.285]     WinBSegment: 0x0
[    15.285]     WinFuncPtr: 0xc0005543
[    15.285]     BytesPerScanline: 1024
[    15.285]     XResolution: 1024
[    15.285]     YResolution: 768
[    15.285]     XCharSize: 8
[    15.285]     YCharSize: 16
[    15.285]     NumberOfPlanes: 1
[    15.285]     BitsPerPixel: 8
[    15.285]     NumberOfBanks: 1
[    15.285]     MemoryModel: 4
[    15.285]     BankSize: 0
[    15.285]     NumberOfImages: 18
[    15.285]     RedMaskSize: 0
[    15.285]     RedFieldPosition: 0
[    15.285]     GreenMaskSize: 0
[    15.285]     GreenFieldPosition: 0
[    15.285]     BlueMaskSize: 0
[    15.285]     BlueFieldPosition: 0
[    15.285]     RsvdMaskSize: 0
[    15.285]     RsvdFieldPosition: 0
[    15.285]     DirectColorModeInfo: 0
[    15.285]     PhysBasePtr: 0x80000000
[    15.285]     LinBytesPerScanLine: 1024
[    15.285]     BnkNumberOfImagePages: 18
[    15.285]     LinNumberOfImagePages: 18
[    15.285]     LinRedMaskSize: 0
[    15.285]     LinRedFieldPosition: 0
[    15.285]     LinGreenMaskSize: 0
[    15.285]     LinGreenFieldPosition: 0
[    15.285]     LinBlueMaskSize: 0
[    15.285]     LinBlueFieldPosition: 0
[    15.285]     LinRsvdMaskSize: 0
[    15.285]     LinRsvdFieldPosition: 0
[    15.285]     MaxPixelClock: 400000000
[    15.287] Mode: 107 (1280x1024)
[    15.287]     ModeAttributes: 0xba
[    15.287]     WinAAttributes: 0x7
[    15.287]     WinBAttributes: 0x0
[    15.287]     WinGranularity: 64
[    15.287]     WinSize: 64
[    15.287]     WinASegment: 0xa000
[    15.287]     WinBSegment: 0x0
[    15.287]     WinFuncPtr: 0xc0005543
[    15.287]     BytesPerScanline: 1280
[    15.287]     XResolution: 1280
[    15.287]     YResolution: 1024
[    15.287]     XCharSize: 8
[    15.287]     YCharSize: 16
[    15.287]     NumberOfPlanes: 1
[    15.287]     BitsPerPixel: 8
[    15.287]     NumberOfBanks: 1
[    15.287]     MemoryModel: 4
[    15.287]     BankSize: 0
[    15.287]     NumberOfImages: 11
[    15.287]     RedMaskSize: 0
[    15.287]     RedFieldPosition: 0
[    15.287]     GreenMaskSize: 0
[    15.287]     GreenFieldPosition: 0
[    15.287]     BlueMaskSize: 0
[    15.287]     BlueFieldPosition: 0
[    15.287]     RsvdMaskSize: 0
[    15.287]     RsvdFieldPosition: 0
[    15.287]     DirectColorModeInfo: 0
[    15.287]     PhysBasePtr: 0x80000000
[    15.287]     LinBytesPerScanLine: 1280
[    15.287]     BnkNumberOfImagePages: 11
[    15.287]     LinNumberOfImagePages: 11
[    15.287]     LinRedMaskSize: 0
[    15.287]     LinRedFieldPosition: 0
[    15.287]     LinGreenMaskSize: 0
[    15.287]     LinGreenFieldPosition: 0
[    15.287]     LinBlueMaskSize: 0
[    15.287]     LinBlueFieldPosition: 0
[    15.287]     LinRsvdMaskSize: 0
[    15.287]     LinRsvdFieldPosition: 0
[    15.287]     MaxPixelClock: 400000000
[    15.288] Mode: 110 (640x480)
[    15.288]     ModeAttributes: 0xbb
[    15.288]     WinAAttributes: 0x7
[    15.288]     WinBAttributes: 0x0
[    15.288]     WinGranularity: 64
[    15.288]     WinSize: 64
[    15.288]     WinASegment: 0xa000
[    15.288]     WinBSegment: 0x0
[    15.288]     WinFuncPtr: 0xc0005543
[    15.289]     BytesPerScanline: 1280
[    15.289]     XResolution: 640
[    15.289]     YResolution: 480
[    15.289]     XCharSize: 8
[    15.289]     YCharSize: 16
[    15.289]     NumberOfPlanes: 1
[    15.289]     BitsPerPixel: 16
[    15.289]     NumberOfBanks: 1
[    15.289]     MemoryModel: 6
[    15.289]     BankSize: 0
[    15.289]     NumberOfImages: 24
[    15.289]     RedMaskSize: 5
[    15.289]     RedFieldPosition: 10
[    15.289]     GreenMaskSize: 5
[    15.289]     GreenFieldPosition: 5
[    15.289]     BlueMaskSize: 5
[    15.289]     BlueFieldPosition: 0
[    15.289]     RsvdMaskSize: 0
[    15.289]     RsvdFieldPosition: 0
[    15.289]     DirectColorModeInfo: 0
[    15.289]     PhysBasePtr: 0x80000000
[    15.289]     LinBytesPerScanLine: 1280
[    15.289]     BnkNumberOfImagePages: 24
[    15.289]     LinNumberOfImagePages: 24
[    15.289]     LinRedMaskSize: 5
[    15.289]     LinRedFieldPosition: 10
[    15.289]     LinGreenMaskSize: 5
[    15.289]     LinGreenFieldPosition: 5
[    15.289]     LinBlueMaskSize: 5
[    15.289]     LinBlueFieldPosition: 0
[    15.289]     LinRsvdMaskSize: 0
[    15.289]     LinRsvdFieldPosition: 0
[    15.289]     MaxPixelClock: 400000000
[    15.290] Mode: 111 (640x480)
[    15.290]     ModeAttributes: 0xbb
[    15.290]     WinAAttributes: 0x7
[    15.290]     WinBAttributes: 0x0
[    15.290]     WinGranularity: 64
[    15.290]     WinSize: 64
[    15.290]     WinASegment: 0xa000
[    15.290]     WinBSegment: 0x0
[    15.290]     WinFuncPtr: 0xc0005543
[    15.290]     BytesPerScanline: 1280
[    15.290]     XResolution: 640
[    15.290]     YResolution: 480
[    15.290]     XCharSize: 8
[    15.290]     YCharSize: 16
[    15.290]     NumberOfPlanes: 1
[    15.290]     BitsPerPixel: 16
[    15.290]     NumberOfBanks: 1
[    15.290]     MemoryModel: 6
[    15.290]     BankSize: 0
[    15.290]     NumberOfImages: 24
[    15.290]     RedMaskSize: 5
[    15.290]     RedFieldPosition: 11
[    15.291]     GreenMaskSize: 6
[    15.291]     GreenFieldPosition: 5
[    15.291]     BlueMaskSize: 5
[    15.291]     BlueFieldPosition: 0
[    15.291]     RsvdMaskSize: 0
[    15.291]     RsvdFieldPosition: 0
[    15.291]     DirectColorModeInfo: 0
[    15.291]     PhysBasePtr: 0x80000000
[    15.291]     LinBytesPerScanLine: 1280
[    15.291]     BnkNumberOfImagePages: 24
[    15.291]     LinNumberOfImagePages: 24
[    15.291]     LinRedMaskSize: 5
[    15.291]     LinRedFieldPosition: 11
[    15.291]     LinGreenMaskSize: 6
[    15.291]     LinGreenFieldPosition: 5
[    15.291]     LinBlueMaskSize: 5
[    15.291]     LinBlueFieldPosition: 0
[    15.291]     LinRsvdMaskSize: 0
[    15.291]     LinRsvdFieldPosition: 0
[    15.291]     MaxPixelClock: 400000000
[    15.292] Mode: 113 (800x600)
[    15.292]     ModeAttributes: 0xbb
[    15.292]     WinAAttributes: 0x7
[    15.292]     WinBAttributes: 0x0
[    15.292]     WinGranularity: 64
[    15.292]     WinSize: 64
[    15.292]     WinASegment: 0xa000
[    15.292]     WinBSegment: 0x0
[    15.292]     WinFuncPtr: 0xc0005543
[    15.292]     BytesPerScanline: 1600
[    15.292]     XResolution: 800
[    15.292]     YResolution: 600
[    15.292]     XCharSize: 8
[    15.292]     YCharSize: 14
[    15.292]     NumberOfPlanes: 1
[    15.292]     BitsPerPixel: 16
[    15.292]     NumberOfBanks: 1
[    15.292]     MemoryModel: 6
[    15.292]     BankSize: 0
[    15.292]     NumberOfImages: 16
[    15.292]     RedMaskSize: 5
[    15.292]     RedFieldPosition: 10
[    15.292]     GreenMaskSize: 5
[    15.292]     GreenFieldPosition: 5
[    15.292]     BlueMaskSize: 5
[    15.292]     BlueFieldPosition: 0
[    15.292]     RsvdMaskSize: 0
[    15.292]     RsvdFieldPosition: 0
[    15.292]     DirectColorModeInfo: 0
[    15.292]     PhysBasePtr: 0x80000000
[    15.293]     LinBytesPerScanLine: 1600
[    15.293]     BnkNumberOfImagePages: 16
[    15.293]     LinNumberOfImagePages: 16
[    15.293]     LinRedMaskSize: 5
[    15.293]     LinRedFieldPosition: 10
[    15.293]     LinGreenMaskSize: 5
[    15.293]     LinGreenFieldPosition: 5
[    15.293]     LinBlueMaskSize: 5
[    15.293]     LinBlueFieldPosition: 0
[    15.293]     LinRsvdMaskSize: 0
[    15.293]     LinRsvdFieldPosition: 0
[    15.293]     MaxPixelClock: 400000000
[    15.294] Mode: 114 (800x600)
[    15.294]     ModeAttributes: 0xbb
[    15.294]     WinAAttributes: 0x7
[    15.294]     WinBAttributes: 0x0
[    15.294]     WinGranularity: 64
[    15.294]     WinSize: 64
[    15.294]     WinASegment: 0xa000
[    15.294]     WinBSegment: 0x0
[    15.294]     WinFuncPtr: 0xc0005543
[    15.294]     BytesPerScanline: 1600
[    15.294]     XResolution: 800
[    15.294]     YResolution: 600
[    15.294]     XCharSize: 8
[    15.294]     YCharSize: 14
[    15.294]     NumberOfPlanes: 1
[    15.294]     BitsPerPixel: 16
[    15.294]     NumberOfBanks: 1
[    15.294]     MemoryModel: 6
[    15.294]     BankSize: 0
[    15.294]     NumberOfImages: 16
[    15.294]     RedMaskSize: 5
[    15.294]     RedFieldPosition: 11
[    15.294]     GreenMaskSize: 6
[    15.294]     GreenFieldPosition: 5
[    15.294]     BlueMaskSize: 5
[    15.294]     BlueFieldPosition: 0
[    15.294]     RsvdMaskSize: 0
[    15.294]     RsvdFieldPosition: 0
[    15.294]     DirectColorModeInfo: 0
[    15.294]     PhysBasePtr: 0x80000000
[    15.294]     LinBytesPerScanLine: 1600
[    15.294]     BnkNumberOfImagePages: 16
[    15.294]     LinNumberOfImagePages: 16
[    15.294]     LinRedMaskSize: 5
[    15.294]     LinRedFieldPosition: 11
[    15.294]     LinGreenMaskSize: 6
[    15.294]     LinGreenFieldPosition: 5
[    15.294]     LinBlueMaskSize: 5
[    15.294]     LinBlueFieldPosition: 0
[    15.294]     LinRsvdMaskSize: 0
[    15.294]     LinRsvdFieldPosition: 0
[    15.295]     MaxPixelClock: 400000000
[    15.296] Mode: 116 (1024x768)
[    15.296]     ModeAttributes: 0xbb
[    15.296]     WinAAttributes: 0x7
[    15.296]     WinBAttributes: 0x0
[    15.296]     WinGranularity: 64
[    15.296]     WinSize: 64
[    15.296]     WinASegment: 0xa000
[    15.296]     WinBSegment: 0x0
[    15.296]     WinFuncPtr: 0xc0005543
[    15.296]     BytesPerScanline: 2048
[    15.296]     XResolution: 1024
[    15.296]     YResolution: 768
[    15.296]     XCharSize: 8
[    15.296]     YCharSize: 16
[    15.296]     NumberOfPlanes: 1
[    15.296]     BitsPerPixel: 16
[    15.296]     NumberOfBanks: 1
[    15.296]     MemoryModel: 6
[    15.296]     BankSize: 0
[    15.296]     NumberOfImages: 9
[    15.296]     RedMaskSize: 5
[    15.296]     RedFieldPosition: 10
[    15.296]     GreenMaskSize: 5
[    15.296]     GreenFieldPosition: 5
[    15.296]     BlueMaskSize: 5
[    15.296]     BlueFieldPosition: 0
[    15.296]     RsvdMaskSize: 0
[    15.296]     RsvdFieldPosition: 0
[    15.296]     DirectColorModeInfo: 0
[    15.296]     PhysBasePtr: 0x80000000
[    15.296]     LinBytesPerScanLine: 2048
[    15.296]     BnkNumberOfImagePages: 9
[    15.296]     LinNumberOfImagePages: 9
[    15.296]     LinRedMaskSize: 5
[    15.296]     LinRedFieldPosition: 10
[    15.296]     LinGreenMaskSize: 5
[    15.296]     LinGreenFieldPosition: 5
[    15.296]     LinBlueMaskSize: 5
[    15.296]     LinBlueFieldPosition: 0
[    15.296]     LinRsvdMaskSize: 0
[    15.296]     LinRsvdFieldPosition: 0
[    15.296]     MaxPixelClock: 400000000
[    15.297] Mode: 117 (1024x768)
[    15.298]     ModeAttributes: 0xbb
[    15.298]     WinAAttributes: 0x7
[    15.298]     WinBAttributes: 0x0
[    15.298]     WinGranularity: 64
[    15.298]     WinSize: 64
[    15.298]     WinASegment: 0xa000
[    15.298]     WinBSegment: 0x0
[    15.298]     WinFuncPtr: 0xc0005543
[    15.298]     BytesPerScanline: 2048
[    15.298]     XResolution: 1024
[    15.298]     YResolution: 768
[    15.298]     XCharSize: 8
[    15.298]     YCharSize: 16
[    15.298]     NumberOfPlanes: 1
[    15.298]     BitsPerPixel: 16
[    15.298]     NumberOfBanks: 1
[    15.298]     MemoryModel: 6
[    15.298]     BankSize: 0
[    15.298]     NumberOfImages: 9
[    15.298]     RedMaskSize: 5
[    15.298]     RedFieldPosition: 11
[    15.298]     GreenMaskSize: 6
[    15.298]     GreenFieldPosition: 5
[    15.298]     BlueMaskSize: 5
[    15.298]     BlueFieldPosition: 0
[    15.298]     RsvdMaskSize: 0
[    15.298]     RsvdFieldPosition: 0
[    15.298]     DirectColorModeInfo: 0
[    15.298]     PhysBasePtr: 0x80000000
[    15.298]     LinBytesPerScanLine: 2048
[    15.298]     BnkNumberOfImagePages: 9
[    15.298]     LinNumberOfImagePages: 9
[    15.298]     LinRedMaskSize: 5
[    15.298]     LinRedFieldPosition: 11
[    15.298]     LinGreenMaskSize: 6
[    15.298]     LinGreenFieldPosition: 5
[    15.298]     LinBlueMaskSize: 5
[    15.298]     LinBlueFieldPosition: 0
[    15.298]     LinRsvdMaskSize: 0
[    15.298]     LinRsvdFieldPosition: 0
[    15.298]     MaxPixelClock: 400000000
[    15.299] Mode: 119 (1280x1024)
[    15.299]     ModeAttributes: 0xba
[    15.299]     WinAAttributes: 0x7
[    15.299]     WinBAttributes: 0x0
[    15.299]     WinGranularity: 64
[    15.299]     WinSize: 64
[    15.299]     WinASegment: 0xa000
[    15.299]     WinBSegment: 0x0
[    15.299]     WinFuncPtr: 0xc0005543
[    15.299]     BytesPerScanline: 2560
[    15.299]     XResolution: 1280
[    15.299]     YResolution: 1024
[    15.300]     XCharSize: 8
[    15.300]     YCharSize: 16
[    15.300]     NumberOfPlanes: 1
[    15.300]     BitsPerPixel: 16
[    15.300]     NumberOfBanks: 1
[    15.300]     MemoryModel: 6
[    15.300]     BankSize: 0
[    15.300]     NumberOfImages: 5
[    15.300]     RedMaskSize: 5
[    15.300]     RedFieldPosition: 10
[    15.300]     GreenMaskSize: 5
[    15.300]     GreenFieldPosition: 5
[    15.300]     BlueMaskSize: 5
[    15.300]     BlueFieldPosition: 0
[    15.300]     RsvdMaskSize: 0
[    15.300]     RsvdFieldPosition: 0
[    15.300]     DirectColorModeInfo: 0
[    15.300]     PhysBasePtr: 0x80000000
[    15.300]     LinBytesPerScanLine: 2560
[    15.300]     BnkNumberOfImagePages: 5
[    15.300]     LinNumberOfImagePages: 5
[    15.300]     LinRedMaskSize: 5
[    15.300]     LinRedFieldPosition: 10
[    15.300]     LinGreenMaskSize: 5
[    15.300]     LinGreenFieldPosition: 5
[    15.300]     LinBlueMaskSize: 5
[    15.300]     LinBlueFieldPosition: 0
[    15.300]     LinRsvdMaskSize: 0
[    15.300]     LinRsvdFieldPosition: 0
[    15.300]     MaxPixelClock: 400000000
[    15.301] Mode: 11a (1280x1024)
[    15.301]     ModeAttributes: 0xba
[    15.301]     WinAAttributes: 0x7
[    15.301]     WinBAttributes: 0x0
[    15.301]     WinGranularity: 64
[    15.301]     WinSize: 64
[    15.301]     WinASegment: 0xa000
[    15.301]     WinBSegment: 0x0
[    15.301]     WinFuncPtr: 0xc0005543
[    15.301]     BytesPerScanline: 2560
[    15.301]     XResolution: 1280
[    15.301]     YResolution: 1024
[    15.301]     XCharSize: 8
[    15.301]     YCharSize: 16
[    15.301]     NumberOfPlanes: 1
[    15.301]     BitsPerPixel: 16
[    15.301]     NumberOfBanks: 1
[    15.301]     MemoryModel: 6
[    15.301]     BankSize: 0
[    15.301]     NumberOfImages: 5
[    15.301]     RedMaskSize: 5
[    15.301]     RedFieldPosition: 11
[    15.301]     GreenMaskSize: 6
[    15.301]     GreenFieldPosition: 5
[    15.302]     BlueMaskSize: 5
[    15.302]     BlueFieldPosition: 0
[    15.302]     RsvdMaskSize: 0
[    15.302]     RsvdFieldPosition: 0
[    15.302]     DirectColorModeInfo: 0
[    15.302]     PhysBasePtr: 0x80000000
[    15.302]     LinBytesPerScanLine: 2560
[    15.302]     BnkNumberOfImagePages: 5
[    15.302]     LinNumberOfImagePages: 5
[    15.302]     LinRedMaskSize: 5
[    15.302]     LinRedFieldPosition: 11
[    15.302]     LinGreenMaskSize: 6
[    15.302]     LinGreenFieldPosition: 5
[    15.302]     LinBlueMaskSize: 5
[    15.302]     LinBlueFieldPosition: 0
[    15.302]     LinRsvdMaskSize: 0
[    15.302]     LinRsvdFieldPosition: 0
[    15.302]     MaxPixelClock: 400000000
[    15.303] Mode: 10d (320x200)
[    15.303]     ModeAttributes: 0xbb
[    15.303]     WinAAttributes: 0x7
[    15.303]     WinBAttributes: 0x0
[    15.303]     WinGranularity: 64
[    15.303]     WinSize: 64
[    15.303]     WinASegment: 0xa000
[    15.303]     WinBSegment: 0x0
[    15.303]     WinFuncPtr: 0xc0005543
[    15.303]     BytesPerScanline: 640
[    15.303]     XResolution: 320
[    15.303]     YResolution: 200
[    15.303]     XCharSize: 8
[    15.303]     YCharSize: 8
[    15.303]     NumberOfPlanes: 1
[    15.303]     BitsPerPixel: 16
[    15.303]     NumberOfBanks: 1
[    15.303]     MemoryModel: 6
[    15.303]     BankSize: 0
[    15.303]     NumberOfImages: 127
[    15.303]     RedMaskSize: 5
[    15.303]     RedFieldPosition: 10
[    15.303]     GreenMaskSize: 5
[    15.303]     GreenFieldPosition: 5
[    15.303]     BlueMaskSize: 5
[    15.303]     BlueFieldPosition: 0
[    15.303]     RsvdMaskSize: 0
[    15.303]     RsvdFieldPosition: 0
[    15.303]     DirectColorModeInfo: 0
[    15.303]     PhysBasePtr: 0x80000000
[    15.303]     LinBytesPerScanLine: 640
[    15.303]     BnkNumberOfImagePages: 127
[    15.303]     LinNumberOfImagePages: 127
[    15.303]     LinRedMaskSize: 5
[    15.303]     LinRedFieldPosition: 10
[    15.303]     LinGreenMaskSize: 5
[    15.303]     LinGreenFieldPosition: 5
[    15.303]     LinBlueMaskSize: 5
[    15.303]     LinBlueFieldPosition: 0
[    15.304]     LinRsvdMaskSize: 0
[    15.304]     LinRsvdFieldPosition: 0
[    15.304]     MaxPixelClock: 400000000
[    15.305] Mode: 10e (320x200)
[    15.305]     ModeAttributes: 0xbb
[    15.305]     WinAAttributes: 0x7
[    15.305]     WinBAttributes: 0x0
[    15.305]     WinGranularity: 64
[    15.305]     WinSize: 64
[    15.305]     WinASegment: 0xa000
[    15.305]     WinBSegment: 0x0
[    15.305]     WinFuncPtr: 0xc0005543
[    15.305]     BytesPerScanline: 640
[    15.305]     XResolution: 320
[    15.305]     YResolution: 200
[    15.305]     XCharSize: 8
[    15.305]     YCharSize: 8
[    15.305]     NumberOfPlanes: 1
[    15.305]     BitsPerPixel: 16
[    15.305]     NumberOfBanks: 1
[    15.305]     MemoryModel: 6
[    15.305]     BankSize: 0
[    15.305]     NumberOfImages: 127
[    15.305]     RedMaskSize: 5
[    15.305]     RedFieldPosition: 11
[    15.305]     GreenMaskSize: 6
[    15.305]     GreenFieldPosition: 5
[    15.305]     BlueMaskSize: 5
[    15.305]     BlueFieldPosition: 0
[    15.305]     RsvdMaskSize: 0
[    15.305]     RsvdFieldPosition: 0
[    15.305]     DirectColorModeInfo: 0
[    15.305]     PhysBasePtr: 0x80000000
[    15.305]     LinBytesPerScanLine: 640
[    15.305]     BnkNumberOfImagePages: 127
[    15.305]     LinNumberOfImagePages: 127
[    15.305]     LinRedMaskSize: 5
[    15.305]     LinRedFieldPosition: 11
[    15.305]     LinGreenMaskSize: 6
[    15.305]     LinGreenFieldPosition: 5
[    15.305]     LinBlueMaskSize: 5
[    15.305]     LinBlueFieldPosition: 0
[    15.305]     LinRsvdMaskSize: 0
[    15.305]     LinRsvdFieldPosition: 0
[    15.305]     MaxPixelClock: 400000000
[    15.307] *Mode: 120 (320x200)
[    15.307]     ModeAttributes: 0xbb
[    15.307]     WinAAttributes: 0x7
[    15.307]     WinBAttributes: 0x0
[    15.307]     WinGranularity: 64
[    15.307]     WinSize: 64
[    15.307]     WinASegment: 0xa000
[    15.307]     WinBSegment: 0x0
[    15.307]     WinFuncPtr: 0xc0005543
[    15.307]     BytesPerScanline: 1280
[    15.307]     XResolution: 320
[    15.307]     YResolution: 200
[    15.307]     XCharSize: 8
[    15.307]     YCharSize: 8
[    15.307]     NumberOfPlanes: 1
[    15.307]     BitsPerPixel: 32
[    15.307]     NumberOfBanks: 1
[    15.307]     MemoryModel: 6
[    15.307]     BankSize: 0
[    15.307]     NumberOfImages: 63
[    15.307]     RedMaskSize: 8
[    15.307]     RedFieldPosition: 16
[    15.307]     GreenMaskSize: 8
[    15.307]     GreenFieldPosition: 8
[    15.307]     BlueMaskSize: 8
[    15.307]     BlueFieldPosition: 0
[    15.307]     RsvdMaskSize: 0
[    15.307]     RsvdFieldPosition: 0
[    15.307]     DirectColorModeInfo: 0
[    15.307]     PhysBasePtr: 0x80000000
[    15.307]     LinBytesPerScanLine: 1280
[    15.307]     BnkNumberOfImagePages: 63
[    15.307]     LinNumberOfImagePages: 63
[    15.307]     LinRedMaskSize: 8
[    15.307]     LinRedFieldPosition: 16
[    15.307]     LinGreenMaskSize: 8
[    15.307]     LinGreenFieldPosition: 8
[    15.307]     LinBlueMaskSize: 8
[    15.307]     LinBlueFieldPosition: 0
[    15.307]     LinRsvdMaskSize: 0
[    15.307]     LinRsvdFieldPosition: 0
[    15.307]     MaxPixelClock: 400000000
[    15.308] Mode: 193 (320x240)
[    15.308]     ModeAttributes: 0xbb
[    15.308]     WinAAttributes: 0x7
[    15.308]     WinBAttributes: 0x0
[    15.309]     WinGranularity: 64
[    15.309]     WinSize: 64
[    15.309]     WinASegment: 0xa000
[    15.309]     WinBSegment: 0x0
[    15.309]     WinFuncPtr: 0xc0005543
[    15.309]     BytesPerScanline: 320
[    15.309]     XResolution: 320
[    15.309]     YResolution: 240
[    15.309]     XCharSize: 8
[    15.309]     YCharSize: 8
[    15.309]     NumberOfPlanes: 1
[    15.309]     BitsPerPixel: 8
[    15.309]     NumberOfBanks: 1
[    15.309]     MemoryModel: 4
[    15.309]     BankSize: 0
[    15.309]     NumberOfImages: 127
[    15.309]     RedMaskSize: 0
[    15.309]     RedFieldPosition: 0
[    15.309]     GreenMaskSize: 0
[    15.309]     GreenFieldPosition: 0
[    15.309]     BlueMaskSize: 0
[    15.309]     BlueFieldPosition: 0
[    15.309]     RsvdMaskSize: 0
[    15.309]     RsvdFieldPosition: 0
[    15.309]     DirectColorModeInfo: 0
[    15.309]     PhysBasePtr: 0x80000000
[    15.309]     LinBytesPerScanLine: 320
[    15.309]     BnkNumberOfImagePages: 127
[    15.309]     LinNumberOfImagePages: 127
[    15.309]     LinRedMaskSize: 0
[    15.309]     LinRedFieldPosition: 0
[    15.309]     LinGreenMaskSize: 0
[    15.309]     LinGreenFieldPosition: 0
[    15.309]     LinBlueMaskSize: 0
[    15.309]     LinBlueFieldPosition: 0
[    15.309]     LinRsvdMaskSize: 0
[    15.309]     LinRsvdFieldPosition: 0
[    15.309]     MaxPixelClock: 400000000
[    15.310] Mode: 195 (320x240)
[    15.310]     ModeAttributes: 0xbb
[    15.310]     WinAAttributes: 0x7
[    15.310]     WinBAttributes: 0x0
[    15.310]     WinGranularity: 64
[    15.310]     WinSize: 64
[    15.310]     WinASegment: 0xa000
[    15.310]     WinBSegment: 0x0
[    15.310]     WinFuncPtr: 0xc0005543
[    15.310]     BytesPerScanline: 640
[    15.310]     XResolution: 320
[    15.310]     YResolution: 240
[    15.311]     XCharSize: 8
[    15.311]     YCharSize: 8
[    15.311]     NumberOfPlanes: 1
[    15.311]     BitsPerPixel: 16
[    15.311]     NumberOfBanks: 1
[    15.311]     MemoryModel: 6
[    15.311]     BankSize: 0
[    15.311]     NumberOfImages: 84
[    15.311]     RedMaskSize: 5
[    15.311]     RedFieldPosition: 11
[    15.311]     GreenMaskSize: 6
[    15.311]     GreenFieldPosition: 5
[    15.311]     BlueMaskSize: 5
[    15.311]     BlueFieldPosition: 0
[    15.311]     RsvdMaskSize: 0
[    15.311]     RsvdFieldPosition: 0
[    15.311]     DirectColorModeInfo: 0
[    15.311]     PhysBasePtr: 0x80000000
[    15.311]     LinBytesPerScanLine: 640
[    15.311]     BnkNumberOfImagePages: 84
[    15.311]     LinNumberOfImagePages: 84
[    15.311]     LinRedMaskSize: 5
[    15.311]     LinRedFieldPosition: 11
[    15.311]     LinGreenMaskSize: 6
[    15.311]     LinGreenFieldPosition: 5
[    15.311]     LinBlueMaskSize: 5
[    15.311]     LinBlueFieldPosition: 0
[    15.311]     LinRsvdMaskSize: 0
[    15.311]     LinRsvdFieldPosition: 0
[    15.311]     MaxPixelClock: 400000000
[    15.312] *Mode: 196 (320x240)
[    15.312]     ModeAttributes: 0xbb
[    15.312]     WinAAttributes: 0x7
[    15.312]     WinBAttributes: 0x0
[    15.312]     WinGranularity: 64
[    15.312]     WinSize: 64
[    15.312]     WinASegment: 0xa000
[    15.312]     WinBSegment: 0x0
[    15.312]     WinFuncPtr: 0xc0005543
[    15.312]     BytesPerScanline: 1280
[    15.312]     XResolution: 320
[    15.312]     YResolution: 240
[    15.312]     XCharSize: 8
[    15.312]     YCharSize: 8
[    15.312]     NumberOfPlanes: 1
[    15.312]     BitsPerPixel: 32
[    15.312]     NumberOfBanks: 1
[    15.312]     MemoryModel: 6
[    15.312]     BankSize: 0
[    15.312]     NumberOfImages: 50
[    15.312]     RedMaskSize: 8
[    15.312]     RedFieldPosition: 16
[    15.312]     GreenMaskSize: 8
[    15.313]     GreenFieldPosition: 8
[    15.313]     BlueMaskSize: 8
[    15.313]     BlueFieldPosition: 0
[    15.313]     RsvdMaskSize: 0
[    15.313]     RsvdFieldPosition: 0
[    15.313]     DirectColorModeInfo: 0
[    15.313]     PhysBasePtr: 0x80000000
[    15.313]     LinBytesPerScanLine: 1280
[    15.313]     BnkNumberOfImagePages: 50
[    15.313]     LinNumberOfImagePages: 50
[    15.313]     LinRedMaskSize: 8
[    15.313]     LinRedFieldPosition: 16
[    15.313]     LinGreenMaskSize: 8
[    15.313]     LinGreenFieldPosition: 8
[    15.313]     LinBlueMaskSize: 8
[    15.313]     LinBlueFieldPosition: 0
[    15.313]     LinRsvdMaskSize: 0
[    15.313]     LinRsvdFieldPosition: 0
[    15.313]     MaxPixelClock: 400000000
[    15.314] Mode: 1b3 (512x384)
[    15.314]     ModeAttributes: 0xbb
[    15.314]     WinAAttributes: 0x7
[    15.314]     WinBAttributes: 0x0
[    15.314]     WinGranularity: 64
[    15.314]     WinSize: 64
[    15.314]     WinASegment: 0xa000
[    15.314]     WinBSegment: 0x0
[    15.314]     WinFuncPtr: 0xc0005543
[    15.314]     BytesPerScanline: 512
[    15.314]     XResolution: 512
[    15.314]     YResolution: 384
[    15.314]     XCharSize: 8
[    15.314]     YCharSize: 16
[    15.314]     NumberOfPlanes: 1
[    15.314]     BitsPerPixel: 8
[    15.314]     NumberOfBanks: 1
[    15.314]     MemoryModel: 4
[    15.314]     BankSize: 0
[    15.314]     NumberOfImages: 63
[    15.314]     RedMaskSize: 0
[    15.314]     RedFieldPosition: 0
[    15.314]     GreenMaskSize: 0
[    15.314]     GreenFieldPosition: 0
[    15.314]     BlueMaskSize: 0
[    15.314]     BlueFieldPosition: 0
[    15.314]     RsvdMaskSize: 0
[    15.314]     RsvdFieldPosition: 0
[    15.314]     DirectColorModeInfo: 0
[    15.314]     PhysBasePtr: 0x80000000
[    15.314]     LinBytesPerScanLine: 512
[    15.314]     BnkNumberOfImagePages: 63
[    15.314]     LinNumberOfImagePages: 63
[    15.314]     LinRedMaskSize: 0
[    15.314]     LinRedFieldPosition: 0
[    15.315]     LinGreenMaskSize: 0
[    15.315]     LinGreenFieldPosition: 0
[    15.315]     LinBlueMaskSize: 0
[    15.315]     LinBlueFieldPosition: 0
[    15.315]     LinRsvdMaskSize: 0
[    15.315]     LinRsvdFieldPosition: 0
[    15.315]     MaxPixelClock: 400000000
[    15.316] Mode: 1b5 (512x384)
[    15.316]     ModeAttributes: 0xbb
[    15.316]     WinAAttributes: 0x7
[    15.316]     WinBAttributes: 0x0
[    15.316]     WinGranularity: 64
[    15.316]     WinSize: 64
[    15.316]     WinASegment: 0xa000
[    15.316]     WinBSegment: 0x0
[    15.316]     WinFuncPtr: 0xc0005543
[    15.316]     BytesPerScanline: 1024
[    15.316]     XResolution: 512
[    15.316]     YResolution: 384
[    15.316]     XCharSize: 8
[    15.316]     YCharSize: 16
[    15.316]     NumberOfPlanes: 1
[    15.316]     BitsPerPixel: 16
[    15.316]     NumberOfBanks: 1
[    15.316]     MemoryModel: 6
[    15.316]     BankSize: 0
[    15.316]     NumberOfImages: 35
[    15.316]     RedMaskSize: 5
[    15.316]     RedFieldPosition: 11
[    15.316]     GreenMaskSize: 6
[    15.316]     GreenFieldPosition: 5
[    15.316]     BlueMaskSize: 5
[    15.316]     BlueFieldPosition: 0
[    15.316]     RsvdMaskSize: 0
[    15.316]     RsvdFieldPosition: 0
[    15.316]     DirectColorModeInfo: 0
[    15.316]     PhysBasePtr: 0x80000000
[    15.316]     LinBytesPerScanLine: 1024
[    15.316]     BnkNumberOfImagePages: 35
[    15.316]     LinNumberOfImagePages: 35
[    15.316]     LinRedMaskSize: 5
[    15.316]     LinRedFieldPosition: 11
[    15.316]     LinGreenMaskSize: 6
[    15.316]     LinGreenFieldPosition: 5
[    15.316]     LinBlueMaskSize: 5
[    15.316]     LinBlueFieldPosition: 0
[    15.316]     LinRsvdMaskSize: 0
[    15.316]     LinRsvdFieldPosition: 0
[    15.316]     MaxPixelClock: 400000000
[    15.318] *Mode: 1b6 (512x384)
[    15.318]     ModeAttributes: 0xbb
[    15.318]     WinAAttributes: 0x7
[    15.318]     WinBAttributes: 0x0
[    15.318]     WinGranularity: 64
[    15.318]     WinSize: 64
[    15.318]     WinASegment: 0xa000
[    15.318]     WinBSegment: 0x0
[    15.318]     WinFuncPtr: 0xc0005543
[    15.318]     BytesPerScanline: 2048
[    15.318]     XResolution: 512
[    15.318]     YResolution: 384
[    15.318]     XCharSize: 8
[    15.318]     YCharSize: 16
[    15.318]     NumberOfPlanes: 1
[    15.318]     BitsPerPixel: 32
[    15.318]     NumberOfBanks: 1
[    15.318]     MemoryModel: 6
[    15.318]     BankSize: 0
[    15.318]     NumberOfImages: 18
[    15.318]     RedMaskSize: 8
[    15.318]     RedFieldPosition: 16
[    15.318]     GreenMaskSize: 8
[    15.318]     GreenFieldPosition: 8
[    15.318]     BlueMaskSize: 8
[    15.318]     BlueFieldPosition: 0
[    15.318]     RsvdMaskSize: 0
[    15.318]     RsvdFieldPosition: 0
[    15.318]     DirectColorModeInfo: 0
[    15.318]     PhysBasePtr: 0x80000000
[    15.318]     LinBytesPerScanLine: 2048
[    15.318]     BnkNumberOfImagePages: 18
[    15.318]     LinNumberOfImagePages: 18
[    15.318]     LinRedMaskSize: 8
[    15.318]     LinRedFieldPosition: 16
[    15.318]     LinGreenMaskSize: 8
[    15.318]     LinGreenFieldPosition: 8
[    15.318]     LinBlueMaskSize: 8
[    15.318]     LinBlueFieldPosition: 0
[    15.318]     LinRsvdMaskSize: 0
[    15.318]     LinRsvdFieldPosition: 0
[    15.318]     MaxPixelClock: 400000000
[    15.320] Mode: 1c3 (640x350)
[    15.320]     ModeAttributes: 0xbb
[    15.320]     WinAAttributes: 0x7
[    15.320]     WinBAttributes: 0x0
[    15.320]     WinGranularity: 64
[    15.320]     WinSize: 64
[    15.320]     WinASegment: 0xa000
[    15.320]     WinBSegment: 0x0
[    15.320]     WinFuncPtr: 0xc0005543
[    15.320]     BytesPerScanline: 640
[    15.320]     XResolution: 640
[    15.320]     YResolution: 350
[    15.320]     XCharSize: 8
[    15.320]     YCharSize: 14
[    15.320]     NumberOfPlanes: 1
[    15.320]     BitsPerPixel: 8
[    15.320]     NumberOfBanks: 1
[    15.320]     MemoryModel: 4
[    15.320]     BankSize: 0
[    15.320]     NumberOfImages: 63
[    15.320]     RedMaskSize: 0
[    15.320]     RedFieldPosition: 0
[    15.320]     GreenMaskSize: 0
[    15.320]     GreenFieldPosition: 0
[    15.320]     BlueMaskSize: 0
[    15.320]     BlueFieldPosition: 0
[    15.320]     RsvdMaskSize: 0
[    15.320]     RsvdFieldPosition: 0
[    15.320]     DirectColorModeInfo: 0
[    15.320]     PhysBasePtr: 0x80000000
[    15.320]     LinBytesPerScanLine: 640
[    15.320]     BnkNumberOfImagePages: 63
[    15.320]     LinNumberOfImagePages: 63
[    15.320]     LinRedMaskSize: 0
[    15.320]     LinRedFieldPosition: 0
[    15.320]     LinGreenMaskSize: 0
[    15.320]     LinGreenFieldPosition: 0
[    15.320]     LinBlueMaskSize: 0
[    15.320]     LinBlueFieldPosition: 0
[    15.320]     LinRsvdMaskSize: 0
[    15.320]     LinRsvdFieldPosition: 0
[    15.320]     MaxPixelClock: 400000000
[    15.321] Mode: 1c5 (640x350)
[    15.321]     ModeAttributes: 0xbb
[    15.321]     WinAAttributes: 0x7
[    15.321]     WinBAttributes: 0x0
[    15.321]     WinGranularity: 64
[    15.321]     WinSize: 64
[    15.321]     WinASegment: 0xa000
[    15.321]     WinBSegment: 0x0
[    15.321]     WinFuncPtr: 0xc0005543
[    15.322]     BytesPerScanline: 1280
[    15.322]     XResolution: 640
[    15.322]     YResolution: 350
[    15.322]     XCharSize: 8
[    15.322]     YCharSize: 14
[    15.322]     NumberOfPlanes: 1
[    15.322]     BitsPerPixel: 16
[    15.322]     NumberOfBanks: 1
[    15.322]     MemoryModel: 6
[    15.322]     BankSize: 0
[    15.322]     NumberOfImages: 35
[    15.322]     RedMaskSize: 5
[    15.322]     RedFieldPosition: 11
[    15.322]     GreenMaskSize: 6
[    15.322]     GreenFieldPosition: 5
[    15.322]     BlueMaskSize: 5
[    15.322]     BlueFieldPosition: 0
[    15.322]     RsvdMaskSize: 0
[    15.322]     RsvdFieldPosition: 0
[    15.322]     DirectColorModeInfo: 0
[    15.322]     PhysBasePtr: 0x80000000
[    15.322]     LinBytesPerScanLine: 1280
[    15.322]     BnkNumberOfImagePages: 35
[    15.322]     LinNumberOfImagePages: 35
[    15.322]     LinRedMaskSize: 5
[    15.322]     LinRedFieldPosition: 11
[    15.322]     LinGreenMaskSize: 6
[    15.322]     LinGreenFieldPosition: 5
[    15.322]     LinBlueMaskSize: 5
[    15.322]     LinBlueFieldPosition: 0
[    15.322]     LinRsvdMaskSize: 0
[    15.322]     LinRsvdFieldPosition: 0
[    15.322]     MaxPixelClock: 400000000
[    15.323] *Mode: 1c6 (640x350)
[    15.323]     ModeAttributes: 0xbb
[    15.323]     WinAAttributes: 0x7
[    15.323]     WinBAttributes: 0x0
[    15.323]     WinGranularity: 64
[    15.323]     WinSize: 64
[    15.323]     WinASegment: 0xa000
[    15.323]     WinBSegment: 0x0
[    15.323]     WinFuncPtr: 0xc0005543
[    15.323]     BytesPerScanline: 2560
[    15.323]     XResolution: 640
[    15.323]     YResolution: 350
[    15.323]     XCharSize: 8
[    15.323]     YCharSize: 14
[    15.323]     NumberOfPlanes: 1
[    15.324]     BitsPerPixel: 32
[    15.324]     NumberOfBanks: 1
[    15.324]     MemoryModel: 6
[    15.324]     BankSize: 0
[    15.324]     NumberOfImages: 17
[    15.324]     RedMaskSize: 8
[    15.324]     RedFieldPosition: 16
[    15.324]     GreenMaskSize: 8
[    15.324]     GreenFieldPosition: 8
[    15.324]     BlueMaskSize: 8
[    15.324]     BlueFieldPosition: 0
[    15.324]     RsvdMaskSize: 0
[    15.324]     RsvdFieldPosition: 0
[    15.324]     DirectColorModeInfo: 0
[    15.324]     PhysBasePtr: 0x80000000
[    15.324]     LinBytesPerScanLine: 2560
[    15.324]     BnkNumberOfImagePages: 17
[    15.324]     LinNumberOfImagePages: 17
[    15.324]     LinRedMaskSize: 8
[    15.324]     LinRedFieldPosition: 16
[    15.324]     LinGreenMaskSize: 8
[    15.324]     LinGreenFieldPosition: 8
[    15.324]     LinBlueMaskSize: 8
[    15.324]     LinBlueFieldPosition: 0
[    15.324]     LinRsvdMaskSize: 0
[    15.324]     LinRsvdFieldPosition: 0
[    15.324]     MaxPixelClock: 400000000
[    15.325] Mode: 133 (720x400)
[    15.325]     ModeAttributes: 0xbb
[    15.325]     WinAAttributes: 0x7
[    15.325]     WinBAttributes: 0x0
[    15.325]     WinGranularity: 64
[    15.325]     WinSize: 64
[    15.325]     WinASegment: 0xa000
[    15.325]     WinBSegment: 0x0
[    15.325]     WinFuncPtr: 0xc0005543
[    15.325]     BytesPerScanline: 768
[    15.325]     XResolution: 720
[    15.325]     YResolution: 400
[    15.326]     XCharSize: 8
[    15.326]     YCharSize: 16
[    15.326]     NumberOfPlanes: 1
[    15.326]     BitsPerPixel: 8
[    15.326]     NumberOfBanks: 1
[    15.326]     MemoryModel: 4
[    15.326]     BankSize: 0
[    15.326]     NumberOfImages: 50
[    15.326]     RedMaskSize: 0
[    15.326]     RedFieldPosition: 0
[    15.326]     GreenMaskSize: 0
[    15.326]     GreenFieldPosition: 0
[    15.326]     BlueMaskSize: 0
[    15.326]     BlueFieldPosition: 0
[    15.326]     RsvdMaskSize: 0
[    15.326]     RsvdFieldPosition: 0
[    15.326]     DirectColorModeInfo: 0
[    15.326]     PhysBasePtr: 0x80000000
[    15.326]     LinBytesPerScanLine: 768
[    15.326]     BnkNumberOfImagePages: 50
[    15.326]     LinNumberOfImagePages: 50
[    15.326]     LinRedMaskSize: 0
[    15.326]     LinRedFieldPosition: 0
[    15.326]     LinGreenMaskSize: 0
[    15.326]     LinGreenFieldPosition: 0
[    15.326]     LinBlueMaskSize: 0
[    15.326]     LinBlueFieldPosition: 0
[    15.326]     LinRsvdMaskSize: 0
[    15.326]     LinRsvdFieldPosition: 0
[    15.326]     MaxPixelClock: 400000000
[    15.327] Mode: 135 (720x400)
[    15.327]     ModeAttributes: 0xbb
[    15.327]     WinAAttributes: 0x7
[    15.327]     WinBAttributes: 0x0
[    15.327]     WinGranularity: 64
[    15.327]     WinSize: 64
[    15.327]     WinASegment: 0xa000
[    15.327]     WinBSegment: 0x0
[    15.327]     WinFuncPtr: 0xc0005543
[    15.327]     BytesPerScanline: 1472
[    15.328]     XResolution: 720
[    15.328]     YResolution: 400
[    15.328]     XCharSize: 8
[    15.328]     YCharSize: 16
[    15.328]     NumberOfPlanes: 1
[    15.328]     BitsPerPixel: 16
[    15.328]     NumberOfBanks: 1
[    15.328]     MemoryModel: 6
[    15.328]     BankSize: 0
[    15.328]     NumberOfImages: 27
[    15.328]     RedMaskSize: 5
[    15.328]     RedFieldPosition: 11
[    15.328]     GreenMaskSize: 6
[    15.328]     GreenFieldPosition: 5
[    15.328]     BlueMaskSize: 5
[    15.328]     BlueFieldPosition: 0
[    15.328]     RsvdMaskSize: 0
[    15.328]     RsvdFieldPosition: 0
[    15.328]     DirectColorModeInfo: 0
[    15.328]     PhysBasePtr: 0x80000000
[    15.328]     LinBytesPerScanLine: 1472
[    15.328]     BnkNumberOfImagePages: 27
[    15.328]     LinNumberOfImagePages: 27
[    15.328]     LinRedMaskSize: 5
[    15.328]     LinRedFieldPosition: 11
[    15.328]     LinGreenMaskSize: 6
[    15.328]     LinGreenFieldPosition: 5
[    15.328]     LinBlueMaskSize: 5
[    15.328]     LinBlueFieldPosition: 0
[    15.328]     LinRsvdMaskSize: 0
[    15.328]     LinRsvdFieldPosition: 0
[    15.328]     MaxPixelClock: 400000000
[    15.329] *Mode: 136 (720x400)
[    15.329]     ModeAttributes: 0xbb
[    15.329]     WinAAttributes: 0x7
[    15.329]     WinBAttributes: 0x0
[    15.329]     WinGranularity: 64
[    15.329]     WinSize: 64
[    15.329]     WinASegment: 0xa000
[    15.329]     WinBSegment: 0x0
[    15.329]     WinFuncPtr: 0xc0005543
[    15.330]     BytesPerScanline: 2944
[    15.330]     XResolution: 720
[    15.330]     YResolution: 400
[    15.330]     XCharSize: 8
[    15.330]     YCharSize: 16
[    15.330]     NumberOfPlanes: 1
[    15.330]     BitsPerPixel: 32
[    15.330]     NumberOfBanks: 1
[    15.330]     MemoryModel: 6
[    15.330]     BankSize: 0
[    15.330]     NumberOfImages: 13
[    15.330]     RedMaskSize: 8
[    15.330]     RedFieldPosition: 16
[    15.330]     GreenMaskSize: 8
[    15.330]     GreenFieldPosition: 8
[    15.330]     BlueMaskSize: 8
[    15.330]     BlueFieldPosition: 0
[    15.330]     RsvdMaskSize: 0
[    15.330]     RsvdFieldPosition: 0
[    15.330]     DirectColorModeInfo: 0
[    15.330]     PhysBasePtr: 0x80000000
[    15.330]     LinBytesPerScanLine: 2944
[    15.330]     BnkNumberOfImagePages: 13
[    15.330]     LinNumberOfImagePages: 13
[    15.330]     LinRedMaskSize: 8
[    15.330]     LinRedFieldPosition: 16
[    15.330]     LinGreenMaskSize: 8
[    15.330]     LinGreenFieldPosition: 8
[    15.330]     LinBlueMaskSize: 8
[    15.330]     LinBlueFieldPosition: 0
[    15.330]     LinRsvdMaskSize: 0
[    15.330]     LinRsvdFieldPosition: 0
[    15.330]     MaxPixelClock: 400000000
[    15.331] Mode: 153 (1152x864)
[    15.331]     ModeAttributes: 0xba
[    15.331]     WinAAttributes: 0x7
[    15.331]     WinBAttributes: 0x0
[    15.331]     WinGranularity: 64
[    15.331]     WinSize: 64
[    15.331]     WinASegment: 0xa000
[    15.332]     WinBSegment: 0x0
[    15.332]     WinFuncPtr: 0xc0005543
[    15.332]     BytesPerScanline: 1152
[    15.332]     XResolution: 1152
[    15.332]     YResolution: 864
[    15.332]     XCharSize: 8
[    15.332]     YCharSize: 16
[    15.332]     NumberOfPlanes: 1
[    15.332]     BitsPerPixel: 8
[    15.332]     NumberOfBanks: 1
[    15.332]     MemoryModel: 4
[    15.332]     BankSize: 0
[    15.332]     NumberOfImages: 15
[    15.332]     RedMaskSize: 0
[    15.332]     RedFieldPosition: 0
[    15.332]     GreenMaskSize: 0
[    15.332]     GreenFieldPosition: 0
[    15.332]     BlueMaskSize: 0
[    15.332]     BlueFieldPosition: 0
[    15.332]     RsvdMaskSize: 0
[    15.332]     RsvdFieldPosition: 0
[    15.332]     DirectColorModeInfo: 0
[    15.332]     PhysBasePtr: 0x80000000
[    15.332]     LinBytesPerScanLine: 1152
[    15.332]     BnkNumberOfImagePages: 15
[    15.332]     LinNumberOfImagePages: 15
[    15.332]     LinRedMaskSize: 0
[    15.332]     LinRedFieldPosition: 0
[    15.332]     LinGreenMaskSize: 0
[    15.332]     LinGreenFieldPosition: 0
[    15.332]     LinBlueMaskSize: 0
[    15.332]     LinBlueFieldPosition: 0
[    15.332]     LinRsvdMaskSize: 0
[    15.332]     LinRsvdFieldPosition: 0
[    15.332]     MaxPixelClock: 400000000
[    15.333] Mode: 155 (1152x864)
[    15.333]     ModeAttributes: 0xba
[    15.333]     WinAAttributes: 0x7
[    15.333]     WinBAttributes: 0x0
[    15.333]     WinGranularity: 64
[    15.333]     WinSize: 64
[    15.334]     WinASegment: 0xa000
[    15.334]     WinBSegment: 0x0
[    15.334]     WinFuncPtr: 0xc0005543
[    15.334]     BytesPerScanline: 2304
[    15.334]     XResolution: 1152
[    15.334]     YResolution: 864
[    15.334]     XCharSize: 8
[    15.334]     YCharSize: 16
[    15.334]     NumberOfPlanes: 1
[    15.334]     BitsPerPixel: 16
[    15.334]     NumberOfBanks: 1
[    15.334]     MemoryModel: 6
[    15.334]     BankSize: 0
[    15.334]     NumberOfImages: 7
[    15.334]     RedMaskSize: 5
[    15.334]     RedFieldPosition: 11
[    15.334]     GreenMaskSize: 6
[    15.334]     GreenFieldPosition: 5
[    15.334]     BlueMaskSize: 5
[    15.334]     BlueFieldPosition: 0
[    15.334]     RsvdMaskSize: 0
[    15.334]     RsvdFieldPosition: 0
[    15.334]     DirectColorModeInfo: 0
[    15.334]     PhysBasePtr: 0x80000000
[    15.334]     LinBytesPerScanLine: 2304
[    15.334]     BnkNumberOfImagePages: 7
[    15.334]     LinNumberOfImagePages: 7
[    15.334]     LinRedMaskSize: 5
[    15.334]     LinRedFieldPosition: 11
[    15.334]     LinGreenMaskSize: 6
[    15.334]     LinGreenFieldPosition: 5
[    15.334]     LinBlueMaskSize: 5
[    15.334]     LinBlueFieldPosition: 0
[    15.334]     LinRsvdMaskSize: 0
[    15.334]     LinRsvdFieldPosition: 0
[    15.334]     MaxPixelClock: 400000000
[    15.335] Mode: 156 (1152x864)
[    15.335]     ModeAttributes: 0xba
[    15.335]     WinAAttributes: 0x7
[    15.335]     WinBAttributes: 0x0
[    15.335]     WinGranularity: 64
[    15.336]     WinSize: 64
[    15.336]     WinASegment: 0xa000
[    15.336]     WinBSegment: 0x0
[    15.336]     WinFuncPtr: 0xc0005543
[    15.336]     BytesPerScanline: 4608
[    15.336]     XResolution: 1152
[    15.336]     YResolution: 864
[    15.336]     XCharSize: 8
[    15.336]     YCharSize: 16
[    15.336]     NumberOfPlanes: 1
[    15.336]     BitsPerPixel: 32
[    15.336]     NumberOfBanks: 1
[    15.336]     MemoryModel: 6
[    15.336]     BankSize: 0
[    15.336]     NumberOfImages: 3
[    15.336]     RedMaskSize: 8
[    15.336]     RedFieldPosition: 16
[    15.336]     GreenMaskSize: 8
[    15.336]     GreenFieldPosition: 8
[    15.336]     BlueMaskSize: 8
[    15.336]     BlueFieldPosition: 0
[    15.336]     RsvdMaskSize: 0
[    15.336]     RsvdFieldPosition: 0
[    15.336]     DirectColorModeInfo: 0
[    15.336]     PhysBasePtr: 0x80000000
[    15.336]     LinBytesPerScanLine: 4608
[    15.336]     BnkNumberOfImagePages: 3
[    15.336]     LinNumberOfImagePages: 3
[    15.336]     LinRedMaskSize: 8
[    15.336]     LinRedFieldPosition: 16
[    15.336]     LinGreenMaskSize: 8
[    15.336]     LinGreenFieldPosition: 8
[    15.336]     LinBlueMaskSize: 8
[    15.336]     LinBlueFieldPosition: 0
[    15.336]     LinRsvdMaskSize: 0
[    15.336]     LinRsvdFieldPosition: 0
[    15.336]     MaxPixelClock: 400000000
[    15.337] Mode: 163 (1280x960)
[    15.337]     ModeAttributes: 0xba
[    15.337]     WinAAttributes: 0x7
[    15.337]     WinBAttributes: 0x0
[    15.337]     WinGranularity: 64
[    15.337]     WinSize: 64
[    15.337]     WinASegment: 0xa000
[    15.338]     WinBSegment: 0x0
[    15.338]     WinFuncPtr: 0xc0005543
[    15.338]     BytesPerScanline: 1280
[    15.338]     XResolution: 1280
[    15.338]     YResolution: 960
[    15.338]     XCharSize: 8
[    15.338]     YCharSize: 16
[    15.338]     NumberOfPlanes: 1
[    15.338]     BitsPerPixel: 8
[    15.338]     NumberOfBanks: 1
[    15.338]     MemoryModel: 4
[    15.338]     BankSize: 0
[    15.338]     NumberOfImages: 12
[    15.338]     RedMaskSize: 0
[    15.338]     RedFieldPosition: 0
[    15.338]     GreenMaskSize: 0
[    15.338]     GreenFieldPosition: 0
[    15.338]     BlueMaskSize: 0
[    15.338]     BlueFieldPosition: 0
[    15.338]     RsvdMaskSize: 0
[    15.338]     RsvdFieldPosition: 0
[    15.338]     DirectColorModeInfo: 0
[    15.338]     PhysBasePtr: 0x80000000
[    15.338]     LinBytesPerScanLine: 1280
[    15.338]     BnkNumberOfImagePages: 12
[    15.338]     LinNumberOfImagePages: 12
[    15.338]     LinRedMaskSize: 0
[    15.338]     LinRedFieldPosition: 0
[    15.338]     LinGreenMaskSize: 0
[    15.338]     LinGreenFieldPosition: 0
[    15.338]     LinBlueMaskSize: 0
[    15.338]     LinBlueFieldPosition: 0
[    15.338]     LinRsvdMaskSize: 0
[    15.338]     LinRsvdFieldPosition: 0
[    15.338]     MaxPixelClock: 400000000
[    15.339] Mode: 165 (1280x960)
[    15.339]     ModeAttributes: 0xba
[    15.339]     WinAAttributes: 0x7
[    15.339]     WinBAttributes: 0x0
[    15.339]     WinGranularity: 64
[    15.339]     WinSize: 64
[    15.339]     WinASegment: 0xa000
[    15.339]     WinBSegment: 0x0
[    15.339]     WinFuncPtr: 0xc0005543
[    15.339]     BytesPerScanline: 2560
[    15.339]     XResolution: 1280
[    15.340]     YResolution: 960
[    15.340]     XCharSize: 8
[    15.340]     YCharSize: 16
[    15.340]     NumberOfPlanes: 1
[    15.340]     BitsPerPixel: 16
[    15.340]     NumberOfBanks: 1
[    15.340]     MemoryModel: 6
[    15.340]     BankSize: 0
[    15.340]     NumberOfImages: 5
[    15.340]     RedMaskSize: 5
[    15.340]     RedFieldPosition: 11
[    15.340]     GreenMaskSize: 6
[    15.340]     GreenFieldPosition: 5
[    15.340]     BlueMaskSize: 5
[    15.340]     BlueFieldPosition: 0
[    15.340]     RsvdMaskSize: 0
[    15.340]     RsvdFieldPosition: 0
[    15.340]     DirectColorModeInfo: 0
[    15.340]     PhysBasePtr: 0x80000000
[    15.340]     LinBytesPerScanLine: 2560
[    15.340]     BnkNumberOfImagePages: 5
[    15.340]     LinNumberOfImagePages: 5
[    15.340]     LinRedMaskSize: 5
[    15.340]     LinRedFieldPosition: 11
[    15.340]     LinGreenMaskSize: 6
[    15.340]     LinGreenFieldPosition: 5
[    15.340]     LinBlueMaskSize: 5
[    15.340]     LinBlueFieldPosition: 0
[    15.340]     LinRsvdMaskSize: 0
[    15.340]     LinRsvdFieldPosition: 0
[    15.340]     MaxPixelClock: 400000000
[    15.341] Mode: 166 (1280x960)
[    15.341]     ModeAttributes: 0xba
[    15.341]     WinAAttributes: 0x7
[    15.341]     WinBAttributes: 0x0
[    15.341]     WinGranularity: 64
[    15.341]     WinSize: 64
[    15.342]     WinASegment: 0xa000
[    15.342]     WinBSegment: 0x0
[    15.342]     WinFuncPtr: 0xc0005543
[    15.342]     BytesPerScanline: 5120
[    15.342]     XResolution: 1280
[    15.342]     YResolution: 960
[    15.342]     XCharSize: 8
[    15.342]     YCharSize: 16
[    15.342]     NumberOfPlanes: 1
[    15.342]     BitsPerPixel: 32
[    15.342]     NumberOfBanks: 1
[    15.342]     MemoryModel: 6
[    15.342]     BankSize: 0
[    15.342]     NumberOfImages: 2
[    15.342]     RedMaskSize: 8
[    15.342]     RedFieldPosition: 16
[    15.342]     GreenMaskSize: 8
[    15.342]     GreenFieldPosition: 8
[    15.342]     BlueMaskSize: 8
[    15.342]     BlueFieldPosition: 0
[    15.342]     RsvdMaskSize: 0
[    15.342]     RsvdFieldPosition: 0
[    15.342]     DirectColorModeInfo: 0
[    15.342]     PhysBasePtr: 0x80000000
[    15.342]     LinBytesPerScanLine: 5120
[    15.342]     BnkNumberOfImagePages: 2
[    15.342]     LinNumberOfImagePages: 2
[    15.342]     LinRedMaskSize: 8
[    15.342]     LinRedFieldPosition: 16
[    15.342]     LinGreenMaskSize: 8
[    15.342]     LinGreenFieldPosition: 8
[    15.342]     LinBlueMaskSize: 8
[    15.342]     LinBlueFieldPosition: 0
[    15.342]     LinRsvdMaskSize: 0
[    15.342]     LinRsvdFieldPosition: 0
[    15.342]     MaxPixelClock: 400000000
[    15.343] *Mode: 121 (640x480)
[    15.343]     ModeAttributes: 0xbb
[    15.343]     WinAAttributes: 0x7
[    15.344]     WinBAttributes: 0x0
[    15.344]     WinGranularity: 64
[    15.344]     WinSize: 64
[    15.344]     WinASegment: 0xa000
[    15.344]     WinBSegment: 0x0
[    15.344]     WinFuncPtr: 0xc0005543
[    15.344]     BytesPerScanline: 2560
[    15.344]     XResolution: 640
[    15.344]     YResolution: 480
[    15.344]     XCharSize: 8
[    15.344]     YCharSize: 16
[    15.344]     NumberOfPlanes: 1
[    15.344]     BitsPerPixel: 32
[    15.344]     NumberOfBanks: 1
[    15.344]     MemoryModel: 6
[    15.344]     BankSize: 0
[    15.344]     NumberOfImages: 12
[    15.344]     RedMaskSize: 8
[    15.344]     RedFieldPosition: 16
[    15.344]     GreenMaskSize: 8
[    15.344]     GreenFieldPosition: 8
[    15.344]     BlueMaskSize: 8
[    15.344]     BlueFieldPosition: 0
[    15.344]     RsvdMaskSize: 0
[    15.344]     RsvdFieldPosition: 0
[    15.344]     DirectColorModeInfo: 0
[    15.344]     PhysBasePtr: 0x80000000
[    15.344]     LinBytesPerScanLine: 2560
[    15.344]     BnkNumberOfImagePages: 12
[    15.344]     LinNumberOfImagePages: 12
[    15.344]     LinRedMaskSize: 8
[    15.344]     LinRedFieldPosition: 16
[    15.344]     LinGreenMaskSize: 8
[    15.344]     LinGreenFieldPosition: 8
[    15.344]     LinBlueMaskSize: 8
[    15.344]     LinBlueFieldPosition: 0
[    15.344]     LinRsvdMaskSize: 0
[    15.344]     LinRsvdFieldPosition: 0
[    15.344]     MaxPixelClock: 400000000
[    15.345] *Mode: 122 (800x600)
[    15.345]     ModeAttributes: 0xbb
[    15.345]     WinAAttributes: 0x7
[    15.345]     WinBAttributes: 0x0
[    15.345]     WinGranularity: 64
[    15.345]     WinSize: 64
[    15.346]     WinASegment: 0xa000
[    15.346]     WinBSegment: 0x0
[    15.346]     WinFuncPtr: 0xc0005543
[    15.346]     BytesPerScanline: 3200
[    15.346]     XResolution: 800
[    15.346]     YResolution: 600
[    15.346]     XCharSize: 8
[    15.346]     YCharSize: 14
[    15.346]     NumberOfPlanes: 1
[    15.346]     BitsPerPixel: 32
[    15.346]     NumberOfBanks: 1
[    15.346]     MemoryModel: 6
[    15.346]     BankSize: 0
[    15.346]     NumberOfImages: 7
[    15.346]     RedMaskSize: 8
[    15.346]     RedFieldPosition: 16
[    15.346]     GreenMaskSize: 8
[    15.346]     GreenFieldPosition: 8
[    15.346]     BlueMaskSize: 8
[    15.346]     BlueFieldPosition: 0
[    15.346]     RsvdMaskSize: 0
[    15.346]     RsvdFieldPosition: 0
[    15.346]     DirectColorModeInfo: 0
[    15.346]     PhysBasePtr: 0x80000000
[    15.346]     LinBytesPerScanLine: 3200
[    15.346]     BnkNumberOfImagePages: 7
[    15.346]     LinNumberOfImagePages: 7
[    15.346]     LinRedMaskSize: 8
[    15.346]     LinRedFieldPosition: 16
[    15.346]     LinGreenMaskSize: 8
[    15.346]     LinGreenFieldPosition: 8
[    15.346]     LinBlueMaskSize: 8
[    15.346]     LinBlueFieldPosition: 0
[    15.346]     LinRsvdMaskSize: 0
[    15.346]     LinRsvdFieldPosition: 0
[    15.346]     MaxPixelClock: 400000000
[    15.347] *Mode: 123 (1024x768)
[    15.347]     ModeAttributes: 0xbb
[    15.347]     WinAAttributes: 0x7
[    15.347]     WinBAttributes: 0x0
[    15.347]     WinGranularity: 64
[    15.347]     WinSize: 64
[    15.347]     WinASegment: 0xa000
[    15.347]     WinBSegment: 0x0
[    15.347]     WinFuncPtr: 0xc0005543
[    15.348]     BytesPerScanline: 4096
[    15.348]     XResolution: 1024
[    15.348]     YResolution: 768
[    15.348]     XCharSize: 8
[    15.348]     YCharSize: 16
[    15.348]     NumberOfPlanes: 1
[    15.348]     BitsPerPixel: 32
[    15.348]     NumberOfBanks: 1
[    15.348]     MemoryModel: 6
[    15.348]     BankSize: 0
[    15.348]     NumberOfImages: 4
[    15.348]     RedMaskSize: 8
[    15.348]     RedFieldPosition: 16
[    15.348]     GreenMaskSize: 8
[    15.348]     GreenFieldPosition: 8
[    15.348]     BlueMaskSize: 8
[    15.348]     BlueFieldPosition: 0
[    15.348]     RsvdMaskSize: 0
[    15.348]     RsvdFieldPosition: 0
[    15.348]     DirectColorModeInfo: 0
[    15.348]     PhysBasePtr: 0x80000000
[    15.348]     LinBytesPerScanLine: 4096
[    15.348]     BnkNumberOfImagePages: 4
[    15.348]     LinNumberOfImagePages: 4
[    15.348]     LinRedMaskSize: 8
[    15.348]     LinRedFieldPosition: 16
[    15.348]     LinGreenMaskSize: 8
[    15.348]     LinGreenFieldPosition: 8
[    15.348]     LinBlueMaskSize: 8
[    15.348]     LinBlueFieldPosition: 0
[    15.348]     LinRsvdMaskSize: 0
[    15.348]     LinRsvdFieldPosition: 0
[    15.348]     MaxPixelClock: 400000000
[    15.349] Mode: 124 (1280x1024)
[    15.349]     ModeAttributes: 0xba
[    15.349]     WinAAttributes: 0x7
[    15.349]     WinBAttributes: 0x0
[    15.349]     WinGranularity: 64
[    15.349]     WinSize: 64
[    15.349]     WinASegment: 0xa000
[    15.349]     WinBSegment: 0x0
[    15.349]     WinFuncPtr: 0xc0005543
[    15.350]     BytesPerScanline: 5120
[    15.350]     XResolution: 1280
[    15.350]     YResolution: 1024
[    15.350]     XCharSize: 8
[    15.350]     YCharSize: 16
[    15.350]     NumberOfPlanes: 1
[    15.350]     BitsPerPixel: 32
[    15.350]     NumberOfBanks: 1
[    15.350]     MemoryModel: 6
[    15.350]     BankSize: 0
[    15.350]     NumberOfImages: 2
[    15.350]     RedMaskSize: 8
[    15.350]     RedFieldPosition: 16
[    15.350]     GreenMaskSize: 8
[    15.350]     GreenFieldPosition: 8
[    15.350]     BlueMaskSize: 8
[    15.350]     BlueFieldPosition: 0
[    15.350]     RsvdMaskSize: 0
[    15.350]     RsvdFieldPosition: 0
[    15.350]     DirectColorModeInfo: 0
[    15.350]     PhysBasePtr: 0x80000000
[    15.350]     LinBytesPerScanLine: 5120
[    15.350]     BnkNumberOfImagePages: 2
[    15.350]     LinNumberOfImagePages: 2
[    15.350]     LinRedMaskSize: 8
[    15.350]     LinRedFieldPosition: 16
[    15.350]     LinGreenMaskSize: 8
[    15.350]     LinGreenFieldPosition: 8
[    15.350]     LinBlueMaskSize: 8
[    15.350]     LinBlueFieldPosition: 0
[    15.350]     LinRsvdMaskSize: 0
[    15.350]     LinRsvdFieldPosition: 0
[    15.350]     MaxPixelClock: 400000000
[    15.351] Mode: 143 (1400x1050)
[    15.351]     ModeAttributes: 0xba
[    15.351]     WinAAttributes: 0x7
[    15.351]     WinBAttributes: 0x0
[    15.351]     WinGranularity: 64
[    15.351]     WinSize: 64
[    15.351]     WinASegment: 0xa000
[    15.351]     WinBSegment: 0x0
[    15.351]     WinFuncPtr: 0xc0005543
[    15.351]     BytesPerScanline: 1408
[    15.351]     XResolution: 1400
[    15.351]     YResolution: 1050
[    15.351]     XCharSize: 8
[    15.351]     YCharSize: 16
[    15.352]     NumberOfPlanes: 1
[    15.352]     BitsPerPixel: 8
[    15.352]     NumberOfBanks: 1
[    15.352]     MemoryModel: 4
[    15.352]     BankSize: 0
[    15.352]     NumberOfImages: 10
[    15.352]     RedMaskSize: 0
[    15.352]     RedFieldPosition: 0
[    15.352]     GreenMaskSize: 0
[    15.352]     GreenFieldPosition: 0
[    15.352]     BlueMaskSize: 0
[    15.352]     BlueFieldPosition: 0
[    15.352]     RsvdMaskSize: 0
[    15.352]     RsvdFieldPosition: 0
[    15.352]     DirectColorModeInfo: 0
[    15.352]     PhysBasePtr: 0x80000000
[    15.352]     LinBytesPerScanLine: 1408
[    15.352]     BnkNumberOfImagePages: 10
[    15.352]     LinNumberOfImagePages: 10
[    15.352]     LinRedMaskSize: 0
[    15.352]     LinRedFieldPosition: 0
[    15.352]     LinGreenMaskSize: 0
[    15.352]     LinGreenFieldPosition: 0
[    15.352]     LinBlueMaskSize: 0
[    15.352]     LinBlueFieldPosition: 0
[    15.352]     LinRsvdMaskSize: 0
[    15.352]     LinRsvdFieldPosition: 0
[    15.352]     MaxPixelClock: 400000000
[    15.353] Mode: 145 (1400x1050)
[    15.353]     ModeAttributes: 0xba
[    15.353]     WinAAttributes: 0x7
[    15.353]     WinBAttributes: 0x0
[    15.353]     WinGranularity: 64
[    15.353]     WinSize: 64
[    15.353]     WinASegment: 0xa000
[    15.353]     WinBSegment: 0x0
[    15.353]     WinFuncPtr: 0xc0005543
[    15.353]     BytesPerScanline: 2816
[    15.353]     XResolution: 1400
[    15.353]     YResolution: 1050
[    15.353]     XCharSize: 8
[    15.353]     YCharSize: 16
[    15.353]     NumberOfPlanes: 1
[    15.353]     BitsPerPixel: 16
[    15.354]     NumberOfBanks: 1
[    15.354]     MemoryModel: 6
[    15.354]     BankSize: 0
[    15.354]     NumberOfImages: 4
[    15.354]     RedMaskSize: 5
[    15.354]     RedFieldPosition: 11
[    15.354]     GreenMaskSize: 6
[    15.354]     GreenFieldPosition: 5
[    15.354]     BlueMaskSize: 5
[    15.354]     BlueFieldPosition: 0
[    15.354]     RsvdMaskSize: 0
[    15.354]     RsvdFieldPosition: 0
[    15.354]     DirectColorModeInfo: 0
[    15.354]     PhysBasePtr: 0x80000000
[    15.354]     LinBytesPerScanLine: 2816
[    15.354]     BnkNumberOfImagePages: 4
[    15.354]     LinNumberOfImagePages: 4
[    15.354]     LinRedMaskSize: 5
[    15.354]     LinRedFieldPosition: 11
[    15.354]     LinGreenMaskSize: 6
[    15.354]     LinGreenFieldPosition: 5
[    15.354]     LinBlueMaskSize: 5
[    15.354]     LinBlueFieldPosition: 0
[    15.354]     LinRsvdMaskSize: 0
[    15.354]     LinRsvdFieldPosition: 0
[    15.354]     MaxPixelClock: 400000000
[    15.355] Mode: 146 (1400x1050)
[    15.355]     ModeAttributes: 0xba
[    15.355]     WinAAttributes: 0x7
[    15.355]     WinBAttributes: 0x0
[    15.355]     WinGranularity: 64
[    15.355]     WinSize: 64
[    15.355]     WinASegment: 0xa000
[    15.355]     WinBSegment: 0x0
[    15.355]     WinFuncPtr: 0xc0005543
[    15.355]     BytesPerScanline: 5632
[    15.355]     XResolution: 1400
[    15.355]     YResolution: 1050
[    15.355]     XCharSize: 8
[    15.355]     YCharSize: 16
[    15.355]     NumberOfPlanes: 1
[    15.355]     BitsPerPixel: 32
[    15.355]     NumberOfBanks: 1
[    15.355]     MemoryModel: 6
[    15.355]     BankSize: 0
[    15.355]     NumberOfImages: 1
[    15.356]     RedMaskSize: 8
[    15.356]     RedFieldPosition: 16
[    15.356]     GreenMaskSize: 8
[    15.356]     GreenFieldPosition: 8
[    15.356]     BlueMaskSize: 8
[    15.356]     BlueFieldPosition: 0
[    15.356]     RsvdMaskSize: 0
[    15.356]     RsvdFieldPosition: 0
[    15.356]     DirectColorModeInfo: 0
[    15.356]     PhysBasePtr: 0x80000000
[    15.356]     LinBytesPerScanLine: 5632
[    15.356]     BnkNumberOfImagePages: 1
[    15.356]     LinNumberOfImagePages: 1
[    15.356]     LinRedMaskSize: 8
[    15.356]     LinRedFieldPosition: 16
[    15.356]     LinGreenMaskSize: 8
[    15.356]     LinGreenFieldPosition: 8
[    15.356]     LinBlueMaskSize: 8
[    15.356]     LinBlueFieldPosition: 0
[    15.356]     LinRsvdMaskSize: 0
[    15.356]     LinRsvdFieldPosition: 0
[    15.356]     MaxPixelClock: 400000000
[    15.357] Mode: 173 (1600x1200)
[    15.357]     ModeAttributes: 0xba
[    15.357]     WinAAttributes: 0x7
[    15.357]     WinBAttributes: 0x0
[    15.357]     WinGranularity: 64
[    15.357]     WinSize: 64
[    15.357]     WinASegment: 0xa000
[    15.357]     WinBSegment: 0x0
[    15.357]     WinFuncPtr: 0xc0005543
[    15.357]     BytesPerScanline: 1600
[    15.357]     XResolution: 1600
[    15.357]     YResolution: 1200
[    15.357]     XCharSize: 8
[    15.357]     YCharSize: 16
[    15.357]     NumberOfPlanes: 1
[    15.358]     BitsPerPixel: 8
[    15.358]     NumberOfBanks: 1
[    15.358]     MemoryModel: 4
[    15.358]     BankSize: 0
[    15.358]     NumberOfImages: 7
[    15.358]     RedMaskSize: 0
[    15.358]     RedFieldPosition: 0
[    15.358]     GreenMaskSize: 0
[    15.358]     GreenFieldPosition: 0
[    15.358]     BlueMaskSize: 0
[    15.358]     BlueFieldPosition: 0
[    15.358]     RsvdMaskSize: 0
[    15.358]     RsvdFieldPosition: 0
[    15.358]     DirectColorModeInfo: 0
[    15.358]     PhysBasePtr: 0x80000000
[    15.358]     LinBytesPerScanLine: 1600
[    15.358]     BnkNumberOfImagePages: 7
[    15.358]     LinNumberOfImagePages: 7
[    15.358]     LinRedMaskSize: 0
[    15.358]     LinRedFieldPosition: 0
[    15.358]     LinGreenMaskSize: 0
[    15.358]     LinGreenFieldPosition: 0
[    15.358]     LinBlueMaskSize: 0
[    15.358]     LinBlueFieldPosition: 0
[    15.358]     LinRsvdMaskSize: 0
[    15.358]     LinRsvdFieldPosition: 0
[    15.358]     MaxPixelClock: 400000000
[    15.359] Mode: 175 (1600x1200)
[    15.359]     ModeAttributes: 0xba
[    15.359]     WinAAttributes: 0x7
[    15.359]     WinBAttributes: 0x0
[    15.359]     WinGranularity: 64
[    15.359]     WinSize: 64
[    15.359]     WinASegment: 0xa000
[    15.359]     WinBSegment: 0x0
[    15.359]     WinFuncPtr: 0xc0005543
[    15.359]     BytesPerScanline: 3200
[    15.360]     XResolution: 1600
[    15.360]     YResolution: 1200
[    15.360]     XCharSize: 8
[    15.360]     YCharSize: 16
[    15.360]     NumberOfPlanes: 1
[    15.360]     BitsPerPixel: 16
[    15.360]     NumberOfBanks: 1
[    15.360]     MemoryModel: 6
[    15.360]     BankSize: 0
[    15.360]     NumberOfImages: 3
[    15.360]     RedMaskSize: 5
[    15.360]     RedFieldPosition: 11
[    15.360]     GreenMaskSize: 6
[    15.360]     GreenFieldPosition: 5
[    15.360]     BlueMaskSize: 5
[    15.360]     BlueFieldPosition: 0
[    15.360]     RsvdMaskSize: 0
[    15.360]     RsvdFieldPosition: 0
[    15.360]     DirectColorModeInfo: 0
[    15.360]     PhysBasePtr: 0x80000000
[    15.360]     LinBytesPerScanLine: 3200
[    15.360]     BnkNumberOfImagePages: 3
[    15.360]     LinNumberOfImagePages: 3
[    15.360]     LinRedMaskSize: 5
[    15.360]     LinRedFieldPosition: 11
[    15.360]     LinGreenMaskSize: 6
[    15.360]     LinGreenFieldPosition: 5
[    15.360]     LinBlueMaskSize: 5
[    15.360]     LinBlueFieldPosition: 0
[    15.360]     LinRsvdMaskSize: 0
[    15.360]     LinRsvdFieldPosition: 0
[    15.360]     MaxPixelClock: 400000000
[    15.361] Mode: 176 (1600x1200)
[    15.361]     ModeAttributes: 0xba
[    15.361]     WinAAttributes: 0x7
[    15.361]     WinBAttributes: 0x0
[    15.361]     WinGranularity: 64
[    15.361]     WinSize: 64
[    15.361]     WinASegment: 0xa000
[    15.361]     WinBSegment: 0x0
[    15.361]     WinFuncPtr: 0xc0005543
[    15.361]     BytesPerScanline: 6400
[    15.362]     XResolution: 1600
[    15.362]     YResolution: 1200
[    15.362]     XCharSize: 8
[    15.362]     YCharSize: 16
[    15.362]     NumberOfPlanes: 1
[    15.362]     BitsPerPixel: 32
[    15.362]     NumberOfBanks: 1
[    15.362]     MemoryModel: 6
[    15.362]     BankSize: 0
[    15.362]     NumberOfImages: 1
[    15.362]     RedMaskSize: 8
[    15.362]     RedFieldPosition: 16
[    15.362]     GreenMaskSize: 8
[    15.362]     GreenFieldPosition: 8
[    15.362]     BlueMaskSize: 8
[    15.362]     BlueFieldPosition: 0
[    15.362]     RsvdMaskSize: 0
[    15.362]     RsvdFieldPosition: 0
[    15.362]     DirectColorModeInfo: 0
[    15.362]     PhysBasePtr: 0x80000000
[    15.362]     LinBytesPerScanLine: 6400
[    15.362]     BnkNumberOfImagePages: 1
[    15.362]     LinNumberOfImagePages: 1
[    15.362]     LinRedMaskSize: 8
[    15.362]     LinRedFieldPosition: 16
[    15.362]     LinGreenMaskSize: 8
[    15.362]     LinGreenFieldPosition: 8
[    15.362]     LinBlueMaskSize: 8
[    15.362]     LinBlueFieldPosition: 0
[    15.362]     LinRsvdMaskSize: 0
[    15.362]     LinRsvdFieldPosition: 0
[    15.362]     MaxPixelClock: 400000000
[    15.363] Mode: 183 (1792x1344)
[    15.363]     ModeAttributes: 0xba
[    15.363]     WinAAttributes: 0x7
[    15.363]     WinBAttributes: 0x0
[    15.363]     WinGranularity: 64
[    15.363]     WinSize: 64
[    15.363]     WinASegment: 0xa000
[    15.363]     WinBSegment: 0x0
[    15.363]     WinFuncPtr: 0xc0005543
[    15.363]     BytesPerScanline: 1792
[    15.363]     XResolution: 1792
[    15.363]     YResolution: 1344
[    15.364]     XCharSize: 8
[    15.364]     YCharSize: 16
[    15.364]     NumberOfPlanes: 1
[    15.364]     BitsPerPixel: 8
[    15.364]     NumberOfBanks: 1
[    15.364]     MemoryModel: 4
[    15.364]     BankSize: 0
[    15.364]     NumberOfImages: 5
[    15.364]     RedMaskSize: 0
[    15.364]     RedFieldPosition: 0
[    15.364]     GreenMaskSize: 0
[    15.364]     GreenFieldPosition: 0
[    15.364]     BlueMaskSize: 0
[    15.364]     BlueFieldPosition: 0
[    15.364]     RsvdMaskSize: 0
[    15.364]     RsvdFieldPosition: 0
[    15.364]     DirectColorModeInfo: 0
[    15.364]     PhysBasePtr: 0x80000000
[    15.364]     LinBytesPerScanLine: 1792
[    15.364]     BnkNumberOfImagePages: 5
[    15.364]     LinNumberOfImagePages: 5
[    15.364]     LinRedMaskSize: 0
[    15.364]     LinRedFieldPosition: 0
[    15.364]     LinGreenMaskSize: 0
[    15.364]     LinGreenFieldPosition: 0
[    15.364]     LinBlueMaskSize: 0
[    15.364]     LinBlueFieldPosition: 0
[    15.364]     LinRsvdMaskSize: 0
[    15.364]     LinRsvdFieldPosition: 0
[    15.364]     MaxPixelClock: 400000000
[    15.365] Mode: 185 (1792x1344)
[    15.365]     ModeAttributes: 0xba
[    15.365]     WinAAttributes: 0x7
[    15.365]     WinBAttributes: 0x0
[    15.365]     WinGranularity: 64
[    15.365]     WinSize: 64
[    15.365]     WinASegment: 0xa000
[    15.365]     WinBSegment: 0x0
[    15.365]     WinFuncPtr: 0xc0005543
[    15.365]     BytesPerScanline: 3584
[    15.365]     XResolution: 1792
[    15.366]     YResolution: 1344
[    15.366]     XCharSize: 8
[    15.366]     YCharSize: 16
[    15.366]     NumberOfPlanes: 1
[    15.366]     BitsPerPixel: 16
[    15.366]     NumberOfBanks: 1
[    15.366]     MemoryModel: 6
[    15.366]     BankSize: 0
[    15.366]     NumberOfImages: 2
[    15.366]     RedMaskSize: 5
[    15.366]     RedFieldPosition: 11
[    15.366]     GreenMaskSize: 6
[    15.366]     GreenFieldPosition: 5
[    15.366]     BlueMaskSize: 5
[    15.366]     BlueFieldPosition: 0
[    15.366]     RsvdMaskSize: 0
[    15.366]     RsvdFieldPosition: 0
[    15.366]     DirectColorModeInfo: 0
[    15.366]     PhysBasePtr: 0x80000000
[    15.366]     LinBytesPerScanLine: 3584
[    15.366]     BnkNumberOfImagePages: 2
[    15.366]     LinNumberOfImagePages: 2
[    15.366]     LinRedMaskSize: 5
[    15.366]     LinRedFieldPosition: 11
[    15.366]     LinGreenMaskSize: 6
[    15.366]     LinGreenFieldPosition: 5
[    15.366]     LinBlueMaskSize: 5
[    15.366]     LinBlueFieldPosition: 0
[    15.366]     LinRsvdMaskSize: 0
[    15.366]     LinRsvdFieldPosition: 0
[    15.366]     MaxPixelClock: 400000000
[    15.367] Mode: 186 (1792x1344)
[    15.367]     ModeAttributes: 0xba
[    15.367]     WinAAttributes: 0x7
[    15.367]     WinBAttributes: 0x0
[    15.367]     WinGranularity: 64
[    15.367]     WinSize: 64
[    15.367]     WinASegment: 0xa000
[    15.367]     WinBSegment: 0x0
[    15.367]     WinFuncPtr: 0xc0005543
[    15.367]     BytesPerScanline: 7168
[    15.367]     XResolution: 1792
[    15.368]     YResolution: 1344
[    15.368]     XCharSize: 8
[    15.368]     YCharSize: 16
[    15.368]     NumberOfPlanes: 1
[    15.368]     BitsPerPixel: 32
[    15.368]     NumberOfBanks: 1
[    15.368]     MemoryModel: 6
[    15.368]     BankSize: 0
[    15.368]     NumberOfImages: 1
[    15.368]     RedMaskSize: 8
[    15.368]     RedFieldPosition: 16
[    15.368]     GreenMaskSize: 8
[    15.368]     GreenFieldPosition: 8
[    15.368]     BlueMaskSize: 8
[    15.368]     BlueFieldPosition: 0
[    15.368]     RsvdMaskSize: 0
[    15.368]     RsvdFieldPosition: 0
[    15.368]     DirectColorModeInfo: 0
[    15.368]     PhysBasePtr: 0x80000000
[    15.368]     LinBytesPerScanLine: 7168
[    15.368]     BnkNumberOfImagePages: 1
[    15.368]     LinNumberOfImagePages: 1
[    15.368]     LinRedMaskSize: 8
[    15.368]     LinRedFieldPosition: 16
[    15.368]     LinGreenMaskSize: 8
[    15.368]     LinGreenFieldPosition: 8
[    15.368]     LinBlueMaskSize: 8
[    15.368]     LinBlueFieldPosition: 0
[    15.368]     LinRsvdMaskSize: 0
[    15.368]     LinRsvdFieldPosition: 0
[    15.368]     MaxPixelClock: 400000000
[    15.369] Mode: 1d3 (1856x1392)
[    15.369]     ModeAttributes: 0xba
[    15.369]     WinAAttributes: 0x7
[    15.369]     WinBAttributes: 0x0
[    15.369]     WinGranularity: 64
[    15.369]     WinSize: 64
[    15.369]     WinASegment: 0xa000
[    15.369]     WinBSegment: 0x0
[    15.369]     WinFuncPtr: 0xc0005543
[    15.369]     BytesPerScanline: 1856
[    15.369]     XResolution: 1856
[    15.370]     YResolution: 1392
[    15.370]     XCharSize: 8
[    15.370]     YCharSize: 16
[    15.370]     NumberOfPlanes: 1
[    15.370]     BitsPerPixel: 8
[    15.370]     NumberOfBanks: 1
[    15.370]     MemoryModel: 4
[    15.370]     BankSize: 0
[    15.370]     NumberOfImages: 5
[    15.370]     RedMaskSize: 0
[    15.370]     RedFieldPosition: 0
[    15.370]     GreenMaskSize: 0
[    15.370]     GreenFieldPosition: 0
[    15.370]     BlueMaskSize: 0
[    15.370]     BlueFieldPosition: 0
[    15.370]     RsvdMaskSize: 0
[    15.370]     RsvdFieldPosition: 0
[    15.370]     DirectColorModeInfo: 0
[    15.370]     PhysBasePtr: 0x80000000
[    15.370]     LinBytesPerScanLine: 1856
[    15.370]     BnkNumberOfImagePages: 5
[    15.370]     LinNumberOfImagePages: 5
[    15.370]     LinRedMaskSize: 0
[    15.370]     LinRedFieldPosition: 0
[    15.370]     LinGreenMaskSize: 0
[    15.370]     LinGreenFieldPosition: 0
[    15.370]     LinBlueMaskSize: 0
[    15.370]     LinBlueFieldPosition: 0
[    15.370]     LinRsvdMaskSize: 0
[    15.370]     LinRsvdFieldPosition: 0
[    15.370]     MaxPixelClock: 400000000
[    15.371] Mode: 1d5 (1856x1392)
[    15.371]     ModeAttributes: 0xba
[    15.371]     WinAAttributes: 0x7
[    15.371]     WinBAttributes: 0x0
[    15.371]     WinGranularity: 64
[    15.371]     WinSize: 64
[    15.371]     WinASegment: 0xa000
[    15.371]     WinBSegment: 0x0
[    15.371]     WinFuncPtr: 0xc0005543
[    15.372]     BytesPerScanline: 3712
[    15.372]     XResolution: 1856
[    15.372]     YResolution: 1392
[    15.372]     XCharSize: 8
[    15.372]     YCharSize: 16
[    15.372]     NumberOfPlanes: 1
[    15.372]     BitsPerPixel: 16
[    15.372]     NumberOfBanks: 1
[    15.372]     MemoryModel: 6
[    15.372]     BankSize: 0
[    15.372]     NumberOfImages: 2
[    15.372]     RedMaskSize: 5
[    15.372]     RedFieldPosition: 11
[    15.372]     GreenMaskSize: 6
[    15.372]     GreenFieldPosition: 5
[    15.372]     BlueMaskSize: 5
[    15.372]     BlueFieldPosition: 0
[    15.372]     RsvdMaskSize: 0
[    15.372]     RsvdFieldPosition: 0
[    15.372]     DirectColorModeInfo: 0
[    15.372]     PhysBasePtr: 0x80000000
[    15.372]     LinBytesPerScanLine: 3712
[    15.372]     BnkNumberOfImagePages: 2
[    15.372]     LinNumberOfImagePages: 2
[    15.372]     LinRedMaskSize: 5
[    15.372]     LinRedFieldPosition: 11
[    15.372]     LinGreenMaskSize: 6
[    15.372]     LinGreenFieldPosition: 5
[    15.372]     LinBlueMaskSize: 5
[    15.372]     LinBlueFieldPosition: 0
[    15.372]     LinRsvdMaskSize: 0
[    15.372]     LinRsvdFieldPosition: 0
[    15.372]     MaxPixelClock: 400000000
[    15.373] Mode: 1d6 (1856x1392)
[    15.373]     ModeAttributes: 0xba
[    15.373]     WinAAttributes: 0x7
[    15.374]     WinBAttributes: 0x0
[    15.374]     WinGranularity: 64
[    15.374]     WinSize: 64
[    15.374]     WinASegment: 0xa000
[    15.374]     WinBSegment: 0x0
[    15.374]     WinFuncPtr: 0xc0005543
[    15.374]     BytesPerScanline: 7424
[    15.374]     XResolution: 1856
[    15.374]     YResolution: 1392
[    15.374]     XCharSize: 8
[    15.374]     YCharSize: 16
[    15.374]     NumberOfPlanes: 1
[    15.374]     BitsPerPixel: 32
[    15.374]     NumberOfBanks: 1
[    15.374]     MemoryModel: 6
[    15.374]     BankSize: 0
[    15.374]     NumberOfImages: 1
[    15.374]     RedMaskSize: 8
[    15.374]     RedFieldPosition: 16
[    15.374]     GreenMaskSize: 8
[    15.374]     GreenFieldPosition: 8
[    15.374]     BlueMaskSize: 8
[    15.374]     BlueFieldPosition: 0
[    15.374]     RsvdMaskSize: 0
[    15.374]     RsvdFieldPosition: 0
[    15.374]     DirectColorModeInfo: 0
[    15.374]     PhysBasePtr: 0x80000000
[    15.374]     LinBytesPerScanLine: 7424
[    15.374]     BnkNumberOfImagePages: 1
[    15.374]     LinNumberOfImagePages: 1
[    15.374]     LinRedMaskSize: 8
[    15.374]     LinRedFieldPosition: 16
[    15.374]     LinGreenMaskSize: 8
[    15.374]     LinGreenFieldPosition: 8
[    15.374]     LinBlueMaskSize: 8
[    15.374]     LinBlueFieldPosition: 0
[    15.374]     LinRsvdMaskSize: 0
[    15.374]     LinRsvdFieldPosition: 0
[    15.374]     MaxPixelClock: 400000000
[    15.376] Mode: 1e3 (1920x1440)
[    15.376]     ModeAttributes: 0xba
[    15.376]     WinAAttributes: 0x7
[    15.376]     WinBAttributes: 0x0
[    15.376]     WinGranularity: 64
[    15.376]     WinSize: 64
[    15.376]     WinASegment: 0xa000
[    15.376]     WinBSegment: 0x0
[    15.376]     WinFuncPtr: 0xc0005543
[    15.376]     BytesPerScanline: 1920
[    15.376]     XResolution: 1920
[    15.376]     YResolution: 1440
[    15.376]     XCharSize: 8
[    15.376]     YCharSize: 16
[    15.376]     NumberOfPlanes: 1
[    15.376]     BitsPerPixel: 8
[    15.376]     NumberOfBanks: 1
[    15.376]     MemoryModel: 4
[    15.376]     BankSize: 0
[    15.376]     NumberOfImages: 4
[    15.376]     RedMaskSize: 0
[    15.376]     RedFieldPosition: 0
[    15.376]     GreenMaskSize: 0
[    15.376]     GreenFieldPosition: 0
[    15.376]     BlueMaskSize: 0
[    15.376]     BlueFieldPosition: 0
[    15.376]     RsvdMaskSize: 0
[    15.376]     RsvdFieldPosition: 0
[    15.376]     DirectColorModeInfo: 0
[    15.376]     PhysBasePtr: 0x80000000
[    15.376]     LinBytesPerScanLine: 1920
[    15.376]     BnkNumberOfImagePages: 4
[    15.376]     LinNumberOfImagePages: 4
[    15.376]     LinRedMaskSize: 0
[    15.376]     LinRedFieldPosition: 0
[    15.376]     LinGreenMaskSize: 0
[    15.376]     LinGreenFieldPosition: 0
[    15.376]     LinBlueMaskSize: 0
[    15.376]     LinBlueFieldPosition: 0
[    15.376]     LinRsvdMaskSize: 0
[    15.376]     LinRsvdFieldPosition: 0
[    15.376]     MaxPixelClock: 400000000
[    15.378] Mode: 1e5 (1920x1440)
[    15.378]     ModeAttributes: 0xba
[    15.378]     WinAAttributes: 0x7
[    15.378]     WinBAttributes: 0x0
[    15.378]     WinGranularity: 64
[    15.378]     WinSize: 64
[    15.378]     WinASegment: 0xa000
[    15.378]     WinBSegment: 0x0
[    15.378]     WinFuncPtr: 0xc0005543
[    15.378]     BytesPerScanline: 3840
[    15.378]     XResolution: 1920
[    15.378]     YResolution: 1440
[    15.378]     XCharSize: 8
[    15.378]     YCharSize: 16
[    15.378]     NumberOfPlanes: 1
[    15.378]     BitsPerPixel: 16
[    15.378]     NumberOfBanks: 1
[    15.378]     MemoryModel: 6
[    15.378]     BankSize: 0
[    15.378]     NumberOfImages: 2
[    15.378]     RedMaskSize: 5
[    15.378]     RedFieldPosition: 11
[    15.378]     GreenMaskSize: 6
[    15.378]     GreenFieldPosition: 5
[    15.378]     BlueMaskSize: 5
[    15.378]     BlueFieldPosition: 0
[    15.378]     RsvdMaskSize: 0
[    15.378]     RsvdFieldPosition: 0
[    15.378]     DirectColorModeInfo: 0
[    15.378]     PhysBasePtr: 0x80000000
[    15.378]     LinBytesPerScanLine: 3840
[    15.378]     BnkNumberOfImagePages: 2
[    15.378]     LinNumberOfImagePages: 2
[    15.378]     LinRedMaskSize: 5
[    15.378]     LinRedFieldPosition: 11
[    15.378]     LinGreenMaskSize: 6
[    15.378]     LinGreenFieldPosition: 5
[    15.378]     LinBlueMaskSize: 5
[    15.378]     LinBlueFieldPosition: 0
[    15.378]     LinRsvdMaskSize: 0
[    15.378]     LinRsvdFieldPosition: 0
[    15.378]     MaxPixelClock: 400000000
[    15.380] Mode: 1e6 (1920x1440)
[    15.380]     ModeAttributes: 0xba
[    15.380]     WinAAttributes: 0x7
[    15.380]     WinBAttributes: 0x0
[    15.380]     WinGranularity: 64
[    15.380]     WinSize: 64
[    15.380]     WinASegment: 0xa000
[    15.380]     WinBSegment: 0x0
[    15.380]     WinFuncPtr: 0xc0005543
[    15.380]     BytesPerScanline: 7680
[    15.380]     XResolution: 1920
[    15.380]     YResolution: 1440
[    15.380]     XCharSize: 8
[    15.380]     YCharSize: 16
[    15.380]     NumberOfPlanes: 1
[    15.380]     BitsPerPixel: 32
[    15.380]     NumberOfBanks: 1
[    15.380]     MemoryModel: 6
[    15.380]     BankSize: 0
[    15.380]     NumberOfImages: 1
[    15.380]     RedMaskSize: 8
[    15.380]     RedFieldPosition: 16
[    15.380]     GreenMaskSize: 8
[    15.380]     GreenFieldPosition: 8
[    15.380]     BlueMaskSize: 8
[    15.380]     BlueFieldPosition: 0
[    15.380]     RsvdMaskSize: 0
[    15.380]     RsvdFieldPosition: 0
[    15.380]     DirectColorModeInfo: 0
[    15.380]     PhysBasePtr: 0x80000000
[    15.380]     LinBytesPerScanLine: 7680
[    15.380]     BnkNumberOfImagePages: 1
[    15.380]     LinNumberOfImagePages: 1
[    15.380]     LinRedMaskSize: 8
[    15.380]     LinRedFieldPosition: 16
[    15.380]     LinGreenMaskSize: 8
[    15.380]     LinGreenFieldPosition: 8
[    15.380]     LinBlueMaskSize: 8
[    15.380]     LinBlueFieldPosition: 0
[    15.380]     LinRsvdMaskSize: 0
[    15.380]     LinRsvdFieldPosition: 0
[    15.380]     MaxPixelClock: 400000000
[    15.380] 
[    15.380] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    15.380] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    15.380] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    15.381] (WW) VESA(0): Unable to estimate virtual size
[    15.381] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    15.381] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    15.381] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    15.381] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    15.381] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    15.381] (WW) VESA(0): Unable to estimate virtual size
[    15.381] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    15.381] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    15.381] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[    15.381] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[    15.381] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[    15.381] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    15.381] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    15.381] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    15.381] (**) VESA(0): *Built-in mode "1024x768"
[    15.381] (**) VESA(0): Display dimensions: (350, 190) mm
[    15.381] (**) VESA(0): DPI set to (74, 102)
[    15.381] (**) VESA(0): Using "Shadow Framebuffer"
[    15.381] (II) Loading sub module "shadow"
[    15.381] (II) LoadModule: "shadow"
[    15.382] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.382] (II) Module shadow: vendor="X.Org Foundation"
[    15.382]     compiled for 1.9.0, module version = 1.1.0
[    15.382]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.382] (II) Loading sub module "fb"
[    15.382] (II) LoadModule: "fb"
[    15.383] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.383] (II) Module fb: vendor="X.Org Foundation"
[    15.383]     compiled for 1.9.0, module version = 1.0.0
[    15.383]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.383] (II) UnloadModule: "radeon"
[    15.383] (II) Unloading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    15.383] (II) UnloadModule: "fbdev"
[    15.383] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.383] (II) UnloadModule: "fbdevhw"
[    15.383] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    15.383] (==) Depth 24 pixmap format is 32 bpp
[    15.383] (II) Loading sub module "int10"
[    15.383] (II) LoadModule: "int10"
[    15.384] (II) Reloading /usr/lib/xorg/modules/libint10.so
[    15.384] (II) VESA(0): initializing int10
[    15.390] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    15.390] (II) VESA(0): VESA BIOS detected
[    15.390] (II) VESA(0): VESA VBE Version 3.0
[    15.390] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    15.390] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    15.390] (II) VESA(0): VESA VBE OEM Software Rev: 12.37
[    15.390] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    15.390] (II) VESA(0): VESA VBE OEM Product: WRESTLER
[    15.390] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    15.395] (II) VESA(0): virtual address = 0xb65fa000,
    physical address = 0x80000000, size = 16777216
[    15.414] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[    15.739] (==) VESA(0): Default visual is TrueColor
[    15.740] (==) VESA(0): Backing store disabled
[    15.740] (==) VESA(0): DPMS enabled
[    15.740] (==) RandR enabled
[    15.740] (II) Initializing built-in extension Generic Event Extension
[    15.740] (II) Initializing built-in extension SHAPE
[    15.740] (II) Initializing built-in extension MIT-SHM
[    15.740] (II) Initializing built-in extension XInputExtension
[    15.740] (II) Initializing built-in extension XTEST
[    15.740] (II) Initializing built-in extension BIG-REQUESTS
[    15.740] (II) Initializing built-in extension SYNC
[    15.740] (II) Initializing built-in extension XKEYBOARD
[    15.740] (II) Initializing built-in extension XC-MISC
[    15.740] (II) Initializing built-in extension SECURITY
[    15.740] (II) Initializing built-in extension XINERAMA
[    15.740] (II) Initializing built-in extension XFIXES
[    15.740] (II) Initializing built-in extension RENDER
[    15.740] (II) Initializing built-in extension RANDR
[    15.740] (II) Initializing built-in extension COMPOSITE
[    15.740] (II) Initializing built-in extension DAMAGE
[    15.740] (II) Initializing built-in extension GESTURE
[    15.761] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.761] (II) AIGLX: Screen 0 is not DRI capable
[    15.766] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    15.766] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    15.807] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.822] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    15.822] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.822] (II) LoadModule: "evdev"
[    15.823] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.823] (II) Module evdev: vendor="X.Org Foundation"
[    15.823]     compiled for 1.9.0, module version = 2.3.2
[    15.823]     Module class: X.Org XInput Driver
[    15.823]     ABI class: X.Org XInput driver, version 11.0
[    15.823] (**) Power Button: always reports core events
[    15.823] (**) Power Button: Device: "/dev/input/event3"
[    15.832] (II) Power Button: Found keys
[    15.832] (II) Power Button: Configuring as keyboard
[    15.832] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.832] (**) Option "xkb_rules" "evdev"
[    15.832] (**) Option "xkb_model" "pc105"
[    15.832] (**) Option "xkb_layout" "us"
[    15.832] (**) Option "xkb_variant" "dvorak"
[    15.832] (**) Option "xkb_options" "lv3:ralt_switch"
[    15.837] (II) XKB: reuse xkmfile /var/lib/xkb/server-6F86FD73C5E4C040CF174C28CF7A029ECAC10E5B.xkm
[    15.838] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    15.839] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.839] (**) Video Bus: always reports core events
[    15.839] (**) Video Bus: Device: "/dev/input/event5"
[    15.856] (II) Video Bus: Found keys
[    15.856] (II) Video Bus: Configuring as keyboard
[    15.856] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    15.856] (**) Option "xkb_rules" "evdev"
[    15.856] (**) Option "xkb_model" "pc105"
[    15.856] (**) Option "xkb_layout" "us"
[    15.856] (**) Option "xkb_variant" "dvorak"
[    15.856] (**) Option "xkb_options" "lv3:ralt_switch"
[    15.859] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.859] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.859] (**) Power Button: always reports core events
[    15.859] (**) Power Button: Device: "/dev/input/event0"
[    15.876] (II) Power Button: Found keys
[    15.876] (II) Power Button: Configuring as keyboard
[    15.876] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.876] (**) Option "xkb_rules" "evdev"
[    15.876] (**) Option "xkb_model" "pc105"
[    15.876] (**) Option "xkb_layout" "us"
[    15.876] (**) Option "xkb_variant" "dvorak"
[    15.876] (**) Option "xkb_options" "lv3:ralt_switch"
[    15.877] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    15.877] (II) No input driver/identifier specified (ignoring)
[    15.877] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    15.877] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    15.878] (**) Sleep Button: always reports core events
[    15.878] (**) Sleep Button: Device: "/dev/input/event1"
[    15.896] (II) Sleep Button: Found keys
[    15.896] (II) Sleep Button: Configuring as keyboard
[    15.896] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    15.896] (**) Option "xkb_rules" "evdev"
[    15.896] (**) Option "xkb_model" "pc105"
[    15.896] (**) Option "xkb_layout" "us"
[    15.896] (**) Option "xkb_variant" "dvorak"
[    15.896] (**) Option "xkb_options" "lv3:ralt_switch"
[    15.901] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event6)
[    15.902] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    15.902] (**) 1.3M WebCam: always reports core events
[    15.902] (**) 1.3M WebCam: Device: "/dev/input/event6"
[    15.916] (II) 1.3M WebCam: Found keys
[    15.916] (II) 1.3M WebCam: Configuring as keyboard
[    15.916] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD)
[    15.916] (**) Option "xkb_rules" "evdev"
[    15.916] (**) Option "xkb_model" "pc105"
[    15.916] (**) Option "xkb_layout" "us"
[    15.916] (**) Option "xkb_variant" "dvorak"
[    15.916] (**) Option "xkb_options" "lv3:ralt_switch"
[    15.920] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    15.920] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.920] (**) AT Translated Set 2 keyboard: always reports core events
[    15.920] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    15.936] (II) AT Translated Set 2 keyboard: Found keys
[    15.936] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    15.936] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    15.936] (**) Option "xkb_rules" "evdev"
[    15.936] (**) Option "xkb_model" "pc105"
[    15.936] (**) Option "xkb_layout" "us"
[    15.936] (**) Option "xkb_variant" "dvorak"
[    15.936] (**) Option "xkb_options" "lv3:ralt_switch"
[    15.937] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    15.937] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    15.937] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    15.937] (II) LoadModule: "synaptics"
[    15.938] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    15.938] (II) Module synaptics: vendor="X.Org Foundation"
[    15.938]     compiled for 1.9.0, module version = 1.2.2
[    15.938]     Module class: X.Org XInput Driver
[    15.938]     ABI class: X.Org XInput driver, version 11.0
[    15.938] (II) Synaptics touchpad driver version 1.2.2
[    15.938] (**) Option "Device" "/dev/input/event7"
[    15.988] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    15.988] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    15.988] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    15.988] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    15.988] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    16.020] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.020] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.036] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    16.036] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.036] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    16.036] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.036] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.068] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    16.068] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.068] (II) No input driver/identifier specified (ignoring)
```

Thanks Afishionado and khelben1979 for the suggestions and link--I will check them out.
hreichgott

---

### Post by hreichgott on 2011-03-08
Just checking, as I look at the log, it looks as if Xorg recognizes that the graphics card has 1366x768 resolution, searches through all its available modes, finds pretty much everything except 1366x768, then falls back to 1024x768 and unloads the radeon driver.

Is that what it looks like to you?

---

### Post by hreichgott on 2011-03-08
Ok, khelben1979, the instructions on askubuntu.com are to boot into a root terminal, run X -configure, and copy the resulting xorg.conf to /etc/X11.

Running X -configure resulted in a segmentation fault. Here is the log
```
[    33.168] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    33.168] X Protocol Version 11, Revision 0
[    33.168] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    33.168] Current Operating System: Linux Data 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686
[    33.169] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=8769c21a-9b5e-4e6b-8ddf-22882e559d6e ro single
[    33.169] Build Date: 09 January 2011  12:14:58PM
[    33.169] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    33.169] Current version of pixman: 0.18.4
[    33.169]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    33.169] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.170] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar  8 11:35:59 2011
[    33.170] (II) Loader magic: 0x81f9b00
[    33.170] (II) Module ABI versions:
[    33.170]     X.Org ANSI C Emulation: 0.4
[    33.170]     X.Org Video Driver: 8.0
[    33.170]     X.Org XInput driver : 11.0
[    33.170]     X.Org Server Extension : 4.0
[    33.172] (--) PCI:*(0:0:1:0) 1002:9802:1025:0520 rev 0, Mem @ 0x80000000/268435456, 0x90500000/262144, I/O @ 0x00004000/256
[    33.173] List of video drivers:
[    33.173]     tdfx
[    33.173]     intel
[    33.173]     r128
[    33.174]     ztv
[    33.174]     vmware
[    33.174]     rendition
[    33.174]     siliconmotion
[    33.174]     nouveau
[    33.174]     i740
[    33.174]     ati
[    33.174]     sis
[    33.175]     openchrome
[    33.175]     nv
[    33.175]     neomagic
[    33.175]     voodoo
[    33.175]     mga
[    33.175]     tseng
[    33.175]     mach64
[    33.175]     ark
[    33.175]     radeon
[    33.176]     apm
[    33.176]     s3
[    33.176]     trident
[    33.176]     sisusb
[    33.176]     s3virge
[    33.176]     savage
[    33.176]     geode
[    33.176]     cirrus
[    33.177]     vmwlegacy
[    33.177]     chips
[    33.177]     i128
[    33.177]     fbdev
[    33.177]     vesa
[    33.177] (II) LoadModule: "tdfx"
[    33.177] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[    33.193] (II) Module tdfx: vendor="X.Org Foundation"
[    33.193]     compiled for 1.8.99.905, module version = 1.4.3
[    33.193]     Module class: X.Org Video Driver
[    33.193]     ABI class: X.Org Video Driver, version 8.0
[    33.193] (II) LoadModule: "intel"
[    33.193] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    33.210] (II) Module intel: vendor="X.Org Foundation"
[    33.210]     compiled for 1.9.0, module version = 2.13.901
[    33.210]     Module class: X.Org Video Driver
[    33.210]     ABI class: X.Org Video Driver, version 8.0
[    33.210] (II) LoadModule: "r128"
[    33.210] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    33.214] (II) Module r128: vendor="X.Org Foundation"
[    33.214]     compiled for 1.8.99.905, module version = 6.8.1
[    33.214]     Module class: X.Org Video Driver
[    33.214]     ABI class: X.Org Video Driver, version 8.0
[    33.214] (II) LoadModule: "ztv"
[    33.214] (II) Loading /usr/lib/xorg/modules/drivers/ztv_drv.so
[    33.215] (II) Module ztv: vendor="X.Org Foundation"
[    33.215]     compiled for 1.9.0, module version = 0.0.1
[    33.215]     ABI class: X.Org Video Driver, version 8.0
[    33.215] (II) LoadModule: "vmware"
[    33.215] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[    33.221] (II) Module vmware: vendor="X.Org Foundation"
[    33.221]     compiled for 1.8.99.905, module version = 11.0.1
[    33.221]     Module class: X.Org Video Driver
[    33.221]     ABI class: X.Org Video Driver, version 8.0
[    33.221] (II) LoadModule: "vmwgfx"
[    33.229] (WW) Warning, couldn't open module vmwgfx
[    33.229] (II) UnloadModule: "vmwgfx"
[    33.229] (EE) Failed to load module "vmwgfx" (module does not exist, 0)
[    33.229] (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
[    33.229] (II) vmware: Using vmwlegacy driver everything is fine.
[    33.229] (II) LoadModule: "vmwlegacy"
[    33.229] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[    33.231] (II) Module vmwlegacy: vendor="X.Org Foundation"
[    33.231]     compiled for 1.8.99.905, module version = 11.0.1
[    33.231]     Module class: X.Org Video Driver
[    33.231]     ABI class: X.Org Video Driver, version 8.0
[    33.231] (II) LoadModule: "rendition"
[    33.231] (II) Loading /usr/lib/xorg/modules/drivers/rendition_drv.so
[    33.240] (II) Module rendition: vendor="X.Org Foundation"
[    33.240]     compiled for 1.8.99.905, module version = 4.2.4
[    33.241]     Module class: X.Org Video Driver
[    33.241]     ABI class: X.Org Video Driver, version 8.0
[    33.241] (II) LoadModule: "siliconmotion"
[    33.241] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[    33.249] (II) Module siliconmotion: vendor="X.Org Foundation"
[    33.249]     compiled for 1.8.99.905, module version = 1.7.4
[    33.249]     Module class: X.Org Video Driver
[    33.249]     ABI class: X.Org Video Driver, version 8.0
[    33.249] (II) LoadModule: "nouveau"
[    33.249] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    33.260] (II) Module nouveau: vendor="X.Org Foundation"
[    33.260]     compiled for 1.8.99.905, module version = 0.0.16
[    33.260]     Module class: X.Org Video Driver
[    33.260]     ABI class: X.Org Video Driver, version 8.0
[    33.260] (II) LoadModule: "i740"
[    33.260] (II) Loading /usr/lib/xorg/modules/drivers/i740_drv.so
[    33.268] (II) Module i740: vendor="X.Org Foundation"
[    33.268]     compiled for 1.8.99.905, module version = 1.3.2
[    33.268]     Module class: X.Org Video Driver
[    33.268]     ABI class: X.Org Video Driver, version 8.0
[    33.268] (II) LoadModule: "ati"
[    33.268] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    33.268] (II) Module ati: vendor="X.Org Foundation"
[    33.268]     compiled for 1.9.0, module version = 6.13.2
[    33.268]     Module class: X.Org Video Driver
[    33.268]     ABI class: X.Org Video Driver, version 8.0
[    33.268] (II) LoadModule: "sis"
[    33.268] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    33.280] (II) Module sis: vendor="X.Org Foundation"
[    33.280]     compiled for 1.8.99.905, module version = 0.10.3
[    33.280]     Module class: X.Org Video Driver
[    33.280]     ABI class: X.Org Video Driver, version 8.0
[    33.280] (II) LoadModule: "openchrome"
[    33.280] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[    33.300] (II) Module openchrome: vendor="http://openchrome.org/"
[    33.300]     compiled for 1.8.99.905, module version = 0.2.904
[    33.301]     Module class: X.Org Video Driver
[    33.301]     ABI class: X.Org Video Driver, version 8.0
[    33.301] (II) LoadModule: "nv"
[    33.301] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[    33.303] (II) Module nv: vendor="X.Org Foundation"
[    33.303]     compiled for 1.8.99.905, module version = 2.1.17
[    33.303]     Module class: X.Org Video Driver
[    33.303]     ABI class: X.Org Video Driver, version 8.0
[    33.303] (II) LoadModule: "neomagic"
[    33.303] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[    33.304] (II) Module neomagic: vendor="X.Org Foundation"
[    33.304]     compiled for 1.8.99.905, module version = 1.2.4
[    33.304]     Module class: X.Org Video Driver
[    33.304]     ABI class: X.Org Video Driver, version 8.0
[    33.304] (II) LoadModule: "voodoo"
[    33.304] (II) Loading /usr/lib/xorg/modules/drivers/voodoo_drv.so
[    33.305] (II) Module voodoo: vendor="X.Org Foundation"
[    33.305]     compiled for 1.8.99.905, module version = 1.1.0
[    33.305]     Module class: X.Org Video Driver
[    33.305]     ABI class: X.Org Video Driver, version 8.0
[    33.305] (II) LoadModule: "mga"
[    33.305] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[    33.311] (II) Module mga: vendor="X.Org Foundation"
[    33.311]     compiled for 1.8.99.905, module version = 1.4.11
[    33.311]     Module class: X.Org Video Driver
[    33.311]     ABI class: X.Org Video Driver, version 8.0
[    33.312] (II) LoadModule: "tseng"
[    33.312] (II) Loading /usr/lib/xorg/modules/drivers/tseng_drv.so
[    33.312] (II) Module tseng: vendor="X.Org Foundation"
[    33.313]     compiled for 1.8.99.905, module version = 1.1.0
[    33.313]     Module class: X.Org Video Driver
[    33.313]     ABI class: X.Org Video Driver, version 8.0
[    33.313] (II) LoadModule: "mach64"
[    33.313] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    33.314] (II) Module mach64: vendor="X.Org Foundation"
[    33.314]     compiled for 1.8.99.905, module version = 6.8.2
[    33.314]     Module class: X.Org Video Driver
[    33.314]     ABI class: X.Org Video Driver, version 8.0
[    33.314] (II) LoadModule: "ark"
[    33.314] (II) Loading /usr/lib/xorg/modules/drivers/ark_drv.so
[    33.324] (II) Module ark: vendor="X.Org Foundation"
[    33.324]     compiled for 1.8.99.905, module version = 0.7.2
[    33.324]     Module class: X.Org Video Driver
[    33.324]     ABI class: X.Org Video Driver, version 8.0
[    33.324] (II) LoadModule: "radeon"
[    33.324] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    33.325] (II) Module radeon: vendor="X.Org Foundation"
[    33.325]     compiled for 1.9.0, module version = 6.13.2
[    33.325]     Module class: X.Org Video Driver
[    33.325]     ABI class: X.Org Video Driver, version 8.0
[    33.325] (II) LoadModule: "apm"
[    33.325] (II) Loading /usr/lib/xorg/modules/drivers/apm_drv.so
[    33.336] (II) Module apm: vendor="X.Org Foundation"
[    33.336]     compiled for 1.8.99.905, module version = 1.2.3
[    33.336]     Module class: X.Org Video Driver
[    33.336]     ABI class: X.Org Video Driver, version 8.0
[    33.336] (II) LoadModule: "s3"
[    33.337] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[    33.341] (II) Module s3: vendor="X.Org Foundation"
[    33.341]     compiled for 1.8.99.905, module version = 0.6.3
[    33.341]     Module class: X.Org Video Driver
[    33.341]     ABI class: X.Org Video Driver, version 8.0
[    33.341] (II) LoadModule: "trident"
[    33.341] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[    33.343] (II) Module trident: vendor="X.Org Foundation"
[    33.343]     compiled for 1.8.99.905, module version = 1.3.4
[    33.343]     Module class: X.Org Video Driver
[    33.343]     ABI class: X.Org Video Driver, version 8.0
[    33.343] (II) LoadModule: "sisusb"
[    33.343] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[    33.344] (II) Module sisusb: vendor="X.Org Foundation"
[    33.344]     compiled for 1.8.99.905, module version = 0.9.4
[    33.344]     Module class: X.Org Video Driver
[    33.344]     ABI class: X.Org Video Driver, version 8.0
[    33.344] (II) LoadModule: "s3virge"
[    33.344] (II) Loading /usr/lib/xorg/modules/drivers/s3virge_drv.so
[    33.345] (II) Module s3virge: vendor="X.Org Foundation"
[    33.345]     compiled for 1.8.99.905, module version = 1.10.4
[    33.345]     Module class: X.Org Video Driver
[    33.345]     ABI class: X.Org Video Driver, version 8.0
[    33.345] (II) LoadModule: "savage"
[    33.345] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[    33.347] (II) Module savage: vendor="X.Org Foundation"
[    33.347]     compiled for 1.8.99.905, module version = 2.3.1
[    33.347]     Module class: X.Org Video Driver
[    33.347]     ABI class: X.Org Video Driver, version 8.0
[    33.347] (II) LoadModule: "geode"
[    33.347] (II) Loading /usr/lib/xorg/modules/drivers/geode_drv.so
[    33.355] (II) Module geode: vendor="X.Org Foundation"
[    33.355]     compiled for 1.9.0, module version = 2.11.9
[    33.356]     Module class: X.Org Video Driver
[    33.356]     ABI class: X.Org Video Driver, version 8.0
[    33.356] (II) LoadModule: "cirrus"
[    33.356] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[    33.356] (II) Module cirrus: vendor="X.Org Foundation"
[    33.356]     compiled for 1.8.99.905, module version = 1.3.2
[    33.356]     Module class: X.Org Video Driver
[    33.356]     ABI class: X.Org Video Driver, version 8.0
[    33.356] (II) LoadModule: "vmwlegacy"
[    33.357] (II) Reloading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[    33.357] (II) UnloadModule: "vmwlegacy"
[    33.357] (II) Failed to load module "vmwlegacy" (already loaded, -1075873928)
[    33.357] (II) LoadModule: "chips"
[    33.357] (II) Loading /usr/lib/xorg/modules/drivers/chips_drv.so
[    33.371] (II) Module chips: vendor="X.Org Foundation"
[    33.371]     compiled for 1.8.99.905, module version = 1.2.3
[    33.371]     Module class: X.Org Video Driver
[    33.371]     ABI class: X.Org Video Driver, version 8.0
[    33.371] (II) LoadModule: "i128"
[    33.372] (II) Loading /usr/lib/xorg/modules/drivers/i128_drv.so
[    33.372] (II) Module i128: vendor="X.Org Foundation"
[    33.372]     compiled for 1.8.99.905, module version = 1.3.3
[    33.372]     Module class: X.Org Video Driver
[    33.373]     ABI class: X.Org Video Driver, version 8.0
[    33.373] (II) LoadModule: "fbdev"
[    33.373] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    33.373] (II) Module fbdev: vendor="X.Org Foundation"
[    33.373]     compiled for 1.8.99.905, module version = 0.4.2
[    33.373]     ABI class: X.Org Video Driver, version 8.0
[    33.373] (II) LoadModule: "vesa"
[    33.373] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    33.373] (II) Module vesa: vendor="X.Org Foundation"
[    33.373]     compiled for 1.8.99.905, module version = 2.3.0
[    33.373]     Module class: X.Org Video Driver
[    33.373]     ABI class: X.Org Video Driver, version 8.0
[    33.373] (WW) Falling back to old probe method for z4l
[    33.373] (II) z4l driver for Video4Linux
[    33.373] (WW) Falling back to old probe method for siliconmotion
[    33.373] (WW) Falling back to old probe method for i740
[    33.373] (WW) Falling back to old probe method for sis
[    33.374] (WW) Falling back to old probe method for neomagic
[    33.374] (WW) Falling back to old probe method for voodoo
[    33.374] (WW) Falling back to old probe method for tseng
[    33.374] (WW) Falling back to old probe method for ark
[    33.374] (WW) Falling back to old probe method for apm
[    33.374] (WW) Falling back to old probe method for s3
[    33.374] (WW) Falling back to old probe method for trident
[    33.374] (WW) Falling back to old probe method for sisusb
[    33.374] (WW) Falling back to old probe method for s3virge
[    33.374] (WW) Falling back to old probe method for cirrus
[    33.374] (II) Loading sub module "cirrus_laguna"
[    33.374] (II) LoadModule: "cirrus_laguna"
[    33.374] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[    33.375] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[    33.375]     compiled for 1.8.99.905, module version = 1.0.0
[    33.375]     ABI class: X.Org Video Driver, version 8.0
[    33.375] (II) Loading sub module "cirrus_alpine"
[    33.375] (II) LoadModule: "cirrus_alpine"
[    33.375] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[    33.376] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[    33.376]     compiled for 1.8.99.905, module version = 1.0.0
[    33.376]     ABI class: X.Org Video Driver, version 8.0
[    33.376] (WW) Falling back to old probe method for i128
[    33.376] (II) FBDEV: driver for framebuffer: fbdev
[    33.376] (II) VESA: driver for VESA chipsets: vesa
[    33.430] (++) Using config file: "/root/xorg.conf.new"
[    33.431] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.431] (==) ServerLayout "X.org Configured"
[    33.431] (**) |-->Screen "Screen0" (0)
[    33.431] (**) |   |-->Monitor "Monitor0"
[    33.432] (**) |   |-->Device "Card0"
[    33.432] (**) |-->Input Device "Mouse0"
[    33.432] (**) |-->Input Device "Keyboard0"
[    33.432] (==) Automatically adding devices
[    33.432] (==) Automatically enabling devices
[    33.432] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.432]     Entry deleted from font path.
[    33.432] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.432]     Entry deleted from font path.
[    33.432] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    33.432] (**) ModulePath set to "/usr/lib/xorg/modules"
[    33.432] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    33.432] (WW) Disabling Mouse0
[    33.432] (WW) Disabling Keyboard0
[    33.432] (II) Loading sub module "fbdevhw"
[    33.432] (II) LoadModule: "fbdevhw"
[    33.433] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    33.433] (II) Module fbdevhw: vendor="X.Org Foundation"
[    33.433]     compiled for 1.9.0, module version = 0.0.2
[    33.433]     ABI class: X.Org Video Driver, version 8.0
[    33.433] (EE) open /dev/fb0: No such file or directory
[    33.433] (WW) Falling back to old probe method for fbdev
[    33.433] 
Backtrace:
[    33.434] 0: X (xorg_backtrace+0x3b) [0x80ef31b]
[    33.434] 1: X (0x8048000+0x5d00d) [0x80a500d]
[    33.434] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x7fa40c]
[    33.434] 3: X (InitOutput+0xe95) [0x80ae4a5]
[    33.434] 4: X (0x8048000+0x1a41b) [0x806241b]
[    33.434] 5: /lib/libc.so.6 (__libc_start_main+0xe7) [0x3d3ce7]
[    33.435] 6: X (0x8048000+0x1a1b1) [0x80621b1]
[    33.435] Segmentation fault at address (nil)
[    33.435] 
Caught signal 11 (Segmentation fault). Server aborting
[    33.435] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    33.435] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    33.435] 
```

After that I was pretty sure the xorg.conf it generated wouldn't be good for anything. It wasn't. (I had no graphics at all when I tried to use it.) Here is the xorg.conf it generated
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "fbdev"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Any suggestions, anyone?

---

### Post by hreichgott on 2011-03-08
Also, here's an example of an xorg.conf I tried to make based on information I could find by googling. This one breaks X completely as well--just boots to a prompt when I use this one. If someone could just explain how xorg.conf works and how I need to set the options for 1366x768 resolution on an ATI Radeon 9802 that would be very helpful.
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    ModeLine     "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Device 9802"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Modes "1368x768"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by hreichgott on 2011-03-08
BTW same results after typo is fixed (1368 instead of 1366)

---

### Post by hreichgott on 2011-03-08
Well, finally got it to work using AMD's proprietary Catalyst driver.
Figured out that my chip is actually called Radeon 6310 (even though lspci says 9802)
For anyone else having the same problem, go to 
[BinaryDriverHowto/ATI - Community Ubuntu Documentation]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20the%20fglrx%20Driver%20from%20AMD/ATI%20Catalyst%2011.2%20For%20Ubuntu%2010.10%20Maverick") 
and follow the instructions, being sure to use the correct 4-digit chip number (6310 in my case)

I like open-source better than proprietary, so I'm going to leave this thread unsolved in the hopes that someone may come along and inform me how to configure xorg.conf to work with the open-source driver.

---

### Post by Yellow Pasque on 2011-03-08
Since it's a new video card, you'll need newer components (2.6.38 kernel, open-source video driver) for it to be recognized and work correctly. If you don't want to install a new kernel and such, your best bet is to use the binary driver until you're ready to move to Natty.

---

### Post by khelben1979 on 2011-03-10
> **Temüjin said:**
> Since it's a new video card, you'll need newer components (2.6.38 kernel, open-source video driver) for it to be recognized and work correctly. If you don't want to install a new kernel and such, your best bet is to use the binary driver until you're ready to move to Natty.

A.F.A.I.K there are several possibilites with using an open source video driver and upgrading to a newer version of Ubuntu which ships a newer Linux kernel isn't really necessary for working graphics, but it is like you wrote that kernel 2.6.38 is required when it comes to the RADEON driver and would give the best performance as well! (excluding the non-free driver)

There are more than one open source video driver available to the same chipset of graphics, with varying performance.

---

