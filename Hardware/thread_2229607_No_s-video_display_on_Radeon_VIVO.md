---
title: "No s-video display on Radeon VIVO"
date: 2014-06-14
forum: Hardware
---

### Post by ed_c2 on 2014-06-14
I just setup Lubuntu 14.04 on an older PC with a Radeon ViVO video card [R100 chip] and can't figure out how to get the s-video output to work. It works fine in Windows XP and even get video as far as the grub boot menu, but as soon as I start Lubuntu I get nothing on the TV. Tried following guides on creating a xorg.conf file in /usr/share/X11/xorg.conf.d but I still can't get it to even recognize the s-video output exist.

```
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 250mm x 184mm
   1280x1024      60.0  
   1024x768       85.0*    75.1     60.0  
   800x600        85.1     75.0  
   640x480        85.0     75.0     60.0  
   720x400        70.1  
   720x350        70.1  

```

I ran the updater and it said there was an ATI driver among the updates, so I'm assuming that the driver is installed correctly. Is there some other setting or driver I need to use to get this to work?

---

### Post by sudodus on 2014-06-14
Welcome to the Ubuntu Forums :-)

I tried s-video recently with Lubuntu 14.04 LTS in my IBM Thinkpad T42, and it worked out of the box. But I don't know what to tweak to make it work for you.

I would try a light-weight community re-spin based on Ubuntu 12.04 LTS because the older kernel and its drivers have a better chance to work with old hardware. ***Bento, Bodhi ***and*** LXLE*** promise long time support until April 2017.

Maybe you should also try some ***proprietary driver for the graphics card***.

---

### Post by ed_c2 on 2014-06-14
I couldn't find a linux driver that old from AMD. Even if there was one, it probably wouldn't work anyway.

---

### Post by sudodus on 2014-06-14
There is still the alternative to try a light-weight community re-spin based on Ubuntu 12.04 LTS

---

### Post by mörgæs on 2014-06-14
> **ed_c2 said:**
> I couldn't find a linux driver that old from AMD. Even if there was one, it probably wouldn't work anyway.

Correct, there are no drivers provided by AMD for this card.

---

### Post by ed_c2 on 2014-06-17
According to this, the current radeon drivers are supposed to support TV Out on the R100. 

[http://wiki.x.org/wiki/RadeonFeature/](http://wiki.x.org/wiki/RadeonFeature/)

Might there have been something I missed?

---

### Post by sudodus on 2014-06-17
I would try a light-weight community re-spin based on Ubuntu 12.04 LTS  because the older kernel and its drivers have a better chance to work  with old hardware. ***Bento, Bodhi ***and*** LXLE*** promise long time support until April 2017.

You can try them live without installing and check if s-video is working.

---

### Post by ed_c2 on 2014-06-23
Tried Bento 12, VGA-0 is still the only output. Is there anyone who actually knows how to troubleshoot video driver issues?

---

### Post by Yellow Pasque on 2014-06-23
Post the /var/log/Xorg.0.log file. Use code tags.

---

### Post by ed_c2 on 2014-06-24
I'll post it as soon as I can get access to that machine again.

---

### Post by ed_c2 on 2014-07-27
Sorry for the delay. It's about an hour and half drive up here, so I don't get around very often. I should be able to get remote access to the machine under Bento now, so that's going to be a bit less of an issue. 

```
 [    17.729] X.Org X Server 1.11.3Release Date: 2011-12-16[    17.729] X Protocol Version 11, Revision 0[    17.729] Build Operating System: Linux
2.6.42-37-generic i686 Ubuntu[    17.729] Current Operating System: Linux
jerryPC 3.2.0-63-generic #95-Ubuntu SMP Thu May 15 23:06:36 UTC 2014
i686[    17.729] Kernel command line:
BOOT_IMAGE=/boot/vmlinuz-3.2.0-63-generic
root=UUID=bcc171e7-0a1d-44ca-8130-85dde66d5ad2 ro quiet splash
vt.handoff=7[    17.729] Build Date: 16 October 2013 
04:45:22PM[    17.729] xorg-server 2:1.11.4-0ubuntu10.14
(For technical support please see http://www.ubuntu.com/support) 
[    17.729] Current version of pixman: 0.30.2[    17.729]     Before reporting problems, check
http://wiki.x.org    to make sure that you have the latest version.[    17.729] Markers: (--) probed, (**) from
config file, (==) default setting,    (++) from command line, (!!) notice, (II)
informational,    (WW) warning, (EE) error, (NI) not implemented,
(??) unknown.[    17.729] (==) Log file:
"/var/log/Xorg.0.log", Time: Sun Jul 27 05:47:59 2014[    17.751] (==) Using system config directory
"/usr/share/X11/xorg.conf.d"[    17.751] (==) No Layout section.  Using the
first Screen section.[    17.751] (==) No screen section available.
Using defaults.[    17.751] (**) |-->Screen "Default
Screen Section" (0)[    17.751] (**) |   |-->Monitor "<default
monitor>"[    17.751] (==) No monitor specified for
screen "Default Screen Section".    Using a default monitor configuration.[    17.751] (==) Automatically adding devices[    17.751] (==) Automatically enabling devices[    17.752] (WW) The directory
"/usr/share/fonts/X11/cyrillic" does not exist.[    17.752]     Entry deleted from font path.[    17.752] (WW) The directory
"/usr/share/fonts/X11/75dpi/" does not exist.[    17.752]     Entry deleted from font path.[    17.752] (WW) The directory
"/usr/share/fonts/X11/75dpi" does not exist.[    17.752]     Entry deleted from font path.[    17.752] (WW) The directory
"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not
exist.[    17.752]     Entry deleted from font path.[    17.752] (==) FontPath set to:    /usr/share/fonts/X11/misc,    /usr/share/fonts/X11/100dpi/:unscaled,    /usr/share/fonts/X11/Type1,    /usr/share/fonts/X11/100dpi,    built-ins[    17.752] (==) ModulePath set to
"/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"[    17.752] (II) The server relies on udev to
provide the list of input devices.    If no devices become available, reconfigure
udev or disable AutoAddDevices.[    17.752] (II) Loader magic: 0xbc95a0[    17.752] (II) Module ABI versions:[    17.752]     X.Org ANSI C Emulation: 0.4[    17.752]     X.Org Video Driver: 11.0[    17.752]     X.Org XInput driver : 16.0[    17.752]     X.Org Server Extension : 6.0[    17.753] (--) PCI:*(0:1:0:0)
1002:5144:1002:001a rev 0, Mem @ 0xf0000000/134217728,
0xfbf00000/524288, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072[    17.753] (II) Open ACPI successful
(/var/run/acpid.socket)[    17.753] (II) LoadModule: "extmod"[    17.764] (II) Loading
/usr/lib/xorg/modules/extensions/libextmod.so[    17.764] (II) Module extmod: vendor="X.Org
Foundation"[    17.764]     compiled for 1.11.3, module
version = 1.0.0[    17.764]     Module class: X.Org Server
Extension[    17.764]     ABI class: X.Org Server Extension,
version 6.0[    17.764] (II) Loading extension
MIT-SCREEN-SAVER[    17.764] (II) Loading extension
XFree86-VidModeExtension[    17.764] (II) Loading extension XFree86-DGA[    17.764] (II) Loading extension DPMS[    17.764] (II) Loading extension XVideo[    17.764] (II) Loading extension
XVideo-MotionCompensation[    17.764] (II) Loading extension X-Resource[    17.764] (II) LoadModule: "dbe"[    17.764] (II) Loading
/usr/lib/xorg/modules/extensions/libdbe.so[    17.765] (II) Module dbe: vendor="X.Org
Foundation"[    17.765]     compiled for 1.11.3, module
version = 1.0.0[    17.765]     Module class: X.Org Server
Extension[    17.765]     ABI class: X.Org Server Extension,
version 6.0[    17.765] (II) Loading extension
DOUBLE-BUFFER[    17.765] (II) LoadModule: "glx"[    17.765] (II) Loading
/usr/lib/xorg/modules/extensions/libglx.so[    17.765] (II) Module glx: vendor="X.Org
Foundation"[    17.765]     compiled for 1.11.3, module
version = 1.0.0[    17.765]     ABI class: X.Org Server Extension,
version 6.0[    17.765] (==) AIGLX enabled[    17.765] (II) Loading extension GLX[    17.765] (II) LoadModule: "record"[    17.766] (II) Loading
/usr/lib/xorg/modules/extensions/librecord.so[    17.766] (II) Module record: vendor="X.Org
Foundation"[    17.766]     compiled for 1.11.3, module
version = 1.13.0[    17.766]     Module class: X.Org Server
Extension[    17.766]     ABI class: X.Org Server Extension,
version 6.0[    17.766] (II) Loading extension RECORD[    17.766] (II) LoadModule: "dri"[    17.766] (II) Loading
/usr/lib/xorg/modules/extensions/libdri.so[    17.766] (II) Module dri: vendor="X.Org
Foundation"[    17.766]     compiled for 1.11.3, module
version = 1.0.0[    17.766]     ABI class: X.Org Server Extension,
version 6.0[    17.767] (II) Loading extension XFree86-DRI[    17.767] (II) LoadModule: "dri2"[    17.767] (II) Loading
/usr/lib/xorg/modules/extensions/libdri2.so[    17.767] (II) Module dri2: vendor="X.Org
Foundation"[    17.767]     compiled for 1.11.3, module
version = 1.2.0[    17.767]     ABI class: X.Org Server Extension,
version 6.0[    17.767] (II) Loading extension DRI2[    17.767] (==) Matched fglrx as
autoconfigured driver 0[    17.767] (==) Matched ati as autoconfigured
driver 1[    17.767] (==) Matched vesa as autoconfigured
driver 2[    17.767] (==) Matched fbdev as
autoconfigured driver 3[    17.767] (==) Assigned the driver to the
xf86ConfigLayout[    17.767] (II) LoadModule: "fglrx"[    17.797] (WW) Warning, couldn't open module
fglrx[    17.797] (II) UnloadModule: "fglrx"[    17.797] (II) Unloading fglrx[    17.797] (EE) Failed to load module "fglrx"
(module does not exist, 0)[    17.797] (II) LoadModule: "ati"[    17.797] (II) Loading
/usr/lib/xorg/modules/drivers/ati_drv.so[    17.797] (II) Module ati: vendor="X.Org
Foundation"[    17.798]     compiled for 1.11.3, module
version = 6.14.99[    17.798]     Module class: X.Org Video Driver[    17.798]     ABI class: X.Org Video Driver,
version 11.0[    17.798] (II) LoadModule: "radeon"[    17.798] (II) Loading
/usr/lib/xorg/modules/drivers/radeon_drv.so[    17.798] (II) Module radeon: vendor="X.Org
Foundation"[    17.799]     compiled for 1.11.3, module
version = 6.14.99[    17.799]     Module class: X.Org Video Driver[    17.799]     ABI class: X.Org Video Driver,
version 11.0[    17.799] (II) LoadModule: "vesa"[    17.799] (II) Loading
/usr/lib/xorg/modules/drivers/vesa_drv.so[    17.799] (II) Module vesa: vendor="X.Org
Foundation"[    17.799]     compiled for 1.11.3, module
version = 2.3.0[    17.799]     Module class: X.Org Video Driver[    17.799]     ABI class: X.Org Video Driver,
version 11.0[    17.799] (II) LoadModule: "fbdev"[    17.800] (II) Loading
/usr/lib/xorg/modules/drivers/fbdev_drv.so[    17.800] (II) Module fbdev: vendor="X.Org
Foundation"[    17.800]     compiled for 1.11.3, module
version = 0.4.2[    17.800]     ABI class: X.Org Video Driver,
version 11.0[    17.800] (==) Matched fglrx as
autoconfigured driver 0[    17.800] (==) Matched ati as autoconfigured
driver 1[    17.800] (==) Matched vesa as autoconfigured
driver 2[    17.800] (==) Matched fbdev as
autoconfigured driver 3[    17.800] (==) Assigned the driver to the
xf86ConfigLayout[    17.800] (II) LoadModule: "fglrx"[    17.801] (WW) Warning, couldn't open module
fglrx[    17.801] (II) UnloadModule: "fglrx"[    17.801] (II) Unloading fglrx[    17.801] (EE) Failed to load module "fglrx"
(module does not exist, 0)[    17.801] (II) LoadModule: "ati"[    17.802] (II) Loading
/usr/lib/xorg/modules/drivers/ati_drv.so[    17.802] (II) Module ati: vendor="X.Org
Foundation"[    17.802]     compiled for 1.11.3, module
version = 6.14.99[    17.802]     Module class: X.Org Video Driver[    17.802]     ABI class: X.Org Video Driver,
version 11.0[    17.802] (II) LoadModule: "vesa"[    17.802] (II) Loading
/usr/lib/xorg/modules/drivers/vesa_drv.so[    17.802] (II) Module vesa: vendor="X.Org
Foundation"[    17.802]     compiled for 1.11.3, module
version = 2.3.0[    17.802]     Module class: X.Org Video Driver[    17.802]     ABI class: X.Org Video Driver,
version 11.0[    17.802] (II) UnloadModule: "vesa"[    17.802] (II) Unloading vesa[    17.802] (II) Failed to load module "vesa"
(already loaded, 0)[    17.802] (II) LoadModule: "fbdev"[    17.802] (II) Loading
/usr/lib/xorg/modules/drivers/fbdev_drv.so[    17.803] (II) Module fbdev: vendor="X.Org
Foundation"[    17.803]     compiled for 1.11.3, module
version = 0.4.2[    17.803]     ABI class: X.Org Video Driver,
version 11.0[    17.803] (II) UnloadModule: "fbdev"[    17.803] (II) Unloading fbdev[    17.803] (II) Failed to load module "fbdev"
(already loaded, 0)[    17.803] (II) RADEON: Driver for ATI Radeon
chipsets:    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI
FireMV 2400 (PCI),    ATI Radeon Mobility X300 (M24) 3152 (PCIE),    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400
3155 (PCI),    ATI Radeon X600 (RV380) 3E50 (PCIE),    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI
Radeon IGP320 (A3) 4136,    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon
9500 AD (AGP),    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF
(AGP),    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH
(AGP),    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ
(AGP),    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP
(AGP),    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT
AR (AGP),    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT
(AGP), ATI Radeon 9650,    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP
(A4+) 4237,    ATI Radeon 8500 AIW BB (AGP), ATI Radeon
IGP320M (U1) 4336,    ATI Radeon IGP330M/340M/350M (U2) 4337,    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon
9000/PRO If (AGP/PCI),    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800
(R420) JH (AGP),    ATI Radeon X800PRO (R420) JI (AGP),    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon
X800 (R420) JK (AGP),    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3
(R420) JM (AGP),    ATI Radeon Mobility 9800 (M18) JN (AGP),    ATI Radeon X800 SE (R420) (AGP), ATI Radeon
X800XT (R420) JP (AGP),    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon
X850 (R480) (AGP),    ATI Radeon X850 XT (R480) (AGP), ATI Radeon
X850 SE (R480) (AGP),    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon
X850 XT PE (R480) (AGP),    ATI Radeon Mobility M7 LW (AGP),    ATI Mobility FireGL 7800 M7 LX (AGP),    ATI Radeon Mobility M6 LY (AGP), ATI Radeon
Mobility M6 LZ (AGP),    ATI FireGL Mobility 9000 (M9) Ld (AGP),    ATI Radeon Mobility 9000 (M9) Lf (AGP),    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI
FireMV 2400 PCI,    ATI Radeon 9700 Pro ND (AGP), ATI Radeon
9700/9500Pro NE (AGP),    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG
(AGP),    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI
(AGP),    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ
(AGP),    ATI Radeon Mobility 9600/9700 (M10/M11) NP
(AGP),    ATI Radeon Mobility 9600 (M10) NQ (AGP),    ATI Radeon Mobility 9600 (M11) NR (AGP),    ATI Radeon Mobility 9600 (M10) NS (AGP),    ATI FireGL Mobility T2 (M10) NT (AGP),    ATI FireGL Mobility T2e (M11) NV (AGP), ATI
Radeon QD (AGP),    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI
Radeon QG (AGP),    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500
QL (AGP),    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW
(AGP/PCI),    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon
VE/7000 QY (AGP/PCI),    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000
515E (PCI),    ATI Radeon Mobility X300 (M22) 5460 (PCIE),    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800
(R423) UH (PCIE),    ATI Radeon X800PRO (R423) UI (PCIE),    ATI Radeon X800LE (R423) UJ (PCIE),    ATI Radeon X800SE (R423) UK (PCIE),    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon
X800 XL (R430) (PCIE),    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon
X800 (R430) (PCIE),    ATI FireGL V7100 (R423) (PCIE), ATI FireGL
V5100 (R423) UQ (PCIE),    ATI FireGL unknown (R423) UR (PCIE),    ATI FireGL unknown (R423) UT (PCIE),    ATI Mobility FireGL V5000 (M26) (PCIE),    ATI Mobility FireGL V5000 (M26) (PCIE),    ATI Mobility Radeon X700 XL (M26) (PCIE),    ATI Mobility Radeon X700 (M26) (PCIE),    ATI Mobility Radeon X700 (M26) (PCIE),    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100
IGP (A5) 5834,    ATI Radeon Mobility 9100 IGP (U3) 5835,    ATI Radeon XPRESS 200 5954 (PCIE),    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon
9250 5960 (AGP),    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200
5962 (AGP),    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200
(PCI),    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200
5974 (PCIE),    ATI Radeon XPRESS 200M 5975 (PCIE),    ATI Radeon XPRESS 200 5A41 (PCIE),    ATI Radeon XPRESS 200M 5A42 (PCIE),    ATI Radeon XPRESS 200 5A61 (PCIE),    ATI Radeon XPRESS 200M 5A62 (PCIE),    ATI Radeon X300 (RV370) 5B60 (PCIE),    ATI Radeon X600 (RV370) 5B62 (PCIE),    ATI Radeon X550 (RV370) 5B63 (PCIE),    ATI FireGL V3100 (RV370) 5B64 (PCIE),    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),    ATI Mobility Radeon X800 XT (M28) (PCIE),    ATI Mobility FireGL V5100 (M28) (PCIE),    ATI Mobility Radeon X800 (M28) (PCIE), ATI
Radeon X850 5D4C (PCIE),    ATI Radeon X850 XT PE (R480) (PCIE),    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon
X850 PRO (R480) (PCIE),    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),    ATI Radeon X850 XT (R480) (PCIE),    ATI Radeon X800XT (R423) 5D57 (PCIE),    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon
X700 XT (RV410) (PCIE),    ATI Radeon X700 PRO (RV410) (PCIE),    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon
X700 (RV410) (PCIE),    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon
X1800,    ATI Mobility Radeon X1800 XT, ATI Mobility
Radeon X1800,    ATI Mobility FireGL V7200, ATI FireGL V7200,
ATI FireGL V5300,    ATI Mobility FireGL V7100, ATI Radeon X1800,
ATI Radeon X1800,    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon
X1800,    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon
X1600, ATI RV505,    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI
M54-GL,    ATI Mobility Radeon X1400, ATI Radeon
X1300/X1550,    ATI Radeon X1550 64-bit, ATI Mobility Radeon
X1300,    ATI Mobility Radeon X1300, ATI Mobility Radeon
X1300,    ATI Mobility Radeon X1300, ATI Radeon X1300,
ATI Radeon X1300,    ATI RV505, ATI RV505, ATI FireGL V3300, ATI
FireGL V3350,    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI
Radeon X1300/X1550,    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI
Mobility Radeon X1450,    ATI Radeon X1300/X1550, ATI Mobility Radeon
X2300,    ATI Mobility Radeon X2300, ATI Mobility Radeon
X1350,    ATI Mobility Radeon X1350, ATI Mobility Radeon
X1450,    ATI Radeon X1300, ATI Radeon X1550, ATI
Mobility Radeon X1350,    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI
Radeon X1600,    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon
X1600,    ATI Mobility FireGL V5200, ATI Mobility Radeon
X1600,    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon
X1600,    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL
V3400,    ATI Mobility FireGL V5250, ATI Mobility Radeon
X1700,    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,    ATI Mobility Radeon X1700, ATI Radeon X2300HD,    ATI Mobility Radeon HD 2300, ATI Mobility
Radeon HD 2300,    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon
X1950,    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon
X1900,    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon
X1900,    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon
X1900,    ATI AMD Stream Processor, ATI Radeon X1900, ATI
Radeon X1950,    ATI RV560, ATI RV560, ATI Mobility Radeon
X1900, ATI RV560,    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI
FireGL V7400,    ATI RV560, ATI Radeon X1650, ATI Radeon X1650,
ATI RV560,    ATI Radeon 9100 PRO IGP 7834, ATI Radeon
Mobility 9200 IGP 7835,    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon
X1200,    ATI Radeon X1200, ATI Radeon X1200, ATI RS740,
ATI RS740M, ATI RS740,    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon
HD 2900 XT,    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
ATI Radeon HD 2900 GT,    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL
V7600,    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,    ATI FirePro V8750 (FireGL), ATI FirePro V7760
(FireGL),    ATI Mobility RADEON HD 4850, ATI Mobility
RADEON HD 4850 X2,    ATI Radeon 4800 Series, ATI FirePro RV770, AMD
FireStream 9270,    AMD FireStream 9250, ATI FirePro V8700
(FireGL),    ATI Mobility RADEON HD 4870, ATI Mobility
RADEON M98,    ATI Mobility RADEON HD 4870, ATI Radeon 4800
Series,    ATI Radeon 4800 Series, ATI FirePro M7750, ATI
M98, ATI M98, ATI M98,    ATI Mobility Radeon HD 4650, ATI Radeon RV730
(AGP),    ATI Mobility Radeon HD 4670, ATI FirePro M5750,    ATI Mobility Radeon HD 4670, ATI Radeon RV730
(AGP),    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,    ATI Radeon HD 4600 Series, ATI RV730 PRO
[Radeon HD 4650],    ATI FirePro V7750 (FireGL), ATI FirePro V5700
(FireGL),    ATI FirePro V3750 (FireGL), ATI Mobility Radeon
HD 4830,    ATI Mobility Radeon HD 4850, ATI FirePro M7740,
ATI RV740,    ATI Radeon HD 4770, ATI Radeon HD 4700 Series,
ATI Radeon HD 4770,    ATI FirePro M5750, ATI RV610, ATI Radeon HD
2400 XT,    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO
AGP, ATI FireGL V4000,    ATI RV610, ATI Radeon HD 2350, ATI Mobility
Radeon HD 2400 XT,    ATI Mobility Radeon HD 2400, ATI RADEON E2400,
ATI RV610,    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,    ATI Mobility Radeon HD 3850 X2, ATI RV670,    ATI Mobility Radeon HD 3870, ATI Mobility
Radeon HD 3870 X2,    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI
Radeon HD3850,    ATI Radeon HD3690, AMD Firestream 9170, ATI
Radeon HD 4550,    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon
RV710,    ATI Radeon HD 4350, ATI Mobility Radeon 4300
Series,    ATI Mobility Radeon 4500 Series, ATI Mobility
Radeon 4500 Series,    ATI FirePro RG220, ATI Mobility Radeon 4330,
ATI RV630,    ATI Mobility Radeon HD 2600, ATI Mobility
Radeon HD 2600 XT,    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600
Pro AGP,    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro,
ATI Gemini RV630,    ATI Gemini Mobility Radeon HD 2600 XT, ATI
FireGL V5600,    ATI FireGL V3600, ATI Radeon HD 2600 LE,    ATI Mobility FireGL Graphics Processor, ATI
Radeon HD 3470,    ATI Mobility Radeon HD 3430, ATI Mobility
Radeon HD 3400 Series,    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI
Radeon HD 3430,    ATI Radeon HD 3450, ATI FirePro V3700, ATI
FireMV 2450,    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD
3600 Series,    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,    ATI Mobility Radeon HD 3650, ATI Mobility
Radeon HD 3670,    ATI Mobility FireGL V5700, ATI Mobility FireGL
V5725,    ATI Radeon HD 3200 Graphics, ATI Radeon 3100
Graphics,    ATI Radeon HD 3200 Graphics, ATI Radeon 3100
Graphics,    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200
Graphics,    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2,
SUMO2, SUMO2, SUMO2,    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI
Radeon HD 4200,    ATI Radeon 4100, ATI Mobility Radeon HD 4200,    ATI Mobility Radeon 4100, ATI Radeon HD 4290,
ATI Radeon HD 4250,    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310
Graphics,    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250
Graphics,    AMD Radeon HD 6300 Series Graphics,    AMD Radeon HD 6200 Series Graphics, PALM, PALM,
CYPRESS,    ATI FirePro (FireGL) Graphics Adapter,    ATI FirePro (FireGL) Graphics Adapter,    ATI FirePro (FireGL) Graphics Adapter, AMD
Firestream 9370,    AMD Firestream 9350, ATI Radeon HD 5800 Series,    ATI Radeon HD 5800 Series, ATI Radeon HD 5800
Series,    ATI Radeon HD 5800 Series, ATI Radeon HD 5900
Series,    ATI Radeon HD 5900 Series, ATI Mobility Radeon
HD 5800 Series,    ATI Mobility Radeon HD 5800 Series,    ATI FirePro (FireGL) Graphics Adapter,    ATI FirePro (FireGL) Graphics Adapter,    ATI Mobility Radeon HD 5800 Series, ATI Radeon
HD 5700 Series,    ATI Radeon HD 5700 Series, ATI Radeon HD 6700
Series,    ATI Radeon HD 5700 Series, ATI Radeon HD 6700
Series,    ATI Mobility Radeon HD 5000 Series,    ATI Mobility Radeon HD 5000 Series, ATI
Mobility Radeon HD 5570,    ATI FirePro (FireGL) Graphics Adapter,    ATI FirePro (FireGL) Graphics Adapter, ATI
Radeon HD 5670,    ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
REDWOOD,    ATI Mobility Radeon HD 5000 Series,    ATI Mobility Radeon HD 5000 Series, ATI
Mobility Radeon Graphics,    ATI Mobility Radeon Graphics, CEDAR,    ATI FirePro (FireGL) Graphics Adapter,    ATI FirePro (FireGL) Graphics Adapter, ATI
FirePro 2270, CEDAR,    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN,
CAYMAN, CAYMAN, CAYMAN,    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,    AMD Radeon HD 6900 Series, AMD Radeon HD 6900
Series, CAYMAN, CAYMAN,    CAYMAN, AMD Radeon HD 6900M Series, Mobility
Radeon HD 6000 Series,    BARTS, BARTS, Mobility Radeon HD 6000 Series,    Mobility Radeon HD 6000 Series, BARTS, BARTS,
BARTS, BARTS,    AMD Radeon HD 6800 Series, AMD Radeon HD 6800
Series,    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS,
TURKS, TURKS, TURKS,    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
TURKS, TURKS, TURKS, TURKS,    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
TURKS, TURKS, TURKS,    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
CAICOS, CAICOS,    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS[    17.831] (II) VESA: driver for VESA
chipsets: vesa[    17.831] (II) FBDEV: driver for framebuffer:
fbdev[    17.831] (++) using VT number 7

[    17.832] (II) Loading
/usr/lib/xorg/modules/drivers/radeon_drv.so[    17.832] (II) [KMS] Kernel modesetting
enabled.[    17.832] (WW) Falling back to old probe
method for vesa[    17.832] (WW) Falling back to old probe
method for fbdev[    17.832] (II) Loading sub module "fbdevhw"[    17.832] (II) LoadModule: "fbdevhw"[    17.832] (II) Loading
/usr/lib/xorg/modules/libfbdevhw.so[    17.832] (II) Module fbdevhw: vendor="X.Org
Foundation"[    17.832]     compiled for 1.11.3, module
version = 0.0.2[    17.832]     ABI class: X.Org Video Driver,
version 11.0[    17.833] (II) RADEON(0): Creating default
Display subsection in Screen section    "Default Screen Section" for
depth/fbbpp 24/32[    17.833] (==) RADEON(0): Depth 24, (--)
framebuffer bpp 32[    17.833] (II) RADEON(0): Pixel depth = 24
bits stored in 4 bytes (32 bpp pixmaps)[    17.833] (==) RADEON(0): Default visual is
TrueColor[    17.833] (==) RADEON(0): RGB weight 888[    17.833] (II) RADEON(0): Using 8 bits per
RGB (8 bit DAC)[    17.833] (--) RADEON(0): Chipset: "ATI
Radeon QD (AGP)" (ChipID = 0x5144)[    17.833] (II) RADEON(0): AGP card detected[    17.833] drmOpenDevice: node name is
/dev/dri/card0[    17.833] drmOpenDevice: open result is 9,
(OK)[    17.833] drmOpenByBusid: Searching for BusID
pci:0000:01:00.0[    17.833] drmOpenDevice: node name is
/dev/dri/card0[    17.833] drmOpenDevice: open result is 9,
(OK)[    17.833] drmOpenByBusid: drmOpenMinor
returns 9[    17.833] drmOpenByBusid: drmGetBusid reports
pci:0000:01:00.0[    17.833] (II) Loading sub module "exa"[    17.833] (II) LoadModule: "exa"[    17.833] (II) Loading
/usr/lib/xorg/modules/libexa.so[    17.834] (II) Module exa: vendor="X.Org
Foundation"[    17.834]     compiled for 1.11.3, module
version = 2.5.0[    17.834]     ABI class: X.Org Video Driver,
version 11.0[    17.834] (II) RADEON(0): KMS Color Tiling:
disabled[    17.834] (II) RADEON(0): KMS Pageflipping:
enabled[    17.834] (II) RADEON(0): SwapBuffers wait
for vsync: enabled[    17.988] (II) RADEON(0): Output VGA-0 has no
monitor section[    18.076] (II) RADEON(0): EDID for output
VGA-0[    18.076] (II) RADEON(0): Manufacturer: DEL 
Model: 71a5  Serial#: 1364218454[    18.076] (II) RADEON(0): Year: 1999  Week:
41[    18.076] (II) RADEON(0): EDID Version: 1.1[    18.076] (II) RADEON(0): Analog Display
Input,  Input Voltage Level: 0.700/0.300 V[    18.076] (II) RADEON(0): Sync:  Separate[    18.076] (II) RADEON(0): Max Image Size
[cm]: horiz.: 30  vert.: 23[    18.076] (II) RADEON(0): Gamma: 2.67[    18.076] (II) RADEON(0): DPMS capabilities:
StandBy Suspend Off; RGB/Color Display[    18.076] (II) RADEON(0): redX: 0.620 redY:
0.345   greenX: 0.290 greenY: 0.610[    18.076] (II) RADEON(0): blueX: 0.155 blueY:
0.065   whiteX: 0.281 whiteY: 0.311[    18.076] (II) RADEON(0): Supported
established timings:[    18.076] (II) RADEON(0): 720x400@70Hz[    18.076] (II) RADEON(0): 640x480@60Hz[    18.076] (II) RADEON(0): 640x480@75Hz[    18.076] (II) RADEON(0): 800x600@75Hz[    18.076] (II) RADEON(0): 1024x768@60Hz[    18.076] (II) RADEON(0): 1024x768@75Hz[    18.076] (II) RADEON(0): Manufacturer's
mask: 0[    18.076] (II) RADEON(0): Supported standard
timings:[    18.076] (II) RADEON(0): #0: hsize: 1024 
vsize 768  refresh: 85  vid: 22881[    18.076] (II) RADEON(0): #1: hsize: 800 
vsize 600  refresh: 85  vid: 22853[    18.076] (II) RADEON(0): #2: hsize: 1280 
vsize 1024  refresh: 60  vid: 32897[    18.076] (II) RADEON(0): #3: hsize: 640 
vsize 480  refresh: 85  vid: 22833[    18.076] (II) RADEON(0): Supported detailed
timing:[    18.076] (II) RADEON(0): clock: 28.3 MHz  
Image Size:  250 x 184 mm[    18.076] (II) RADEON(0): h_active: 720 
h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0[    18.076] (II) RADEON(0): v_active: 350 
v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0[    18.076] (II) RADEON(0): Serial No:
2742PEQPRVA9[    18.076] (II) RADEON(0): Monitor name: DELL
M770[    18.076] (II) RADEON(0): Ranges: V min: 48 V
max: 160 Hz, H min: 30 H max: 69 kHz,[    18.076] (II) RADEON(0): EDID (in hex):[    18.076] (II) RADEON(0):
    00ffffffffffff0010aca57156525051[    18.076] (II) RADEON(0):
    29090101081e17a7e8d5f29e584a9c27[    18.077] (II) RADEON(0):
    10484fa44a0061594559818031590101[    18.077] (II) RADEON(0):
    010101010101100bd0b4205e6310126c[    18.077] (II) RADEON(0):
    6208fab80000001a000000ff00323734[    18.077] (II) RADEON(0):
    3250455150525641390a000000fc0044[    18.077] (II) RADEON(0):
    454c4c204d3737300a202020000000fd[    18.077] (II) RADEON(0):
    0030a01e45ff000a20202020202000a2[    18.077] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[    18.077] (II) RADEON(0): Using EDID range
info for horizontal sync[    18.077] (II) RADEON(0): Using EDID range
info for vertical refresh[    18.077] (II) RADEON(0): Printing DDC
gathered Modelines:[    18.077] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[    18.077] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[    18.077] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[    18.077] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[    18.077] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[    18.077] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[    18.077] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[    18.077] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[    18.077] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[    18.077] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[    18.077] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[    18.077] (II) RADEON(0): Printing probed
modes for output VGA-0[    18.077] (II) RADEON(0): Modeline
"1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[    18.077] (II) RADEON(0): Modeline
"1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[    18.077] (II) RADEON(0): Modeline
"1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.1 kHz)[    18.077] (II) RADEON(0): Modeline
"1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[    18.077] (II) RADEON(0): Modeline
"800x600"x85.1   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[    18.077] (II) RADEON(0): Modeline
"800x600"x75.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[    18.077] (II) RADEON(0): Modeline
"640x480"x85.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[    18.077] (II) RADEON(0): Modeline
"640x480"x75.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[    18.077] (II) RADEON(0): Modeline
"640x480"x60.0   25.20  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[    18.077] (II) RADEON(0): Modeline
"720x400"x70.1   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[    18.077] (II) RADEON(0): Modeline
"720x350"x70.1   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[    18.077] (II) RADEON(0): Output VGA-0
connected[    18.077] (II) RADEON(0): Using exact sizes
for initial modes[    18.077] (II) RADEON(0): Output VGA-0 using
initial mode 1024x768[    18.077] (II) RADEON(0): Using default gamma
of (1.0, 1.0, 1.0) unless otherwise stated.[    18.077] (II) RADEON(0): mem size init: gart
size :fdff000 vram size: s:4000000 visible:3ac0000[    18.077] (II) RADEON(0): EXA: Driver will
allow EXA pixmaps in VRAM[    18.077] (**) RADEON(0): Display dimensions:
(300, 230) mm[    18.077] (**) RADEON(0): DPI set to (86, 84)[    18.077] (II) Loading sub module "fb"[    18.077] (II) LoadModule: "fb"[    18.078] (II) Loading
/usr/lib/xorg/modules/libfb.so[    18.078] (II) Module fb: vendor="X.Org
Foundation"[    18.078]     compiled for 1.11.3, module
version = 1.0.0[    18.078]     ABI class: X.Org ANSI C Emulation,
version 0.4[    18.078] (II) Loading sub module "ramdac"[    18.078] (II) LoadModule: "ramdac"[    18.078] (II) Module "ramdac"
already built-in[    18.078] (II) UnloadModule: "vesa"[    18.078] (II) Unloading vesa[    18.078] (II) UnloadModule: "fbdev"[    18.078] (II) Unloading fbdev[    18.078] (II) UnloadModule: "fbdevhw"[    18.078] (II) Unloading fbdevhw[    18.078] (--) Depth 24 pixmap format is 32
bpp[    18.078] (II) RADEON(0): [DRI2] Setup
complete[    18.078] (II) RADEON(0): [DRI2]   DRI
driver: radeon[    18.078] (II) RADEON(0): [DRI2]   VDPAU
driver: radeon[    18.078] (II) RADEON(0): Front buffer size:
3072K[    18.078] (II) RADEON(0): VRAM usage limit
set to 51379K[    18.078] (==) RADEON(0): Backing store
disabled[    18.078] (II) RADEON(0): Direct rendering
enabled[    18.079] (II) RADEON(0): Render acceleration
enabled for R100 type cards.[    18.079] (II) RADEON(0): Setting EXA
maxPitchBytes[    18.079] (II) EXA(0): Driver allocated
offscreen pixmaps[    18.079] (II) EXA(0): Driver registered
support for the following operations:[    18.079] (II)         Solid[    18.079] (II)         Copy[    18.079] (II)         Composite (RENDER
acceleration)[    18.079] (II)         UploadToScreen[    18.079] (II)         DownloadFromScreen[    18.079] (II) RADEON(0): Acceleration
enabled[    18.079] (==) RADEON(0): DPMS enabled[    18.079] (==) RADEON(0): Silken mouse
enabled[    18.079] (II) RADEON(0): Set up textured
video[    18.079] (II) RADEON(0): [XvMC] Associated
with Radeon Textured Video.[    18.079] (II) RADEON(0): [XvMC] Extension
initialized.[    18.079] (II) RADEON(0): RandR 1.2 enabled,
ignore the following RandR disabled message.[    18.079] (--) RandR disabled[    18.079] (II) Initializing built-in
extension Generic Event Extension[    18.079] (II) Initializing built-in
extension SHAPE[    18.079] (II) Initializing built-in
extension MIT-SHM[    18.079] (II) Initializing built-in
extension XInputExtension[    18.079] (II) Initializing built-in
extension XTEST[    18.079] (II) Initializing built-in
extension BIG-REQUESTS[    18.079] (II) Initializing built-in
extension SYNC[    18.079] (II) Initializing built-in
extension XKEYBOARD[    18.079] (II) Initializing built-in
extension XC-MISC[    18.079] (II) Initializing built-in
extension SECURITY[    18.079] (II) Initializing built-in
extension XINERAMA[    18.079] (II) Initializing built-in
extension XFIXES[    18.079] (II) Initializing built-in
extension RENDER[    18.079] (II) Initializing built-in
extension RANDR[    18.079] (II) Initializing built-in
extension COMPOSITE[    18.079] (II) Initializing built-in
extension DAMAGE[    18.110] (II) AIGLX: enabled
GLX_MESA_copy_sub_buffer[    18.110] (II) AIGLX: enabled
GLX_INTEL_swap_event[    18.110] (II) AIGLX: enabled
GLX_SGI_swap_control and GLX_MESA_swap_control[    18.110] (II) AIGLX:
GLX_EXT_texture_from_pixmap backed by buffer objects[    18.111] (II) AIGLX: Loaded and initialized
radeon[    18.111] (II) GLX: Initialized DRI2 GL
provider for screen 0[    18.168] (II) RADEON(0): Setting screen
physical size to 270 x 203[    18.203] (II) XKB: reuse xkmfile
/var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm[    18.213] (II) config/udev: Adding input
device Power Button (/dev/input/event1)[    18.213] (**) Power Button: Applying
InputClass "evdev keyboard catchall"[    18.213] (II) LoadModule: "evdev"[    18.213] (II) Loading
/usr/lib/xorg/modules/input/evdev_drv.so[    18.214] (II) Module evdev: vendor="X.Org
Foundation"[    18.214]     compiled for 1.11.3, module
version = 2.7.0[    18.214]     Module class: X.Org XInput Driver[    18.214]     ABI class: X.Org XInput driver,
version 16.0[    18.214] (II) Using input driver 'evdev' for
'Power Button'[    18.214] (II) Loading
/usr/lib/xorg/modules/input/evdev_drv.so[    18.214] (**) Power Button: always reports
core events[    18.214] (**) evdev: Power Button: Device:
"/dev/input/event1"[    18.214] (--) evdev: Power Button: Vendor 0
Product 0x1[    18.214] (--) evdev: Power Button: Found
keys[    18.214] (II) evdev: Power Button:
Configuring as keyboard[    18.214] (**) Option "config_info"
"udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"[    18.214] (II) XINPUT: Adding extended input
device "Power Button" (type: KEYBOARD, id 6)[    18.214] (**) Option "xkb_rules"
"evdev"[    18.214] (**) Option "xkb_model"
"pc105"[    18.214] (**) Option "xkb_layout"
"us"[    18.215] (II) config/udev: Adding input
device Power Button (/dev/input/event0)[    18.215] (**) Power Button: Applying
InputClass "evdev keyboard catchall"[    18.215] (II) Using input driver 'evdev' for
'Power Button'[    18.215] (II) Loading
/usr/lib/xorg/modules/input/evdev_drv.so[    18.215] (**) Power Button: always reports
core events[    18.215] (**) evdev: Power Button: Device:
"/dev/input/event0"[    18.217] (--) evdev: Power Button: Vendor 0
Product 0x1[    18.217] (--) evdev: Power Button: Found
keys[    18.217] (II) evdev: Power Button:
Configuring as keyboard[    18.218] (**) Option "config_info"
"udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"[    18.218] (II) XINPUT: Adding extended input
device "Power Button" (type: KEYBOARD, id 7)[    18.218] (**) Option "xkb_rules"
"evdev"[    18.218] (**) Option "xkb_model"
"pc105"[    18.218] (**) Option "xkb_layout"
"us"[    18.219] (II) config/udev: Adding input
device USB+PS/2 Optical Mouse (/dev/input/event3)[    18.219] (**) USB+PS/2 Optical Mouse:
Applying InputClass "evdev pointer catchall"[    18.219] (II) Using input driver 'evdev' for
'USB+PS/2 Optical Mouse'[    18.219] (II) Loading
/usr/lib/xorg/modules/input/evdev_drv.so[    18.219] (**) USB+PS/2 Optical Mouse: always
reports core events[    18.219] (**) evdev: USB+PS/2 Optical Mouse:
Device: "/dev/input/event3"[    18.219] (--) evdev: USB+PS/2 Optical Mouse:
Vendor 0x4f3 Product 0x230[    18.219] (--) evdev: USB+PS/2 Optical Mouse:
Found 3 mouse buttons[    18.219] (--) evdev: USB+PS/2 Optical Mouse:
Found scroll wheel(s)[    18.219] (--) evdev: USB+PS/2 Optical Mouse:
Found relative axes[    18.219] (--) evdev: USB+PS/2 Optical Mouse:
Found x and y relative axes[    18.219] (II) evdev: USB+PS/2 Optical Mouse:
Configuring as mouse[    18.219] (II) evdev: USB+PS/2 Optical Mouse:
Adding scrollwheel support[    18.219] (**) evdev: USB+PS/2 Optical Mouse:
YAxisMapping: buttons 4 and 5[    18.219] (**) evdev: USB+PS/2 Optical Mouse:
EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout:
200[    18.219] (**) Option "config_info"
"udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/input/input3/event3"[    18.219] (II) XINPUT: Adding extended input
device "USB+PS/2 Optical Mouse" (type: MOUSE, id 8)[    18.219] (II) evdev: USB+PS/2 Optical Mouse:
initialized for relative axes.[    18.220] (**) USB+PS/2 Optical Mouse:
(accel) keeping acceleration scheme 1[    18.220] (**) USB+PS/2 Optical Mouse:
(accel) acceleration profile 0[    18.220] (**) USB+PS/2 Optical Mouse:
(accel) acceleration factor: 2.000[    18.220] (**) USB+PS/2 Optical Mouse:
(accel) acceleration threshold: 4[    18.220] (II) config/udev: Adding input
device USB+PS/2 Optical Mouse (/dev/input/mouse0)[    18.220] (II) No input driver specified,
ignoring this device.[    18.220] (II) This device may have been
added with another device file.[    18.221] (II) config/udev: Adding input
device AT Translated Set 2 keyboard (/dev/input/event2)[    18.221] (**) AT Translated Set 2 keyboard:
Applying InputClass "evdev keyboard catchall"[    18.221] (II) Using input driver 'evdev' for
'AT Translated Set 2 keyboard'[    18.221] (II) Loading
/usr/lib/xorg/modules/input/evdev_drv.so[    18.221] (**) AT Translated Set 2 keyboard:
always reports core events[    18.221] (**) evdev: AT Translated Set 2
keyboard: Device: "/dev/input/event2"[    18.221] (--) evdev: AT Translated Set 2
keyboard: Vendor 0x1 Product 0x1[    18.221] (--) evdev: AT Translated Set 2
keyboard: Found keys[    18.221] (II) evdev: AT Translated Set 2
keyboard: Configuring as keyboard[    18.221] (**) Option "config_info"
"udev:/sys/devices/platform/i8042/serio0/input/input2/event2"[    18.221] (II) XINPUT: Adding extended input
device "AT Translated Set 2 keyboard" (type: KEYBOARD, id
9)[    18.221] (**) Option "xkb_rules"
"evdev"[    18.221] (**) Option "xkb_model"
"pc105"[    18.221] (**) Option "xkb_layout"
"us"[   960.033] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[   960.033] (II) RADEON(0): Using hsync ranges
from config file[   960.033] (II) RADEON(0): Using vrefresh
ranges from config file[   960.033] (II) RADEON(0): Printing DDC
gathered Modelines:[   960.033] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[   960.033] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[   960.033] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[   960.033] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[   960.033] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[   960.033] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[   960.033] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[   960.033] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[   960.033] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[   960.033] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[   960.033] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[  1601.814] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[  1601.827] (II) RADEON(0): Using hsync ranges
from config file[  1601.827] (II) RADEON(0): Using vrefresh
ranges from config file[  1601.827] (II) RADEON(0): Printing DDC
gathered Modelines:[  1601.827] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[  1601.827] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[  1601.827] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[  1601.827] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[  1601.827] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[  1601.827] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[  1601.827] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[  1601.827] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[  1601.827] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[  1601.827] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[  1601.827] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[  2401.197] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[  2401.197] (II) RADEON(0): Using hsync ranges
from config file[  2401.197] (II) RADEON(0): Using vrefresh
ranges from config file[  2401.197] (II) RADEON(0): Printing DDC
gathered Modelines:[  2401.197] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[  2401.197] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[  2401.197] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[  2401.197] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[  2401.197] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[  2401.197] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[  2401.197] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[  2401.197] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[  2401.197] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[  2401.197] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[  2401.197] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[  2423.944] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[  2423.944] (II) RADEON(0): Using hsync ranges
from config file[  2423.944] (II) RADEON(0): Using vrefresh
ranges from config file[  2423.944] (II) RADEON(0): Printing DDC
gathered Modelines:[  2423.944] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[  2423.944] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[  2423.944] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[  2423.944] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[  2423.944] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[  2423.944] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[  2423.944] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[  2423.944] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[  2423.944] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[  2423.944] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[  2423.944] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[  2424.105] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[  2424.105] (II) RADEON(0): Using hsync ranges
from config file[  2424.105] (II) RADEON(0): Using vrefresh
ranges from config file[  2424.105] (II) RADEON(0): Printing DDC
gathered Modelines:[  2424.105] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[  2424.105] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[  2424.105] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[  2424.105] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[  2424.105] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[  2424.105] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[  2424.105] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[  2424.105] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[  2424.105] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[  2424.105] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[  2424.105] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)[  2424.528] (II) RADEON(0): EDID vendor "DEL",
prod id 29093[  2424.528] (II) RADEON(0): Using hsync ranges
from config file[  2424.528] (II) RADEON(0): Using vrefresh
ranges from config file[  2424.528] (II) RADEON(0): Printing DDC
gathered Modelines:[  2424.529] (II) RADEON(0): Modeline
"720x350"x0.0   28.32  720 738 846 900  350 388 390 449
+hsync -vsync (31.5 kHz)[  2424.529] (II) RADEON(0): Modeline
"640x480"x0.0   31.50  640 656 720 840  480 481 484 500
-hsync -vsync (37.5 kHz)[  2424.529] (II) RADEON(0): Modeline
"640x480"x0.0   25.18  640 656 752 800  480 490 492 525
-hsync -vsync (31.5 kHz)[  2424.529] (II) RADEON(0): Modeline
"720x400"x0.0   28.32  720 738 846 900  400 412 414 449
-hsync +vsync (31.5 kHz)[  2424.529] (II) RADEON(0): Modeline
"1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772
800 +hsync +vsync (60.0 kHz)[  2424.529] (II) RADEON(0): Modeline
"1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777
806 -hsync -vsync (48.4 kHz)[  2424.529] (II) RADEON(0): Modeline
"800x600"x0.0   49.50  800 816 896 1056  600 601 604 625
+hsync +vsync (46.9 kHz)[  2424.529] (II) RADEON(0): Modeline
"1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772
808 +hsync +vsync (68.7 kHz)[  2424.529] (II) RADEON(0): Modeline
"800x600"x0.0   56.25  800 832 896 1048  600 601 604 631
+hsync +vsync (53.7 kHz)[  2424.529] (II) RADEON(0): Modeline
"1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025
1028 1066 +hsync +vsync (64.0 kHz)[  2424.529] (II) RADEON(0): Modeline
"640x480"x0.0   36.00  640 696 752 832  480 481 484 509
-hsync -vsync (43.3 kHz)
```

---

### Post by Yellow Pasque on 2014-07-27
^The spacing/indentation is really screwed up and that is very difficult to read.

> With kms we don't autodetect s-video connection anymore because it burns power and doesn't work reliably iirc.
[https://bugzilla.redhat.com/show_bug.cgi?id=465607](https://bugzilla.redhat.com/show_bug.cgi?id=465607)
See comment 18 on that bug for suggestions on how to get TV-out to show in xrandr (note that the user was ultimately unsuccessful).

---

### Post by ed_c2 on 2014-08-04
Sorry about the formatting, that's how the file was written. :(

I've tried those settings before, except nomodeset. And as the poster over there mentioned, screwing with the x configs can cause it to crash. (I've managed to do that several times already.) It'll probably have to wait till I can get back up there, because I can't do jack with if it anyway if I screw up while accessing it remotely.

---

### Post by ed_c2 on 2014-11-10
Finally got a chance to test the kernel parameters. "nomodeset" actually got the bootscreen on the TV, but then both displays go black and the PC seems to lockup. "3 nomodeset" gives a text version of the bootscreen on both, but then several errors  quickly flash by before going black. They all say something about "codec 0 is not valid". The picture I tried to take of the error messages didn't come out very well.

---

