---
title: "Ati drivers on Ubuntu 12.10"
date: 2012-11-17
forum: Hardware
---

### Post by FakeJack on 2012-11-17
This is the computer where i tried to install Ubuntu 12.10:

  
[LIST]
[*]CPU_AMD Athlon XP 2000+
[*]Memory_2GB Ram
[*]Video_Ati Radeon 9600 PRO Series 256MB
[*]SO_Ubuntu 12.10
[/LIST]
  The installation went ok, but at first boot, screen resolution was  very low and i wasn't able to change it. I don't have 3D Acceleration  and i can't install ATI drivers. Fresh install or not, i have the same problem with another computer with a different ati card.

  I did many research, but i found nothing that could solve my problem, except for [http://askubuntu.com/questions/134878/no-xorg-conf-and-cannot-detect-ati-radeon-9600-pro-video-card-12-04](http://askubuntu.com/questions/134878/no-xorg-conf-and-cannot-detect-ati-radeon-9600-pro-video-card-12-04).  I made a fresh install, not an upgrade, so i can't recover my old  xorg.conf file or change it, like the link says; plus, there is no  xorg.conf file. Even if i create it, there's nothing that works.

  I know this thing [http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx](http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx) about cards no longer supported; mine isn't there. I also tried [http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/](http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/)  (on a second fresh install) and at reboot desktop didn't show up.  That's the result whenever i try to install ati drivers (or any other  video drivers) this way or another (from software center, repositories,  ppas...). I don't know how to change resolution and how to install  working drivers.

---

### Post by Carlos Araujo on 2012-11-17
welcome to the club.Quantal also not working quantal also not work with hybrid graphics (example: AMD/INTEL and others).Maybe a long wait yet.

I hope in the next version. will be?

---

### Post by FakeJack on 2012-11-17
I hope so. I have the same problem with a PackardBell Notebook with a more recent chip, the Radeon Xpress 200m with an intel cpu. Luckly the resolution is right, but ther's no 3d acceleration (can't watch youtube videos, games, graphic...)

---

### Post by Carlos Araujo on 2012-11-17
My system:

DELL INSPIRON 14z
HYBRID GRAPHICS INTEL HD/AMD HD 7570M

no solution yet !!!

---

### Post by Cheesemill on 2012-11-17
You are already using the only driver available for your graphics card in Ubuntu 12.10.

ATI dropped Linux support for the 9600 series over 3 years ago.

---

### Post by Carlos Araujo on 2012-11-17
Cheesemill, including RADEON HD 7570M ?

---

### Post by Cheesemill on 2012-11-17
> **Carlos Araujo said:**
> Cheesemill, including RADEON HD 7570M ?
No.

Please start a separate thread for your issues. Your problems have nothing to do with the problem that the OP has with his 9600.

---

### Post by Yellow Pasque on 2012-11-17
@FakeJack: post /var/log/Xorg.0.log from your non-working system

---

### Post by FakeJack on 2012-11-17
> **Temüjin said:**
> @FakeJack: post /var/log/Xorg.0.log from your non-working system

Actually i can't login. After i tried to install new drivers, the screen is black even if i try to run recovery mode

---

### Post by Yellow Pasque on 2012-11-18
> **FakeJack said:**
> Actually i can't login. After i tried to install new drivers, the screen is black even if i try to run recovery mode
Then you installed the wrong drivers..

---

### Post by Cheesemill on 2012-11-18
As I mentioned above ***there are no other drivers*** that you can install.

The only drivers for your card that work with Ubuntu 12.10 are the ones which come loaded as standard with a Ubuntu installation.

---

### Post by FakeJack on 2012-11-18
> **Cheesemill said:**
> As I mentioned above ***there are no other drivers*** that you can install.

The only drivers for your card that work with Ubuntu 12.10 are the ones which come loaded as standard with a Ubuntu installation.
I installed ati drivers the way explained by the links i've posted; and many other ways, but ati drivers everytime. Each of this driver bring to an end: black screen at first reboot. The problem is, i can't use ubuntu with the driver it provides because of very low resolution and no graphic acceleration. If ther is absolutely no other way to solve this, i wonder if i have to choose another version of ubuntu...

---

### Post by QIII on 2012-11-18
The most recent version of Ubuntu that will work with a proprietary Linux driver for your card is 9.04.  This is because the driver has been moved to a legacy support branch and the legacy driver will not work with any X Server post 2008.

There is no work around, hack or solution.  This is not unique to Ubuntu.  It applies to any Linux distribution that uses X Server and the version of X Server is post 2008.  So even going to another distro will be fruitless.

Nobody in the Linux community has any control over this.  The decision to move the driver support for your card to a legacy branch was the sole responsibility of AMD/ATI.

Unlike those who recently encountered the decision by AMD to move the HD 2XXX to HD 4XXX models to a legacy driver branch, you do not have the option to downgrade X Server and use an older driver.  Even for those who can do that, it is a work around and not a solution.  Its utility will inevitably be dashed.

Again, as others above have stated several times:  There is no "solution" for you.  No instructions you find on the web will work, so there is no point in searching for them and trying them only to be frustrated.  You are left only with using the open source Radeon driver with its limited capabilities.  That driver is what the open source community has been able to do to maintain the continued operation of your card -- and the developers have done an extremely good job considering that the code for the original driver is closed and they cannot reverse engineer the hardware.

Or you can purchase another card -- an HD 5xxx series or greater.

---

### Post by Carlos Araujo on 2012-11-18
it solves?

FEATURE HIGHLIGHTS OF THE AMD CATALYST 12.11 BETA8 DRIVER

AMD Catalyst 12.11 Beta8 is now available, and includes the following updates:
(Please note that AMD Catalyst 12.11 Beta8 includes all of the fixes found in previous versions of AMD Catalyst 12.11 Beta)

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx)

---

### Post by QIII on 2012-11-18
> **Carlos Araujo said:**
> it solves?

No.  That driver will not work with FakeJack's card.

From the url you provided:

This article applies to the following configuration(s): **Hardware:**
 
[LIST]
[*]AMD Radeon HD 7900 Series
[*]AMD Radeon HD 7800 Series
[*]AMD Radeon HD 7700 Series
[*]AMD Radeon HD 6000 Series
[*]AMD Radeon HD 5000 Series
[*]AMD Mobility Radeon HD 7000M Series
[*]AMD Mobility Radeon HD 6000M Series
[*]AMD Mobility Radeon HD 5000 Series
[/LIST]


If you are having a problem with a different card than FakeJack, *please start a new thread.*

---

### Post by Yellow Pasque on 2012-11-18
FakeJack, you need to remove the proprietary fglrx/Catalyst driver and boot using the open-source/default ati driver. Then, post the Xorg log. Until we see a log, no one can tell you why you have wrong resolution.

---

### Post by FakeJack on 2012-11-19
> **Temüjin said:**
> FakeJack, you need to remove the proprietary fglrx/Catalyst driver and boot using the open-source/default ati driver. Then, post the Xorg log. Until we see a log, no one can tell you why you have wrong resolution.
> [   724.317] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   724.317] X Protocol Version 11, Revision 0
[   724.317] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[   724.317] Current Operating System: Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[   724.317] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[   724.317] Build Date: 08 October 2012  03:34:08PM
[   724.317] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   724.317] Current version of pixman: 0.26.0
[   724.317]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   724.317] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   724.317] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 19 14:49:39 2012
[   724.319] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   724.320] (==) No Layout section.  Using the first Screen section.
[   724.320] (==) No screen section available. Using defaults.
[   724.320] (**) |-->Screen "Default Screen Section" (0)
[   724.320] (**) |   |-->Monitor "<default monitor>"
[   724.320] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   724.320] (==) Automatically adding devices
[   724.320] (==) Automatically enabling devices
[   724.320] (==) Automatically adding GPU devices
[   724.321] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   724.321]     Entry deleted from font path.
[   724.321] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   724.321]     Entry deleted from font path.
[   724.321] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   724.321]     Entry deleted from font path.
[   724.321] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   724.321]     Entry deleted from font path.
[   724.321] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   724.321]     Entry deleted from font path.
[   724.322] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   724.322]     Entry deleted from font path.
[   724.322] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   724.322] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   724.322] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   724.322] (II) Loader magic: 0xb771b640
[   724.322] (II) Module ABI versions:
[   724.322]     X.Org ANSI C Emulation: 0.4
[   724.322]     X.Org Video Driver: 13.0
[   724.322]     X.Org XInput driver : 18.0
[   724.322]     X.Org Server Extension : 7.0
[   724.323] (II) config/udev: Adding drm device (/dev/dri/card0)
[   724.325] (--) PCI:*(0:1:0:0) 1002:4150:174b:0200 rev 0, Mem @ 0xe0000000/268435456, 0xbf800000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
[   724.325] (--) PCI: (0:1:0:1) 1002:4170:174b:0201 rev 0, Mem @ 0xc0000000/268435456, 0xbf000000/65536
[   724.326] (II) Open ACPI successful (/var/run/acpid.socket)
[   724.326] Initializing built-in extension Generic Event Extension
[   724.326] Initializing built-in extension SHAPE
[   724.326] Initializing built-in extension MIT-SHM
[   724.326] Initializing built-in extension XInputExtension
[   724.326] Initializing built-in extension XTEST
[   724.326] Initializing built-in extension BIG-REQUESTS
[   724.326] Initializing built-in extension SYNC
[   724.326] Initializing built-in extension XKEYBOARD
[   724.326] Initializing built-in extension XC-MISC
[   724.326] Initializing built-in extension SECURITY
[   724.326] Initializing built-in extension XINERAMA
[   724.326] Initializing built-in extension XFIXES
[   724.326] Initializing built-in extension RENDER
[   724.326] Initializing built-in extension RANDR
[   724.326] Initializing built-in extension COMPOSITE
[   724.326] Initializing built-in extension DAMAGE
[   724.326] Initializing built-in extension MIT-SCREEN-SAVER
[   724.326] Initializing built-in extension DOUBLE-BUFFER
[   724.326] Initializing built-in extension RECORD
[   724.326] Initializing built-in extension DPMS
[   724.326] Initializing built-in extension X-Resource
[   724.326] Initializing built-in extension XVideo
[   724.326] Initializing built-in extension XVideo-MotionCompensation
[   724.327] Initializing built-in extension XFree86-VidModeExtension
[   724.327] Initializing built-in extension XFree86-DGA
[   724.327] Initializing built-in extension XFree86-DRI
[   724.327] Initializing built-in extension DRI2
[   724.327] (II) LoadModule: "glx"
[   724.329] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   724.329] (II) Module glx: vendor="X.Org Foundation"
[   724.329]     compiled for 1.13.0, module version = 1.0.0
[   724.329]     ABI class: X.Org Server Extension, version 7.0
[   724.329] (==) AIGLX enabled
[   724.329] Loading extension GLX
[   724.330] (==) Matched fglrx as autoconfigured driver 0
[   724.330] (==) Matched ati as autoconfigured driver 1
[   724.330] (==) Matched fglrx as autoconfigured driver 2
[   724.330] (==) Matched ati as autoconfigured driver 3
[   724.330] (==) Matched vesa as autoconfigured driver 4
[   724.330] (==) Matched modesetting as autoconfigured driver 5
[   724.330] (==) Matched fbdev as autoconfigured driver 6
[   724.330] (==) Assigned the driver to the xf86ConfigLayout
[   724.330] (II) LoadModule: "fglrx"
[   724.331] (WW) Warning, couldn't open module fglrx
[   724.331] (II) UnloadModule: "fglrx"
[   724.331] (II) Unloading fglrx
[   724.331] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   724.331] (II) LoadModule: "ati"
[   724.332] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   724.332] (II) Module ati: vendor="X.Org Foundation"
[   724.332]     compiled for 1.13.0, module version = 6.99.99
[   724.332]     Module class: X.Org Video Driver
[   724.332]     ABI class: X.Org Video Driver, version 13.0
[   724.332] (II) LoadModule: "radeon"
[   724.333] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   724.334] (II) Module radeon: vendor="X.Org Foundation"
[   724.334]     compiled for 1.13.0, module version = 6.99.99
[   724.334]     Module class: X.Org Video Driver
[   724.334]     ABI class: X.Org Video Driver, version 13.0
[   724.334] (II) LoadModule: "vesa"
[   724.335] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   724.335] (II) Module vesa: vendor="X.Org Foundation"
[   724.335]     compiled for 1.12.99.902, module version = 2.3.2
[   724.335]     Module class: X.Org Video Driver
[   724.335]     ABI class: X.Org Video Driver, version 13.0
[   724.335] (II) LoadModule: "modesetting"
[   724.335] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   724.335] (II) Module modesetting: vendor="X.Org Foundation"
[   724.336]     compiled for 1.13.0, module version = 0.5.0
[   724.336]     Module class: X.Org Video Driver
[   724.336]     ABI class: X.Org Video Driver, version 13.0
[   724.336] (II) LoadModule: "fbdev"
[   724.336] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   724.336] (II) Module fbdev: vendor="X.Org Foundation"
[   724.336]     compiled for 1.12.99.902, module version = 0.4.3
[   724.336]     Module class: X.Org Video Driver
[   724.336]     ABI class: X.Org Video Driver, version 13.0
[   724.336] (==) Matched fglrx as autoconfigured driver 0
[   724.336] (==) Matched ati as autoconfigured driver 1
[   724.336] (==) Matched fglrx as autoconfigured driver 2
[   724.336] (==) Matched ati as autoconfigured driver 3
[   724.336] (==) Matched vesa as autoconfigured driver 4
[   724.336] (==) Matched modesetting as autoconfigured driver 5
[   724.336] (==) Matched fbdev as autoconfigured driver 6
[   724.337] (==) Assigned the driver to the xf86ConfigLayout
[   724.337] (II) LoadModule: "fglrx"
[   724.338] (WW) Warning, couldn't open module fglrx
[   724.338] (II) UnloadModule: "fglrx"
[   724.338] (II) Unloading fglrx
[   724.338] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   724.338] (II) LoadModule: "ati"
[   724.338] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   724.338] (II) Module ati: vendor="X.Org Foundation"
[   724.338]     compiled for 1.13.0, module version = 6.99.99
[   724.338]     Module class: X.Org Video Driver
[   724.338]     ABI class: X.Org Video Driver, version 13.0
[   724.338] (II) LoadModule: "vesa"
[   724.339] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   724.339] (II) Module vesa: vendor="X.Org Foundation"
[   724.339]     compiled for 1.12.99.902, module version = 2.3.2
[   724.339]     Module class: X.Org Video Driver
[   724.339]     ABI class: X.Org Video Driver, version 13.0
[   724.339] (II) UnloadModule: "vesa"
[   724.339] (II) Unloading vesa
[   724.339] (II) Failed to load module "vesa" (already loaded, 0)
[   724.339] (II) LoadModule: "modesetting"
[   724.339] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   724.339] (II) Module modesetting: vendor="X.Org Foundation"
[   724.339]     compiled for 1.13.0, module version = 0.5.0
[   724.339]     Module class: X.Org Video Driver
[   724.339]     ABI class: X.Org Video Driver, version 13.0
[   724.339] (II) UnloadModule: "modesetting"
[   724.339] (II) Unloading modesetting
[   724.339] (II) Failed to load module "modesetting" (already loaded, 0)
[   724.339] (II) LoadModule: "fbdev"
[   724.340] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   724.340] (II) Module fbdev: vendor="X.Org Foundation"
[   724.340]     compiled for 1.12.99.902, module version = 0.4.3
[   724.340]     Module class: X.Org Video Driver
[   724.340]     ABI class: X.Org Video Driver, version 13.0
[   724.340] (II) UnloadModule: "fbdev"
[   724.340] (II) Unloading fbdev
[   724.340] (II) Failed to load module "fbdev" (already loaded, 0)
[   724.340] (II) RADEON: Driver for ATI Radeon chipsets:
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
[   724.346] (II) VESA: driver for VESA chipsets: vesa
[   724.346] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   724.346] (II) FBDEV: driver for framebuffer: fbdev
[   724.346] (++) using VT number 7

[   724.346] (II) [KMS] Kernel modesetting enabled.
[   724.346] (WW) Falling back to old probe method for vesa
[   724.346] (WW) Falling back to old probe method for modesetting
[   724.346] (WW) Falling back to old probe method for fbdev
[   724.346] (II) Loading sub module "fbdevhw"
[   724.346] (II) LoadModule: "fbdevhw"
[   724.347] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   724.347] (II) Module fbdevhw: vendor="X.Org Foundation"
[   724.348]     compiled for 1.13.0, module version = 0.0.2
[   724.348]     ABI class: X.Org Video Driver, version 13.0
[   724.348] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   724.348] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   724.348] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   724.348] (==) RADEON(0): Default visual is TrueColor
[   724.348] (==) RADEON(0): RGB weight 888
[   724.348] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   724.348] (--) RADEON(0): Chipset: "ATI Radeon 9600 AP (AGP)" (ChipID = 0x4150)
[   724.348] (II) Loading sub module "dri2"
[   724.348] (II) LoadModule: "dri2"
[   724.348] (II) Module "dri2" already built-in
[   724.348] (II) Loading sub module "exa"
[   724.348] (II) LoadModule: "exa"
[   724.349] (II) Loading /usr/lib/xorg/modules/libexa.so
[   724.349] (II) Module exa: vendor="X.Org Foundation"
[   724.349]     compiled for 1.13.0, module version = 2.6.0
[   724.349]     ABI class: X.Org Video Driver, version 13.0
[   724.349] (II) RADEON(0): KMS Color Tiling: enabled
[   724.349] (II) RADEON(0): KMS Pageflipping: enabled
[   724.349] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[   724.379] (II) RADEON(0): Output VGA-0 has no monitor section
[   724.382] (II) RADEON(0): Output DVI-0 has no monitor section
[   724.392] (II) RADEON(0): Output S-video has no monitor section
[   724.422] (II) RADEON(0): EDID for output VGA-0
[   724.422] (II) RADEON(0): Manufacturer: SAM  Model: 2  Serial#: 1129197877
[   724.422] (II) RADEON(0): Year: 2001  Week: 29
[   724.422] (II) RADEON(0): EDID Version: 1.2
[   724.422] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   724.422] (II) RADEON(0): Sync:  SeparateSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
[   724.422] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[   724.422] (II) RADEON(0): Gamma: 1.97
[   724.422] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   724.422] (II) RADEON(0): First detailed timing is preferred mode
[   724.422] (II) RADEON(0): redX: 0.620 redY: 0.330   greenX: 0.290 greenY: 0.590
[   724.422] (II) RADEON(0): blueX: 0.140 blueY: 0.110   whiteX: 0.300 whiteY: 0.330
[   724.422] (II) RADEON(0): Supported established timings:
[   724.422] (II) RADEON(0): 720x400@70Hz
[   724.422] (II) RADEON(0): 640x480@60Hz
[   724.422] (II) RADEON(0): 640x480@67Hz
[   724.422] (II) RADEON(0): 640x480@75Hz
[   724.422] (II) RADEON(0): 800x600@56Hz
[   724.422] (II) RADEON(0): 800x600@60Hz
[   724.422] (II) RADEON(0): 800x600@75Hz
[   724.422] (II) RADEON(0): 832x624@75Hz
[   724.422] (II) RADEON(0): 1024x768@60Hz
[   724.422] (II) RADEON(0): 1024x768@70Hz
[   724.422] (II) RADEON(0): 1024x768@75Hz
[   724.422] (II) RADEON(0): Manufacturer's mask: 0
[   724.422] (II) RADEON(0): Supported standard timings:
[   724.422] (II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
[   724.422] (II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
[   724.422] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[   724.422] (II) RADEON(0): Supported detailed timing:
[   724.422] (II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[   724.422] (II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[   724.422] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[   724.422] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 61 kHz, PixClock max 85 MHz
[   724.422] (II) RADEON(0): Monitor name: 570V TFT
[   724.422] (II) RADEON(0): Serial No: H1CR715972
[   724.422] (II) RADEON(0): EDID (in hex):
[   724.422] (II) RADEON(0):     00ffffffffffff004c2d020035314e43
[   724.422] (II) RADEON(0):     1d0b0102091e1761eae4de9e544a9723
[   724.422] (II) RADEON(0):     1c4c54b76e00314f454f614f01010101
[   724.422] (II) RADEON(0):     01010101010164190040410026301888
[   724.422] (II) RADEON(0):     360030e410000018000000fd00324b1e
[   724.422] (II) RADEON(0):     3d08000a202020202020000000fc0035
[   724.422] (II) RADEON(0):     373056205446540a20202020000000ff
[   724.422] (II) RADEON(0):     00483143523731353937320a20200050
[   724.422] (II) RADEON(0): Printing probed modes for output VGA-0
[   724.422] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz eP)
[   724.423] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   724.423] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   724.423] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   724.423] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[   724.423] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   724.423] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   724.423] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   724.423] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   724.423] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   724.423] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[   724.423] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   724.423] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   724.423] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   724.423] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   724.423] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   724.425] (II) RADEON(0): EDID for output DVI-0
[   724.435] (II) RADEON(0): EDID for output S-video
[   724.435] (II) RADEON(0): Printing probed modes for output S-video
[   724.435] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz eP)
[   724.435] (II) RADEON(0): Output VGA-0 connected
[   724.435] (II) RADEON(0): Output DVI-0 disconnected
[   724.435] (II) RADEON(0): Output S-video connected
[   724.435] (II) RADEON(0): Using exact sizes for initial modes
[   724.435] (II) RADEON(0): Output VGA-0 using initial mode 800x600
[   724.435] (II) RADEON(0): Output S-video using initial mode 800x600
[   724.435] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   724.435] (II) RADEON(0): mem size init: gart size :3dff000 vram size: s:10000000 visible:fcc0000
[   724.435] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[   724.435] (==) RADEON(0): DPI set to (96, 96)
[   724.435] (II) Loading sub module "fb"
[   724.435] (II) LoadModule: "fb"
[   724.436] (II) Loading /usr/lib/xorg/modules/libfb.so
[   724.437] (II) Module fb: vendor="X.Org Foundation"
[   724.437]     compiled for 1.13.0, module version = 1.0.0
[   724.437]     ABI class: X.Org ANSI C Emulation, version 0.4
[   724.437] (II) Loading sub module "ramdac"
[   724.437] (II) LoadModule: "ramdac"
[   724.437] (II) Module "ramdac" already built-in
[   724.437] (II) UnloadModule: "vesa"
[   724.437] (II) Unloading vesa
[   724.437] (II) UnloadModule: "modesetting"
[   724.437] (II) Unloading modesetting
[   724.437] (II) UnloadModule: "fbdev"
[   724.437] (II) Unloading fbdev
[   724.437] (II) UnloadSubModule: "fbdevhw"
[   724.437] (II) Unloading fbdevhw
[   724.437] (--) Depth 24 pixmap format is 32 bpp
[   724.437] (II) RADEON(0): [DRI2] Setup complete
[   724.437] (II) RADEON(0): [DRI2]   DRI driver: r300
[   724.437] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[   724.438] (II) RADEON(0): Front buffer size: 1976K
[   724.438] (II) RADEON(0): VRAM usage limit set to 231156K
[   724.438] (==) RADEON(0): Backing store disabled
[   724.438] (II) RADEON(0): Direct rendering enabled
[   724.438] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[   724.438] (II) RADEON(0): Setting EXA maxPitchBytes
[   724.438] (II) EXA(0): Driver allocated offscreen pixmaps
[   724.438] (II) EXA(0): Driver registered support for the following operations:
[   724.438] (II)         Solid
[   724.438] (II)         Copy
[   724.438] (II)         Composite (RENDER acceleration)
[   724.438] (II)         UploadToScreen
[   724.438] (II)         DownloadFromScreen
[   724.438] (II) RADEON(0): Acceleration enabled
[   724.438] (==) RADEON(0): DPMS enabled
[   724.438] (==) RADEON(0): Silken mouse enabled
[   724.438] (II) RADEON(0): Set up textured video
[   724.439] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[   724.439] (II) RADEON(0): [XvMC] Extension initialized.
[   724.439] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   724.492] (--) RandR disabled
[   724.538] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   724.538] (II) AIGLX: enabled GLX_INTEL_swap_event
[   724.538] (II) AIGLX: enabled GLX_ARB_create_context
[   724.538] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   724.538] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   724.538] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   724.538] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   724.539] (II) AIGLX: Loaded and initialized r300
[   724.539] (II) GLX: Initialized DRI2 GL provider for screen 0
[   724.603] (II) RADEON(0): Setting screen physical size to 211 x 158
[   724.628] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   724.638] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   724.638] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   724.638] (II) LoadModule: "evdev"
[   724.639] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   724.641] (II) Module evdev: vendor="X.Org Foundation"
[   724.641]     compiled for 1.13.0, module version = 2.7.3
[   724.641]     Module class: X.Org XInput Driver
[   724.641]     ABI class: X.Org XInput driver, version 18.0
[   724.641] (II) Using input driver 'evdev' for 'Power Button'
[   724.641] (**) Power Button: always reports core events
[   724.641] (**) evdev: Power Button: Device: "/dev/input/event1"
[   724.641] (--) evdev: Power Button: Vendor 0 Product 0x1
[   724.641] (--) evdev: Power Button: Found keys
[   724.641] (II) evdev: Power Button: Configuring as keyboard
[   724.641] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   724.641] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   724.641] (**) Option "xkb_rules" "evdev"
[   724.641] (**) Option "xkb_model" "pc105"
[   724.641] (**) Option "xkb_layout" "us"
[   724.643] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   724.643] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   724.643] (II) Using input driver 'evdev' for 'Power Button'
[   724.643] (**) Power Button: always reports core events
[   724.643] (**) evdev: Power Button: Device: "/dev/input/event0"
[   724.643] (--) evdev: Power Button: Vendor 0 Product 0x1
[   724.643] (--) evdev: Power Button: Found keys
[   724.643] (II) evdev: Power Button: Configuring as keyboard
[   724.643] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   724.643] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   724.643] (**) Option "xkb_rules" "evdev"
[   724.643] (**) Option "xkb_model" "pc105"
[   724.644] (**) Option "xkb_layout" "us"
[   724.645] (II) config/udev: Adding drm device (/dev/dri/card0)
[   724.646] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event3)
[   724.646] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[   724.646] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[   724.646] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[   724.646] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event3"
[   724.646] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc00e
[   724.646] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[   724.646] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[   724.646] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[   724.646] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[   724.646] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[   724.646] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[   724.646] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[   724.646] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   724.647] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1.3/3-1.3:1.0/input/input3/event3"
[   724.647] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8)
[   724.647] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[   724.647] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[   724.647] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[   724.647] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[   724.647] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[   724.648] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[   724.648] (II) No input driver specified, ignoring this device.
[   724.648] (II) This device may have been added with another device file.
[   724.649] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   724.649] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   724.649] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   724.649] (**) AT Translated Set 2 keyboard: always reports core events
[   724.649] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   724.649] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   724.649] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   724.649] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   724.649] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   724.649] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   724.649] (**) Option "xkb_rules" "evdev"
[   724.649] (**) Option "xkb_model" "pc105"
[   724.649] (**) Option "xkb_layout" "us"
[   746.184] (II) XKB: reuse xkmfile /var/lib/xkb/server-C83295E770C8F7DAB74E1291706D8738A1018C30.xkm
Here's the log from Xorg0.log.

@QIII: i didn't mean to complain, sorry if that was the impression. Last time i used ubuntu was some years ago; i noticed a great improvement, especially for the driver side. I just wanted to know more about a problem that seem "unfixable", i know that this come from ATI/AMD.

---

### Post by Yellow Pasque on 2012-11-19
Okay, thanks for the log. What resolution are you trying to achieve? What does this command show?:
```
xrandr -q
```

Note that Unity probably has a frontend for xrandr, but I'm not a Unity user and I do things via the commandline.

---

### Post by kdford on 2012-11-19
I saw somebody previous get slammed in this topic for discussing a card that was not an ATI 9600 like the OP's card, but the thread title was 'ATI drivers on Ubuntu 12.10' so maybe this is the right place...

I have an ATI Radeon 3400 (in a Lenovo T400) -- When I run the ATI card (in discreet graphics mode), I get strange visual artifacts on the screen (Image attached).. does this seem like it'd be related to the lack of ATI Proprietary drivers?

That same "shearing?" effect can be seen on many other tooltips (but oddly it will only affect some at any given time while others will be OK).. and it will affect parts of my desktop background and some parts of application windows (typically the edges)

Any thoughts?

---

### Post by QIII on 2012-11-19
The "right place" to post would be a new thread. That will get you help specifically for your issue and won't confound this thread by attempting to answer two separate questions.

Yours is an issue raised by more recent changes.

Nobody is trying to "slam" anyone.  It is simply easier to deal with one issue at a time in a thread and make sure FakeJack gets full attention on his problem.

---

### Post by FakeJack on 2012-11-20
> **Temüjin said:**
> Okay, thanks for the log. What resolution are you trying to achieve? What does this command show?:
```
xrandr -q
```Note that Unity probably has a frontend for xrandr, but I'm not a Unity user and I do things via the commandline.
Here it is
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA-0 connected 800x600+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768       60.0 +   75.1     75.0     70.1  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2* 
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        59.9*+
```
I would like to be able to set 1024x768

---

### Post by FakeJack on 2012-11-22
No way to change resolution?

---

### Post by Yellow Pasque on 2012-11-22
The manpage for xrandr is good reading.
Try:
```
xrandr --output VGA-0 --mode 1024x768
```

---

### Post by FakeJack on 2012-11-22
It works! Resolution changed to 1024x768. Thanks for help!

(is resolution going to remain changed, or i have to change it everytime with this command?)

For now i think i keep 12.10. When need proper drivers and graphic acceleration i will install 9.04 on this PC. I have another notebook with an ATI Radeon Xpress 200M, no driver support for it too, i suppose (right?). The graphic is ok with drivers provided, the only thing i can't understand, is why i can't watch youtube's video and films in fullscreen mode, while i can with Windows 7. Is this driver-related?

---

### Post by Yellow Pasque on 2012-11-23
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)
Try minitube on the other notebook, as flash plugin is not accelerated by GPU and is a major CPU hog.

---

