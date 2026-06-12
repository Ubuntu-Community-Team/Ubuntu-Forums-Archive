---
title: "How to load appropriate driver for Radeon graphics card."
date: 2016-10-16
forum: Hardware
---

### Post by GwibberFooey on 2016-10-16
I am having screen resolution problems in Ubuntu Mate 16.04 AMD64. My computer is a Samsung laptop with quadcore AMD A6 processors.

All output onscreen is distorted in such a way that is stretched laterally, or equivalently, compressed vertically. The monitor hardware is widescreen therefore it should have 16:9 resolution (ie. 1366:768).

I suspect the reason for this is because my computer boots into nomodeset. My ```
/etc/default/grub
``` file contains a line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```. The reason I added this line to this file is because it solves the problem of the system booting up into a blank screen.

The commands ```
lsmod | grep radeon
``` and ```
lsmod | grep amdgpu
``` currently both return nothing. 

How can I force this system to load the appropriate graphics drivers? 

PS Some additional background information is contained in [https://ubuntuforums.org/showthread.php?t=2297945](https://ubuntuforums.org/showthread.php?t=2297945) and in [https://ubuntuforums.org/showthread.php?t=2339770&page=2](https://ubuntuforums.org/showthread.php?t=2339770&page=2)

---

### Post by kurt18947 on 2016-10-16
You may need to determine which graphics chip you have. This command should help:
> lspci

In my case

01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4200]

which uses the Radeon driver. 

lsmod shows these relevant bits:

> 
radeon               1515520  3
i2c_algo_bit           16384  1 radeon
ttm                    94208  1 radeon


  Once you determine which graphics chip set you have you could look here to see if there's any helpful information:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).

It appears that AMDGPU is only required for recent high end AMD graphics chips. I have two desktop machines with AMD chip sets and both use the Radeon driver without any input on my part. If I had this problem I'd probably save/close all apps because the machine may lock up tight then try this:

> 
sudo modprobe radeon


I haven't tried this so don't know what will happen. It shouldn't cause any damage that a restart won't fix though I don't think. Perhaps the problem that required nomodeset has been fixed. If temporarily loading the radeon driver works you could try removing nomodeset from grub.

---

### Post by GwibberFooey on 2016-10-16
The ```
lspci
``` command returns some output including the line: ```
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G]
```
Am I correct to assaume this device also uses the Radeon driver?
 
The ```
lsmod
``` command returns a table of modules and their sizes. Nowhere in that table does the expression "radeon" appear. How can the graphics chip set be determined from this or any other command?
 
When I run the ```
sudo modprobe radeon
``` command then there is the following error message: ```
modprobe: ERROR: could not insert 'radeon': Invalid argument
```

---

### Post by Yellow Pasque on 2016-10-16
The radeon kernel module is the correct one. amdgpu does not support the 6520G.
You need to try and figure out why it won't boot with nomodeset. At blank screen, can you get to a terminal (Ctrl+Alt+F1) and look at dmesg or /var/log/Xorg.0.log file?
Just saying it boots to a blank screen is about as helpful as saying, "Help. My car doesn't run."

---

### Post by GwibberFooey on 2016-10-16
I have removed the term "nomodeset" from the ```
/etc/default/grub
``` file, ie. I am no longer booting into nomodeset. And happily, the problem of booting into a blank screen seems to have gone away. But the problem of the distorted display remains. Using MATE Terminal, I am able to both run the ```
dmesg
``` command and view the ```
/var/log/Xorg.0.log
``` file. However, each contains a very large amount of information that I do not necessarily know how to interpret. There is one line of output from ```
dmesg
``` that seems significant: ```
[  315.079744] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
```. What does this mean?

---

### Post by Yellow Pasque on 2016-10-16
Copy/paste the /var/log/Xorg.0.log file (use code tags).

As for the no UMS support, that is expected, though I don't know if the message is significant. Maybe the log will shed more light.

---

### Post by alexeyn on 2016-10-17
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1568211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1568211)
Upgrade/downgrade kernel.

---

### Post by GwibberFooey on 2016-10-17
> **Temüjin said:**
> Copy/paste the /var/log/Xorg.0.log file (use code tags).

My ```
/var/log/Xorg.0.log
``` file looks like this:
```
[    48.075] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    48.075] X Protocol Version 11, Revision 0
[    48.075] Build Operating System: Linux 3.13.0-95-generic x86_64 Ubuntu
[    48.075] Current Operating System: Linux earthlingMgu 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64
[    48.075] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-43-generic root=UUID=c4ee79e0-c100-4482-bac7-232100c5e736 ro quiet splash nomodeset vt.handoff=7
[    48.075] Build Date: 14 September 2016  03:33:24PM
[    48.075] xorg-server 2:1.18.4-0ubuntu0.1 (For technical support please see http://www.ubuntu.com/support) 
[    48.075] Current version of pixman: 0.33.6
[    48.075]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    48.075] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    48.076] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 17 22:48:03 2016
[    49.554] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    49.555] (==) No Layout section.  Using the first Screen section.
[    49.555] (==) No screen section available. Using defaults.
[    49.555] (**) |-->Screen "Default Screen Section" (0)
[    49.555] (**) |   |-->Monitor "<default monitor>"
[    50.798] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    50.798] (==) Automatically adding devices
[    50.798] (==) Automatically enabling devices
[    50.798] (==) Automatically adding GPU devices
[    50.798] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    50.798] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    50.798]     Entry deleted from font path.
[    50.798] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    50.798]     Entry deleted from font path.
[    50.798] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    50.798]     Entry deleted from font path.
[    50.798] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    50.798]     Entry deleted from font path.
[    50.798] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    50.798]     Entry deleted from font path.
[    50.798] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    50.798] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    50.798] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    50.861] (II) Loader magic: 0x559845c8cdc0
[    50.861] (II) Module ABI versions:
[    50.861]     X.Org ANSI C Emulation: 0.4
[    50.861]     X.Org Video Driver: 20.0
[    50.861]     X.Org XInput driver : 22.1
[    50.861]     X.Org Server Extension : 9.0
[    50.863] (++) using VT number 7

[    50.863] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    50.865] (--) PCI:*(0:0:1:0) 1002:9647:144d:c609 rev 0, Mem @ 0xa0000000/268435456, 0xfeb00000/262144, I/O @ 0x0000f000/256
[    50.865] (--) PCI: (0:2:0:0) 1002:6760:144d:c609 rev 0, Mem @ 0xb0000000/268435456, 0xfea20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[    50.865] (II) LoadModule: "glx"
[    50.970] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    52.269] (II) Module glx: vendor="X.Org Foundation"
[    52.269]     compiled for 1.18.4, module version = 1.0.0
[    52.269]     ABI class: X.Org Server Extension, version 9.0
[    52.269] (==) AIGLX enabled
[    52.269] (==) Matched ati as autoconfigured driver 0
[    52.269] (==) Matched modesetting as autoconfigured driver 1
[    52.269] (==) Matched fbdev as autoconfigured driver 2
[    52.269] (==) Matched vesa as autoconfigured driver 3
[    52.269] (==) Assigned the driver to the xf86ConfigLayout
[    52.269] (II) LoadModule: "ati"
[    52.269] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    52.270] (II) Module ati: vendor="X.Org Foundation"
[    52.270]     compiled for 1.18.3, module version = 7.7.0
[    52.270]     Module class: X.Org Video Driver
[    52.270]     ABI class: X.Org Video Driver, version 20.0
[    52.270] (II) LoadModule: "radeon"
[    52.270] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    52.451] (II) Module radeon: vendor="X.Org Foundation"
[    52.451]     compiled for 1.18.3, module version = 7.7.0
[    52.451]     Module class: X.Org Video Driver
[    52.451]     ABI class: X.Org Video Driver, version 20.0
[    52.451] (II) LoadModule: "modesetting"
[    52.451] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    52.451] (II) Module modesetting: vendor="X.Org Foundation"
[    52.451]     compiled for 1.18.4, module version = 1.18.4
[    52.451]     Module class: X.Org Video Driver
[    52.451]     ABI class: X.Org Video Driver, version 20.0
[    52.451] (II) LoadModule: "fbdev"
[    52.451] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    52.451] (II) Module fbdev: vendor="X.Org Foundation"
[    52.451]     compiled for 1.18.1, module version = 0.4.4
[    52.451]     Module class: X.Org Video Driver
[    52.451]     ABI class: X.Org Video Driver, version 20.0
[    52.451] (II) LoadModule: "vesa"
[    52.451] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    52.451] (II) Module vesa: vendor="X.Org Foundation"
[    52.451]     compiled for 1.18.1, module version = 2.3.4
[    52.451]     Module class: X.Org Video Driver
[    52.451]     ABI class: X.Org Video Driver, version 20.0
[    52.451] (II) RADEON: Driver for ATI Radeon chipsets:
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
    OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[    52.456] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    52.456] (II) FBDEV: driver for framebuffer: fbdev
[    52.456] (II) VESA: driver for VESA chipsets: vesa
[    52.537] (II) [KMS] drm report modesetting isn't supported.
[    52.537] (EE) open /dev/dri/card0: No such file or directory
[    52.537] (WW) Falling back to old probe method for modesetting
[    52.537] (EE) open /dev/dri/card0: No such file or directory
[    52.537] (II) Loading sub module "fbdevhw"
[    52.537] (II) LoadModule: "fbdevhw"
[    52.537] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    52.537] (II) Module fbdevhw: vendor="X.Org Foundation"
[    52.537]     compiled for 1.18.4, module version = 0.0.2
[    52.537]     ABI class: X.Org Video Driver, version 20.0
[    52.538] (**) FBDEV(2): claimed PCI slot 0@0:1:0
[    52.538] (II) FBDEV(2): using default device
[    52.538] (WW) Falling back to old probe method for vesa
[    52.538] (EE) Screen 0 deleted because of no matching config section.
[    52.538] (II) UnloadModule: "radeon"
[    52.538] (EE) Screen 0 deleted because of no matching config section.
[    52.538] (II) UnloadModule: "modesetting"
[    52.538] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    52.538] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    52.538] (==) FBDEV(0): RGB weight 888
[    52.538] (==) FBDEV(0): Default visual is TrueColor
[    52.538] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    52.538] (II) FBDEV(0): hardware: VESA VGA (video memory: 3072kB)
[    52.538] (II) FBDEV(0): checking modes against framebuffer device...
[    52.538] (II) FBDEV(0): checking modes against monitor...
[    52.538] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    52.538] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[    52.538] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[    52.538] (==) FBDEV(0): DPI set to (96, 96)
[    52.538] (II) Loading sub module "fb"
[    52.538] (II) LoadModule: "fb"
[    52.538] (II) Loading /usr/lib/xorg/modules/libfb.so
[    52.578] (II) Module fb: vendor="X.Org Foundation"
[    52.578]     compiled for 1.18.4, module version = 1.0.0
[    52.578]     ABI class: X.Org ANSI C Emulation, version 0.4
[    52.578] (**) FBDEV(0): using shadow framebuffer
[    52.578] (II) Loading sub module "shadow"
[    52.578] (II) LoadModule: "shadow"
[    52.579] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    52.579] (II) Module shadow: vendor="X.Org Foundation"
[    52.579]     compiled for 1.18.4, module version = 1.1.0
[    52.579]     ABI class: X.Org ANSI C Emulation, version 0.4
[    52.579] (II) UnloadModule: "vesa"
[    52.579] (II) Unloading vesa
[    52.579] (==) Depth 24 pixmap format is 32 bpp
[    52.579] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    52.817] (==) FBDEV(0): Backing store enabled
[    52.840] (==) FBDEV(0): DPMS enabled
[    52.864] (==) RandR enabled
[    52.864] (II) Found 2 VGA devices: arbiter wrapping enabled
[    52.873] (II) SELinux: Disabled on system
[    52.874] (II) AIGLX: Screen 0 is not DRI2 capable
[    52.874] (EE) AIGLX: reverting to software rendering
[    59.547] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    59.547] (II) AIGLX: Loaded and initialized swrast
[    59.547] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    59.861] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    59.861] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    59.861] (II) LoadModule: "evdev"
[    59.861] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    59.967] (II) Module evdev: vendor="X.Org Foundation"
[    59.967]     compiled for 1.18.1, module version = 2.10.1
[    59.967]     Module class: X.Org XInput Driver
[    59.967]     ABI class: X.Org XInput driver, version 22.1
[    59.967] (II) Using input driver 'evdev' for 'Power Button'
[    59.967] (**) Power Button: always reports core events
[    59.967] (**) evdev: Power Button: Device: "/dev/input/event2"
[    59.967] (--) evdev: Power Button: Vendor 0 Product 0x1
[    59.967] (--) evdev: Power Button: Found keys
[    59.967] (II) evdev: Power Button: Configuring as keyboard
[    59.967] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    59.967] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    59.967] (**) Option "xkb_rules" "evdev"
[    59.967] (**) Option "xkb_model" "pc105"
[    59.967] (**) Option "xkb_layout" "us"
[    59.968] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    59.968] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    59.968] (II) Using input driver 'evdev' for 'Video Bus'
[    59.968] (**) Video Bus: always reports core events
[    59.968] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    59.968] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    59.968] (--) evdev: Video Bus: Found keys
[    59.968] (II) evdev: Video Bus: Configuring as keyboard
[    59.968] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5/event4"
[    59.968] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    59.968] (**) Option "xkb_rules" "evdev"
[    59.968] (**) Option "xkb_model" "pc105"
[    59.968] (**) Option "xkb_layout" "us"
[    59.969] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    59.969] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    59.969] (II) Using input driver 'evdev' for 'Video Bus'
[    59.969] (**) Video Bus: always reports core events
[    59.969] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    59.969] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    59.969] (--) evdev: Video Bus: Found keys
[    59.969] (II) evdev: Video Bus: Configuring as keyboard
[    59.969] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:0e/LNXVIDEO:01/input/input6/event5"
[    59.969] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    59.969] (**) Option "xkb_rules" "evdev"
[    59.969] (**) Option "xkb_model" "pc105"
[    59.969] (**) Option "xkb_layout" "us"
[    59.969] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    59.969] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    59.969] (II) Using input driver 'evdev' for 'Power Button'
[    59.969] (**) Power Button: always reports core events
[    59.969] (**) evdev: Power Button: Device: "/dev/input/event1"
[    59.969] (--) evdev: Power Button: Vendor 0 Product 0x1
[    59.969] (--) evdev: Power Button: Found keys
[    59.969] (II) evdev: Power Button: Configuring as keyboard
[    59.969] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    59.969] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    59.969] (**) Option "xkb_rules" "evdev"
[    59.969] (**) Option "xkb_model" "pc105"
[    59.969] (**) Option "xkb_layout" "us"
[    59.970] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    59.970] (II) No input driver specified, ignoring this device.
[    59.970] (II) This device may have been added with another device file.
[    59.970] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event7)
[    59.970] (II) No input driver specified, ignoring this device.
[    59.970] (II) This device may have been added with another device file.
[    59.971] (II) config/udev: Adding input device WebCam SCB-1100N (/dev/input/event10)
[    59.971] (**) WebCam SCB-1100N: Applying InputClass "evdev keyboard catchall"
[    59.971] (II) Using input driver 'evdev' for 'WebCam SCB-1100N'
[    59.971] (**) WebCam SCB-1100N: always reports core events
[    59.971] (**) evdev: WebCam SCB-1100N: Device: "/dev/input/event10"
[    59.971] (--) evdev: WebCam SCB-1100N: Vendor 0x2232 Product 0x1008
[    59.971] (--) evdev: WebCam SCB-1100N: Found keys
[    59.971] (II) evdev: WebCam SCB-1100N: Configuring as keyboard
[    59.971] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input11/event10"
[    59.971] (II) XINPUT: Adding extended input device "WebCam SCB-1100N" (type: KEYBOARD, id 10)
[    59.971] (**) Option "xkb_rules" "evdev"
[    59.971] (**) Option "xkb_model" "pc105"
[    59.971] (**) Option "xkb_layout" "us"
[    59.971] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event9)
[    59.971] (II) No input driver specified, ignoring this device.
[    59.971] (II) This device may have been added with another device file.
[    59.972] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event8)
[    59.972] (II) No input driver specified, ignoring this device.
[    59.972] (II) This device may have been added with another device file.
[    59.972] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    59.972] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    59.972] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    59.972] (**) AT Translated Set 2 keyboard: always reports core events
[    59.972] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    59.972] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    59.972] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    59.972] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    59.972] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    59.972] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    59.972] (**) Option "xkb_rules" "evdev"
[    59.972] (**) Option "xkb_model" "pc105"
[    59.972] (**) Option "xkb_layout" "us"
[    59.973] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    59.973] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    59.973] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchscreen catchall"
[    59.973] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    59.973] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    59.973] (II) LoadModule: "synaptics"
[    59.973] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    59.973] (II) Module synaptics: vendor="X.Org Foundation"
[    59.973]     compiled for 1.18.1, module version = 1.8.2
[    59.973]     Module class: X.Org XInput Driver
[    59.973]     ABI class: X.Org XInput driver, version 22.1
[    59.973] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    59.973] (**) ETPS/2 Elantech Touchpad: always reports core events
[    59.973] (**) Option "Device" "/dev/input/event6"
[    60.040] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2480 (res 28)
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1116 (res 24)
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    60.040] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    60.040] (**) ETPS/2 Elantech Touchpad: always reports core events
[    60.080] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event6"
[    60.080] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    60.080] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    60.080] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    60.080] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.074
[    60.080] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    60.080] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    60.080] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    60.080] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    60.080] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    60.081] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    60.081] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
```

---

### Post by Kris_M on 2016-10-17
What does Ubuntu System Settings (gear with wrench) / Displays / resolution say, and can you change it?

---

### Post by GwibberFooey on 2016-10-18
[ATTACH=CONFIG]271676[/ATTACH]

Here is a screenshot of my Displays window. I can change nothing within this window.

---

### Post by Kris_M on 2016-10-18
yeah :(  The prob of Ubuntu (edit: or ANY Linux) on a laptop is drivers.  You will have to somehow find unix drivers for that chipset.  Sorry.

---

### Post by mastablasta on 2016-10-19
> **alexeyn said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1568211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1568211)
Upgrade/downgrade kernel.

this!

try booting  with newer kernel!:



[    48.075] Build Operating System: Linux 3.13.0-95-generic x86_64 Ubuntu

---

### Post by Yellow Pasque on 2016-10-19
^No, the "Build OS" kernel is what Ubuntu's build server was running when it built the X package.
OP is using standard kernel that comes with 16.04:
```
Current Operating System: Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:48:03 UTC 2016 x86_64
```

The Xorg log also shows that 'nomodeset' was still being used, despite OP thinking/saying system booted without it, hence the distorted (non-native) resolution.

> try booting with newer kernel
That's a thought. Heck, I'd be more interested in trying Ubuntu 16.10 on a LiveUSB (if time/bandwidth allows) to see if problem persists there. If so, it strongly suggests upstream bug rather than a configuration problem with the current install.

---

### Post by Yellow Pasque on 2016-10-19
I'd also like to note that this is actually a hybrid graphics system (just saw it in old thread). That's kind of an important fact that got left out in this thread...
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647] (prog-if 00 [VGA controller])
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])
```

---

### Post by GwibberFooey on 2016-10-19
Thanks everyone for the the feedback on this seemingly intractable problem. I will try booting Ubuntu 16.10 AMD64 from a USB drive (as soon as I have time) to see if this problem persists. During the trial session of Ubuntu 16.10, are there any configuration settings etc. that I should look at? For instance, I will look at the Monitor Preferences to see if I will have gained any additional control there. All suggestions are appreciated.

---

### Post by kurt18947 on 2016-10-19
> **Temüjin said:**
> I'd also like to note that this is actually a hybrid graphics system (just saw it in old thread). That's kind of an important fact that got left out in this thread...
```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647] (prog-if 00 [VGA controller])
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])
```

I'm not at all knowledgeable about video systems but this does indeed seem to be a relevant point.

---

### Post by mastablasta on 2016-10-20
ouch then. if you can, then it might be easier to install 14.04 LTS (the first one not the one with newer kernel versions such as 14.04.2 etc.).

fglrx should resolve it: [SIZE=2]https://wiki.ubuntu.com/X/Config/HybridGraphics
[/SIZE]

if you stay on 16.04 you might need prime. not much can be found on ubuntu wiki but Arch Linux wiki has this to say on it: 

[SIZE=2]https://wiki.archlinux.org/index.php/PRIME

and Debian:


[SIZE=2]https://wiki.debian.org/AtiHowTo

however i can't find anything on AMD/AMD combo. you might need a custom xorg.conf and the switch between them. or you could try to use intel switch command, maybe it works in amd case as well.

anothe roption would be to turn off one of the GPU's.

finally i bet it all works well if you use Windows.




[/SIZE]

[/SIZE]

---

### Post by GwibberFooey on 2016-10-21
I am not so eager to reinstall 14.04. It was only recently that I abandoned Ubuntu 14.04 AMD64 LTS and adopted Ubuntu MATE 16.04 AMD64 LTS. I am no expert but it seems unlikely that moving from Ubuntu MATE to the standard Ubuntu would solve my screen resolution problems. Can anybody confirm this suspicion of mine? 

Perhaps it is actually very simple, but something like a custom xorg.conf seems complicated to me. Unless somebody is willing\able to guide me step by step then I am reluctant to go there. 

Another suggestion I saw was to turn off one of the GPUs. If that enables my system to display onscreen at the correct resolution then I am willing to give it a try. How would I accomplish this task?

---

### Post by deadflowr on 2016-10-21
> Perhaps it is actually very simple
Could be.
Simple solution, from memory, is to disable one of the cards in the BIOS.

But my memory is most likely warped, though...

---

### Post by ping-wu on 2016-10-21
> **GwibberFooey said:**
> Thanks everyone for the the feedback on this seemingly intractable problem. I will try booting Ubuntu 16.10 AMD64 from a USB drive (as soon as I have time) to see if this problem persists. During the trial session of Ubuntu 16.10, are there any configuration settings etc. that I should look at? For instance, I will look at the Monitor Preferences to see if I will have gained any additional control there. All suggestions are appreciated.

I am running Ubuntu Mate 16.10 on an AMD Carrizo (A10-8600) laptop.  This is a customized LiveUSB (only with added apps, no change to stock kernel or module); everything seems to be working great, very smooth video, etc.  Previously I had a lot of problems running 16.04LTS on this machine.  The AMDGPU-PRO driver was not stable, but without it the system runs a bit haggard.  The 4.8 kernel seems to be a godsend for AMD.  Knock on Wood!

---

### Post by GwibberFooey on 2016-10-21
In BIOS on the "Advanced" page there is a setting called "UEFI Boot Support". Until approximately 1 hour ago UEFI boot support had been disabled. I changed this setting to enable UEFI boot support and then I exited BIOS and let Ubuntu boot-up. I was pleasantly surprised to find that the display resolution problems had been corrected. Here is a screenshot of the Preferences > Hardware > Displays window in the Ubuntu MATE System menu during that session; notice that the resolution is correct for a widescreen display. 
[ATTACH=CONFIG]271713[/ATTACH]

I then shutdown the computer using the graphical shutdown/restart/suspend button located at top right of the screen. I restarted the computer and happily found the correct display resolution (ie. the subject of the original post in this thread). Using the same shutdown/restart/suspend button at top right of screen, the next time I selected the restart option. At first the restart operation proceeds as normal, but then during the boot-up of the next session there is eventually only a blank, black screen. The only way I know how to escape this black screen is by holding down the power button. 

I tried returning the "UEFI Boot Support" setting in BIOS back to "disabled". This has not corrected the problem of the blank screen during boot-up. The only way I can now successfully boot up into Ubuntu is by entering the GRUB menu and manually forcing "nomodeset". Note that inserting the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
``` into the ```
/etc/default/grub
``` file does not enable the system to get beyond the blank screen problem described in this post.

Remark: when I boot-up into an Ubuntu session after manually inserting the "nomodeset" command into the GRUB commandline then the only available display resolution is 1024x768, which is not correct for this hardware.

---

### Post by QIII on 2016-10-21
After editing /etc/default/grub, did you do

```
sudo update-grub
```

---

### Post by GwibberFooey on 2016-10-21
I booted up into Ubuntu MATE 16.10 AMD64 from a USB drive. During the 16.10 live session the screen display resolution was correct for my hardware. I did not have to configure anything manually to achieve this. 

I shutdown the machine, removed the usb drive containing 16.10, powered up the computer and let it boot-up. Note I did not manually force it to do "nomodeset" at GRUB. The system booted up perfectly: no blank screen problem; no display resolution problem. 

Next I shutdown the machine again. Then I restarted the machine, and again I did not manually enforce nomodeset via GRUB. This time the machine again had the blank screen problem. 

Subsequently, I ran the ```
sudo update-grub
``` command, as per QIII's instruction. That enables me to boot-up without manually doing "nomodeset" at GRUB. However, there is still the issue of the incorrect display resolution.

---

### Post by Yellow Pasque on 2016-10-21
The only other suggestion I have is the radeon.runpm kernel boot option.

---

### Post by GwibberFooey on 2016-10-23
I perfomed a boot-from-usb of Ubuntu MATE 16.10 AMD64 and during that session the display had the correct aspect-ratio. Therefore I chose to nuke the installed Ubuntu MATE 16.04 AMD64 LTS and to commit to a brand new installation of 16.10. But when I boot-up from harddisk with the new 16.10 operating system then there are the exact same display resolution problems as I experienced in 16.04 LTS. It is remarkable that Ubuntu is consistently able to display correctly during a live-boot from usb-drive, but is also consistently unable to display correctly when booting from the hard-disk. 

I have upgraded my operating system back down to Ubuntu MATE 14.04 AMD64. With this operating system, after having installed the fglrx driver, there is no problem of incorrect screen resolution.

Sadly, my HP printer is not accessible after I installed the 14.04 operating system.:mad:

---

### Post by mastablasta on 2016-10-24
why is HP printer not accessibl ein 14.04? install the drivers for it.

the live vs installed issue seems similar to my sound problems. when doing the live boot it scans and loads the correct driver, while in installed mode it probably has some drivers installed and preconfigured to run them. but they are the wrong ones. this is basically what is happening inmy case with sound chip. it would just load the wrong driver for the chip for osme reason. and the only solution in that case is to reload the modules.

anyway make sure also that the display is not sent to any other port. the nvidia i have on windows - when I load new driver (driver update) it is always sending the picture to the other port eventhough there is nothing plugged in on that port. ](*,)

---

