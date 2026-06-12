---
title: "AMD ATI HD 5970 - X Error of failed request: BadRequest"
date: 2012-11-10
forum: Hardware
---

### Post by rXp on 2012-11-10
Hello,

With the arrival of steam on linux (and me having access to the beta), I decided to install linux on my gaming PC (linux has been on my work pc for years :)).

But now I'm getting hopeless so I need your help.
My goal is simple : install the latest drivers for my graphic card. The drivers is coming from the AMD support website.
I tried I-don't-know-how-much different ways to install it and all of them had the same issue... in the end I stumbled on this non-officiel AMD linux community wiki page. [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
There is a great step-by-step tutorial which should work for me, but...
I am on a newly installed Kubuntu 12.10 64b(I mean I formatted linux for every-try to have a clean installation)
Everything worked (download, build, installation) then I configured the xorg and rebooted, this is the list of command I used (from the tutorial) :
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic
sudo apt-get install ia32-libs lib32gcc1
cd /usr ; sudo ln -svT lib /usr/lib64
#I downloaded the file from the browser
unzip myfile.zip
chmod +x amd-drivers.run
sudo sh ./amd-driver.run --buildpkg Ubuntu/quantal
sudo dpkg -i fglrx*.deb

sudo amdconfig --initial -f --adapter=all #my 5790 is a dual gpu card
sudo amdconfig --set-pcs-str="DDX,EnableRandR12,FALSE" #I have 2 screens

sudo reboot
```

Now I try to get the information from fglrx :
```
rxp@rXp-PC:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

Again this error :s I don't know what to do

This is the xorg.conf :
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
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

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

And the log of xorg
```
[     4.146] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[     4.146] X Protocol Version 11, Revision 0
[     4.146] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[     4.146] Current Operating System: Linux rXp-PC 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[     4.146] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=4c3fd827-f329-4768-96f3-16fa49ee3d8f ro quiet splash vt.handoff=7
[     4.146] Build Date: 08 October 2012  03:34:01PM
[     4.146] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[     4.146] Current version of pixman: 0.26.0
[     4.146] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     4.146] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.146] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  9 21:09:16 2012
[     4.148] (==) Using config file: "/etc/X11/xorg.conf"
[     4.148] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.150] (==) ServerLayout "aticonfig Layout"
[     4.150] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     4.150] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     4.150] (**) |   |-->Device "aticonfig-Device[0]-0"
[     4.150] (**) |-->Screen "aticonfig-Screen[1]-0" (1)
[     4.150] (**) |   |-->Monitor "aticonfig-Monitor[1]-0"
[     4.150] (**) |   |-->Device "aticonfig-Device[1]-0"
[     4.150] (==) Automatically adding devices
[     4.150] (==) Automatically enabling devices
[     4.150] (==) Automatically adding GPU devices
[     4.152] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.152] 	Entry deleted from font path.
[     4.152] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.152] 	Entry deleted from font path.
[     4.152] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.152] 	Entry deleted from font path.
[     4.153] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.153] 	Entry deleted from font path.
[     4.153] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.153] 	Entry deleted from font path.
[     4.153] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     4.153] 	Entry deleted from font path.
[     4.153] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     4.153] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.153] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.153] (II) Loader magic: 0x7f2330000c40
[     4.153] (II) Module ABI versions:
[     4.153] 	X.Org ANSI C Emulation: 0.4
[     4.153] 	X.Org Video Driver: 13.0
[     4.153] 	X.Org XInput driver : 18.0
[     4.153] 	X.Org Server Extension : 7.0
[     4.155] (--) PCI:*(0:4:0:0) 1002:689c:1043:034a rev 0, Mem @ 0xc0000000/268435456, 0xf3cc0000/131072, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[     4.155] (--) PCI: (0:5:0:0) 1002:689c:1043:034a rev 0, Mem @ 0xd0000000/268435456, 0xf3de0000/131072, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
[     4.155] (II) Open ACPI successful (/var/run/acpid.socket)
[     4.156] Initializing built-in extension Generic Event Extension
[     4.156] Initializing built-in extension SHAPE
[     4.156] Initializing built-in extension MIT-SHM
[     4.156] Initializing built-in extension XInputExtension
[     4.156] Initializing built-in extension XTEST
[     4.156] Initializing built-in extension BIG-REQUESTS
[     4.156] Initializing built-in extension SYNC
[     4.156] Initializing built-in extension XKEYBOARD
[     4.156] Initializing built-in extension XC-MISC
[     4.156] Initializing built-in extension SECURITY
[     4.156] Initializing built-in extension XINERAMA
[     4.156] Initializing built-in extension XFIXES
[     4.156] Initializing built-in extension RENDER
[     4.156] Initializing built-in extension RANDR
[     4.156] Initializing built-in extension COMPOSITE
[     4.156] Initializing built-in extension DAMAGE
[     4.156] Initializing built-in extension MIT-SCREEN-SAVER
[     4.156] Initializing built-in extension DOUBLE-BUFFER
[     4.156] Initializing built-in extension RECORD
[     4.156] Initializing built-in extension DPMS
[     4.156] Initializing built-in extension X-Resource
[     4.156] Initializing built-in extension XVideo
[     4.156] Initializing built-in extension XVideo-MotionCompensation
[     4.156] Initializing built-in extension XFree86-VidModeExtension
[     4.156] Initializing built-in extension XFree86-DGA
[     4.156] Initializing built-in extension XFree86-DRI
[     4.156] Initializing built-in extension DRI2
[     4.156] (II) "glx" will be loaded by default.
[     4.156] (II) LoadModule: "glx"
[     4.156] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     4.159] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     4.159] 	compiled for 6.9.0, module version = 1.0.0
[     4.160] Loading extension GLX
[     4.160] (II) LoadModule: "fglrx"
[     4.160] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.194] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension
[     4.194] (II) UnloadModule: "fglrx"
[     4.194] (II) Unloading fglrx
[     4.194] (EE) Failed to load module "fglrx" (loader failed, 7)
[     4.194] (==) Matched fglrx as autoconfigured driver 0
[     4.194] (==) Matched ati as autoconfigured driver 1
[     4.194] (==) Matched vesa as autoconfigured driver 2
[     4.194] (==) Matched modesetting as autoconfigured driver 3
[     4.194] (==) Matched fbdev as autoconfigured driver 4
[     4.194] (==) Assigned the driver to the xf86ConfigLayout
[     4.194] (II) LoadModule: "fglrx"
[     4.194] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.205] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension
[     4.205] (II) UnloadModule: "fglrx"
[     4.205] (II) Unloading fglrx
[     4.205] (EE) Failed to load module "fglrx" (loader failed, 7)
[     4.205] (II) LoadModule: "ati"
[     4.205] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     4.206] (II) Module ati: vendor="X.Org Foundation"
[     4.206] 	compiled for 1.13.0, module version = 6.99.99
[     4.206] 	Module class: X.Org Video Driver
[     4.206] 	ABI class: X.Org Video Driver, version 13.0
[     4.206] (II) LoadModule: "radeon"
[     4.206] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     4.209] (II) Module radeon: vendor="X.Org Foundation"
[     4.209] 	compiled for 1.13.0, module version = 6.99.99
[     4.209] 	Module class: X.Org Video Driver
[     4.209] 	ABI class: X.Org Video Driver, version 13.0
[     4.209] (II) LoadModule: "vesa"
[     4.210] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.210] (II) Module vesa: vendor="X.Org Foundation"
[     4.210] 	compiled for 1.12.99.902, module version = 2.3.2
[     4.210] 	Module class: X.Org Video Driver
[     4.210] 	ABI class: X.Org Video Driver, version 13.0
[     4.210] (II) LoadModule: "modesetting"
[     4.210] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     4.211] (II) Module modesetting: vendor="X.Org Foundation"
[     4.211] 	compiled for 1.13.0, module version = 0.5.0
[     4.211] 	Module class: X.Org Video Driver
[     4.211] 	ABI class: X.Org Video Driver, version 13.0
[     4.211] (II) LoadModule: "fbdev"
[     4.211] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.212] (II) Module fbdev: vendor="X.Org Foundation"
[     4.212] 	compiled for 1.12.99.902, module version = 0.4.3
[     4.212] 	Module class: X.Org Video Driver
[     4.212] 	ABI class: X.Org Video Driver, version 13.0
[     4.212] (II) RADEON: Driver for ATI Radeon chipsets:
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
[     4.214] (II) VESA: driver for VESA chipsets: vesa
[     4.214] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.214] (II) FBDEV: driver for framebuffer: fbdev
[     4.214] (++) using VT number 7

[     4.215] (II) [KMS] drm report modesetting isn't supported.
[     4.215] vesa: Ignoring device with a bound kernel driver
[     4.215] (WW) Falling back to old probe method for vesa
[     4.215] (EE) open /dev/dri/card0: No such file or directory
[     4.215] (WW) Falling back to old probe method for modesetting
[     4.215] (EE) open /dev/dri/card0: No such file or directory
[     4.215] (II) Loading sub module "fbdevhw"
[     4.215] (II) LoadModule: "fbdevhw"
[     4.215] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.216] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.216] 	compiled for 1.13.0, module version = 0.0.2
[     4.216] 	ABI class: X.Org Video Driver, version 13.0
[     4.216] (**) FBDEV(3): claimed PCI slot 4@0:0:0
[     4.216] (II) FBDEV(3): using default device
[     4.216] (EE) Screen 0 deleted because of no matching config section.
[     4.216] (II) UnloadModule: "radeon"
[     4.216] (EE) Screen 0 deleted because of no matching config section.
[     4.216] (II) UnloadModule: "vesa"
[     4.216] (EE) Screen 0 deleted because of no matching config section.
[     4.216] (II) UnloadModule: "modesetting"
[     4.216] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[     4.216] (==) FBDEV(0): RGB weight 888
[     4.216] (==) FBDEV(0): Default visual is TrueColor
[     4.216] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     4.216] (II) FBDEV(0): hardware: VESA VGA (video memory: 5824kB)
[     4.216] (II) FBDEV(0): checking modes against framebuffer device...
[     4.216] (II) FBDEV(0): checking modes against monitor...
[     4.216] (--) FBDEV(0): Virtual size is 1400x1050 (pitch 1400)
[     4.216] (**) FBDEV(0):  Built-in mode "current": 147.0 MHz, 83.2 kHz, 77.4 Hz
[     4.216] (II) FBDEV(0): Modeline "current"x0.0  147.04  1400 1432 1600 1768  1050 1054 1058 1074 -hsync -vsync -csync (83.2 kHz b)
[     4.216] (==) FBDEV(0): DPI set to (96, 96)
[     4.216] (II) Loading sub module "fb"
[     4.216] (II) LoadModule: "fb"
[     4.216] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.217] (II) Module fb: vendor="X.Org Foundation"
[     4.217] 	compiled for 1.13.0, module version = 1.0.0
[     4.217] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.217] (**) FBDEV(0): using shadow framebuffer
[     4.217] (II) Loading sub module "shadow"
[     4.217] (II) LoadModule: "shadow"
[     4.218] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     4.218] (II) Module shadow: vendor="X.Org Foundation"
[     4.218] 	compiled for 1.13.0, module version = 1.1.0
[     4.218] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     4.218] (==) Depth 24 pixmap format is 32 bpp
[     4.218] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     4.220] (==) FBDEV(0): Backing store disabled
[     4.221] (**) FBDEV(0): DPMS enabled
[     4.221] (==) RandR enabled
[     4.226] (EE) GLX error: Can not get required symbols.
[     4.235] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.238] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     4.238] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.238] (II) LoadModule: "evdev"
[     4.239] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.241] (II) Module evdev: vendor="X.Org Foundation"
[     4.243] 	compiled for 1.13.0, module version = 2.7.3
[     4.243] 	Module class: X.Org XInput Driver
[     4.243] 	ABI class: X.Org XInput driver, version 18.0
[     4.243] (II) Using input driver 'evdev' for 'Power Button'
[     4.243] (**) Power Button: always reports core events
[     4.243] (**) evdev: Power Button: Device: "/dev/input/event1"
[     4.243] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.243] (--) evdev: Power Button: Found keys
[     4.243] (II) evdev: Power Button: Configuring as keyboard
[     4.243] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     4.243] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.243] (**) Option "xkb_rules" "evdev"
[     4.243] (**) Option "xkb_model" "pc105"
[     4.243] (**) Option "xkb_layout" "ch"
[     4.243] (**) Option "xkb_variant" "fr"
[     4.244] (II) XKB: reuse xkmfile /var/lib/xkb/server-53A4CFD27CBE694B87E57086754C176B71A8EEB5.xkm
[     4.245] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     4.245] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.245] (II) Using input driver 'evdev' for 'Power Button'
[     4.245] (**) Power Button: always reports core events
[     4.245] (**) evdev: Power Button: Device: "/dev/input/event0"
[     4.245] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.245] (--) evdev: Power Button: Found keys
[     4.245] (II) evdev: Power Button: Configuring as keyboard
[     4.245] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     4.245] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     4.245] (**) Option "xkb_rules" "evdev"
[     4.245] (**) Option "xkb_model" "pc105"
[     4.245] (**) Option "xkb_layout" "ch"
[     4.245] (**) Option "xkb_variant" "fr"
[     4.245] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event5)
[     4.245] (II) No input driver specified, ignoring this device.
[     4.245] (II) This device may have been added with another device file.
[     4.246] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event2)
[     4.246] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[     4.246] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[     4.246] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[     4.246] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event2"
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[     4.246] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[     4.246] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2/event2"
[     4.246] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 8)
[     4.246] (**) Option "xkb_rules" "evdev"
[     4.246] (**) Option "xkb_model" "pc105"
[     4.246] (**) Option "xkb_layout" "ch"
[     4.246] (**) Option "xkb_variant" "fr"
[     4.246] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[     4.246] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[     4.246] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[     4.246] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[     4.246] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found relative axes
[     4.246] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing relative x/y axes to exist.
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[     4.246] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing absolute x/y axes to exist.
[     4.246] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[     4.246] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[     4.246] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[     4.246] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[     4.246] (**) evdev: Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[     4.246] (**) evdev: Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.246] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3/event3"
[     4.246] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 9)
[     4.246] (**) Option "xkb_rules" "evdev"
[     4.246] (**) Option "xkb_model" "pc105"
[     4.246] (**) Option "xkb_layout" "ch"
[     4.246] (**) Option "xkb_variant" "fr"
[     4.247] (II) evdev: Microsoft Comfort Curve Keyboard 2000: initialized for relative axes.
[     4.247] (WW) evdev: Microsoft Comfort Curve Keyboard 2000: ignoring absolute axes.
[     4.247] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[     4.247] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[     4.247] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[     4.247] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[     4.247] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event4)
[     4.247] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[     4.247] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[     4.247] (**) Logitech USB Gaming Mouse: always reports core events
[     4.247] (**) evdev: Logitech USB Gaming Mouse: Device: "/dev/input/event4"
[     4.247] (--) evdev: Logitech USB Gaming Mouse: Vendor 0x46d Product 0xc049
[     4.247] (--) evdev: Logitech USB Gaming Mouse: Found 20 mouse buttons
[     4.247] (--) evdev: Logitech USB Gaming Mouse: Found scroll wheel(s)
[     4.247] (--) evdev: Logitech USB Gaming Mouse: Found relative axes
[     4.247] (--) evdev: Logitech USB Gaming Mouse: Found x and y relative axes
[     4.247] (II) evdev: Logitech USB Gaming Mouse: Configuring as mouse
[     4.247] (II) evdev: Logitech USB Gaming Mouse: Adding scrollwheel support
[     4.247] (**) evdev: Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[     4.247] (**) evdev: Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.247] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4/event4"
[     4.247] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE, id 10)
[     4.247] (II) evdev: Logitech USB Gaming Mouse: initialized for relative axes.
[     4.247] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[     4.247] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[     4.247] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[     4.247] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[     4.248] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[     4.248] (II) No input driver specified, ignoring this device.
[     4.248] (II) This device may have been added with another device file.
[     4.251] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     8.747] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
[     8.747] (II) No input driver specified, ignoring this device.
[     8.747] (II) This device may have been added with another device file.
[     8.748] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event6)
[     8.748] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[     8.748] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[     8.748] (**) PS/2 Generic Mouse: always reports core events
[     8.748] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event6"
[     8.748] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[     8.748] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[     8.748] (--) evdev: PS/2 Generic Mouse: Found relative axes
[     8.748] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[     8.748] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[     8.748] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[     8.748] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.748] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[     8.748] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 11)
[     8.749] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[     8.749] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[     8.749] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[     8.749] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[     8.749] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    12.816] (II) config/udev: Adding input device ROCCAT ROCCAT Valo (/dev/input/mouse2)
[    12.816] (II) No input driver specified, ignoring this device.
[    12.816] (II) This device may have been added with another device file.
[    12.817] (II) config/udev: Adding input device ROCCAT ROCCAT Valo (/dev/input/event7)
[    12.817] (**) ROCCAT ROCCAT Valo: Applying InputClass "evdev pointer catchall"
[    12.817] (**) ROCCAT ROCCAT Valo: Applying InputClass "evdev keyboard catchall"
[    12.817] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Valo'
[    12.817] (**) ROCCAT ROCCAT Valo: always reports core events
[    12.817] (**) evdev: ROCCAT ROCCAT Valo: Device: "/dev/input/event7"
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Vendor 0x1e7d Product 0x3201
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found 9 mouse buttons
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found scroll wheel(s)
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found relative axes
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found x and y relative axes
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found absolute axes
[    12.817] (II) evdev: ROCCAT ROCCAT Valo: Forcing absolute x/y axes to exist.
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found keys
[    12.817] (II) evdev: ROCCAT ROCCAT Valo: Configuring as mouse
[    12.817] (II) evdev: ROCCAT ROCCAT Valo: Configuring as keyboard
[    12.817] (II) evdev: ROCCAT ROCCAT Valo: Adding scrollwheel support
[    12.817] (**) evdev: ROCCAT ROCCAT Valo: YAxisMapping: buttons 4 and 5
[    12.817] (**) evdev: ROCCAT ROCCAT Valo: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.817] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input7/event7"
[    12.817] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Valo" (type: KEYBOARD, id 12)
[    12.817] (**) Option "xkb_rules" "evdev"
[    12.817] (**) Option "xkb_model" "pc105"
[    12.817] (**) Option "xkb_layout" "ch"
[    12.817] (**) Option "xkb_variant" "fr"
[    12.817] (II) evdev: ROCCAT ROCCAT Valo: initialized for relative axes.
[    12.817] (WW) evdev: ROCCAT ROCCAT Valo: ignoring absolute axes.
[    12.817] (**) ROCCAT ROCCAT Valo: (accel) keeping acceleration scheme 1
[    12.817] (**) ROCCAT ROCCAT Valo: (accel) acceleration profile 0
[    12.817] (**) ROCCAT ROCCAT Valo: (accel) acceleration factor: 2.000
[    12.817] (**) ROCCAT ROCCAT Valo: (accel) acceleration threshold: 4
[    12.817] (II) config/udev: Adding input device ROCCAT ROCCAT Valo (/dev/input/event8)
[    12.817] (**) ROCCAT ROCCAT Valo: Applying InputClass "evdev keyboard catchall"
[    12.817] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Valo'
[    12.817] (**) ROCCAT ROCCAT Valo: always reports core events
[    12.817] (**) evdev: ROCCAT ROCCAT Valo: Device: "/dev/input/event8"
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Vendor 0x1e7d Product 0x3201
[    12.817] (--) evdev: ROCCAT ROCCAT Valo: Found keys
[    12.817] (II) evdev: ROCCAT ROCCAT Valo: Configuring as keyboard
[    12.817] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input8/event8"
[    12.817] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Valo" (type: KEYBOARD, id 13)
[    12.817] (**) Option "xkb_rules" "evdev"
[    12.817] (**) Option "xkb_model" "pc105"
[    12.817] (**) Option "xkb_layout" "ch"
[    12.817] (**) Option "xkb_variant" "fr"
[    13.216] (II) config/udev: Adding input device C-Media USB Audio Device    (/dev/input/event9)
[    13.216] (**) C-Media USB Audio Device   : Applying InputClass "evdev keyboard catchall"
[    13.216] (II) Using input driver 'evdev' for 'C-Media USB Audio Device   '
[    13.216] (**) C-Media USB Audio Device   : always reports core events
[    13.216] (**) evdev: C-Media USB Audio Device   : Device: "/dev/input/event9"
[    13.216] (--) evdev: C-Media USB Audio Device   : Vendor 0xd8c Product 0x8
[    13.216] (--) evdev: C-Media USB Audio Device   : Found keys
[    13.216] (II) evdev: C-Media USB Audio Device   : Configuring as keyboard
[    13.216] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.3/input/input9/event9"
[    13.216] (II) XINPUT: Adding extended input device "C-Media USB Audio Device   " (type: KEYBOARD, id 14)
[    13.216] (**) Option "xkb_rules" "evdev"
[    13.216] (**) Option "xkb_model" "pc105"
[    13.216] (**) Option "xkb_layout" "ch"
[    13.216] (**) Option "xkb_variant" "fr"
[    14.695] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    14.698] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   134.795] (II) XKB: reuse xkmfile /var/lib/xkb/server-2E48696FBE4936A26EDD0BC6043189FEF62EA9E0.xkm

```

My card is compatible (it is even quoted in the wiki page).
Help me :)

Best regards,

rXp>!<

---

### Post by Rollback91 on 2012-11-10
Hi rXp,

can you please check if you have the radeon driver installed? 
Because your xorg.log shows
```
 
[     4.160] (II) LoadModule: "fglrx" [     4.160] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so [     4.194] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension [     4.194] (II) UnloadModule: "fglrx" [     4.194] (II) Unloading fglrx [     4.194] (EE) Failed to load module "fglrx" (loader failed, 7) [     4.194] (==) Matched fglrx as autoconfigured driver 0 [     4.194] (==) Matched ati as autoconfigured driver 1 [     4.194] (==) Matched vesa as autoconfigured driver 2 [     4.194] (==) Matched modesetting as autoconfigured driver 3 [     4.194] (==) Matched fbdev as autoconfigured driver 4 [     4.194] (==) Assigned the driver to the xf86ConfigLayout [     4.194] (II) LoadModule: "fglrx" [     4.194] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so [     4.205] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension [     4.205] (II) UnloadModule: "fglrx" [     4.205] (II) Unloading fglrx [     4.205] (EE) Failed to load module "fglrx" (loader failed, 7) [     4.205] (II) LoadModule: "ati" [     4.205] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so [     4.206] (II) Module ati: vendor="X.Org Foundation" [     4.206]     compiled for 1.13.0, module version = 6.99.99 [     4.206]     Module class: X.Org Video Driver [     4.206]     ABI class: X.Org Video Driver, version 13.0 [     4.206] (II) LoadModule: "radeon" [     4.206] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so [     4.209] (II) Module radeon: vendor="X.Org Foundation" [     4.209]     compiled for 1.13.0, module version = 6.99.99 [     4.209]     Module class: X.Org Video Driver [     4.209]     ABI class: X.Org Video Driver, version 13.0

```that it can't load the fglrx driver (idk why) and it loads the radeon one.

try to delete your xorg.conf and see how it goes!

Sorry for the english, and let me know how it goes!

[edit] can you also run lspci | grep VGA and post it here?

---

### Post by rXp on 2012-11-10
> **Rollback91 said:**
> Hi rXp,

can you please check if you have the radeon driver installed? 
Because your xorg.log shows
```
 
[     4.160] (II) LoadModule: "fglrx" [     4.160] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so [     4.194] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension [     4.194] (II) UnloadModule: "fglrx" [     4.194] (II) Unloading fglrx [     4.194] (EE) Failed to load module "fglrx" (loader failed, 7) [     4.194] (==) Matched fglrx as autoconfigured driver 0 [     4.194] (==) Matched ati as autoconfigured driver 1 [     4.194] (==) Matched vesa as autoconfigured driver 2 [     4.194] (==) Matched modesetting as autoconfigured driver 3 [     4.194] (==) Matched fbdev as autoconfigured driver 4 [     4.194] (==) Assigned the driver to the xf86ConfigLayout [     4.194] (II) LoadModule: "fglrx" [     4.194] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so [     4.205] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension [     4.205] (II) UnloadModule: "fglrx" [     4.205] (II) Unloading fglrx [     4.205] (EE) Failed to load module "fglrx" (loader failed, 7) [     4.205] (II) LoadModule: "ati" [     4.205] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so [     4.206] (II) Module ati: vendor="X.Org Foundation" [     4.206]     compiled for 1.13.0, module version = 6.99.99 [     4.206]     Module class: X.Org Video Driver [     4.206]     ABI class: X.Org Video Driver, version 13.0 [     4.206] (II) LoadModule: "radeon" [     4.206] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so [     4.209] (II) Module radeon: vendor="X.Org Foundation" [     4.209]     compiled for 1.13.0, module version = 6.99.99 [     4.209]     Module class: X.Org Video Driver [     4.209]     ABI class: X.Org Video Driver, version 13.0

```that it can't load the fglrx driver (idk why) and it loads the radeon one.

try to delete your xorg.conf and see how it goes!

Sorry for the english, and let me know how it goes!

[edit] can you also run lspci | grep VGA and post it here?
First of all :```
rxp@rXp-PC:~$ lspci | grep VGA
04:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Hemlock [Radeon HD 5900 Series]

```

I will edit this post in 2min to tell if deleting xorg helped.

EDIT: I deleted the xorg.conf and rebooted
Still the issue and this is the new log :
```
[     5.367] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[     5.367] X Protocol Version 11, Revision 0
[     5.367] Build Operating System: Linux 3.2.0-30-generic x86_64 Ubuntu
[     5.367] Current Operating System: Linux rXp-PC 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[     5.367] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=4c3fd827-f329-4768-96f3-16fa49ee3d8f ro quiet splash vt.handoff=7
[     5.367] Build Date: 08 October 2012  03:34:01PM
[     5.367] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     5.367] Current version of pixman: 0.26.0
[     5.367] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[     5.367] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.367] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 10 17:26:14 2012
[     5.368] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.368] (==) No Layout section.  Using the first Screen section.
[     5.368] (==) No screen section available. Using defaults.
[     5.368] (**) |-->Screen "Default Screen Section" (0)
[     5.368] (**) |   |-->Monitor "<default monitor>"
[     5.368] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     5.368] (==) Automatically adding devices
[     5.368] (==) Automatically enabling devices
[     5.368] (==) Automatically adding GPU devices
[     5.368] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.368] 	Entry deleted from font path.
[     5.368] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.368] 	Entry deleted from font path.
[     5.368] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.368] 	Entry deleted from font path.
[     5.368] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.368] 	Entry deleted from font path.
[     5.368] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.368] 	Entry deleted from font path.
[     5.368] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     5.368] 	Entry deleted from font path.
[     5.368] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     5.368] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.368] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.368] (II) Loader magic: 0x7f60c7af5c40
[     5.368] (II) Module ABI versions:
[     5.368] 	X.Org ANSI C Emulation: 0.4
[     5.368] 	X.Org Video Driver: 13.0
[     5.368] 	X.Org XInput driver : 18.0
[     5.368] 	X.Org Server Extension : 7.0
[     5.370] (--) PCI:*(0:4:0:0) 1002:689c:1043:034a rev 0, Mem @ 0xc0000000/268435456, 0xf3cc0000/131072, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[     5.370] (--) PCI: (0:5:0:0) 1002:689c:1043:034a rev 0, Mem @ 0xd0000000/268435456, 0xf3de0000/131072, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
[     5.370] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.370] Initializing built-in extension Generic Event Extension
[     5.371] Initializing built-in extension SHAPE
[     5.371] Initializing built-in extension MIT-SHM
[     5.371] Initializing built-in extension XInputExtension
[     5.371] Initializing built-in extension XTEST
[     5.371] Initializing built-in extension BIG-REQUESTS
[     5.371] Initializing built-in extension SYNC
[     5.371] Initializing built-in extension XKEYBOARD
[     5.371] Initializing built-in extension XC-MISC
[     5.371] Initializing built-in extension SECURITY
[     5.371] Initializing built-in extension XINERAMA
[     5.371] Initializing built-in extension XFIXES
[     5.371] Initializing built-in extension RENDER
[     5.371] Initializing built-in extension RANDR
[     5.371] Initializing built-in extension COMPOSITE
[     5.371] Initializing built-in extension DAMAGE
[     5.371] Initializing built-in extension MIT-SCREEN-SAVER
[     5.371] Initializing built-in extension DOUBLE-BUFFER
[     5.371] Initializing built-in extension RECORD
[     5.371] Initializing built-in extension DPMS
[     5.371] Initializing built-in extension X-Resource
[     5.371] Initializing built-in extension XVideo
[     5.371] Initializing built-in extension XVideo-MotionCompensation
[     5.371] Initializing built-in extension XFree86-VidModeExtension
[     5.371] Initializing built-in extension XFree86-DGA
[     5.371] Initializing built-in extension XFree86-DRI
[     5.371] Initializing built-in extension DRI2
[     5.371] (II) LoadModule: "glx"
[     5.371] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     5.371] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     5.371] 	compiled for 6.9.0, module version = 1.0.0
[     5.371] Loading extension GLX
[     5.371] (==) Matched fglrx as autoconfigured driver 0
[     5.371] (==) Matched ati as autoconfigured driver 1
[     5.371] (==) Matched vesa as autoconfigured driver 2
[     5.371] (==) Matched modesetting as autoconfigured driver 3
[     5.371] (==) Matched fbdev as autoconfigured driver 4
[     5.371] (==) Assigned the driver to the xf86ConfigLayout
[     5.371] (II) LoadModule: "fglrx"
[     5.372] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     5.382] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension
[     5.382] (II) UnloadModule: "fglrx"
[     5.382] (II) Unloading fglrx
[     5.382] (EE) Failed to load module "fglrx" (loader failed, 7)
[     5.382] (II) LoadModule: "ati"
[     5.383] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     5.383] (II) Module ati: vendor="X.Org Foundation"
[     5.383] 	compiled for 1.13.0, module version = 6.99.99
[     5.383] 	Module class: X.Org Video Driver
[     5.383] 	ABI class: X.Org Video Driver, version 13.0
[     5.383] (II) LoadModule: "radeon"
[     5.383] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     5.384] (II) Module radeon: vendor="X.Org Foundation"
[     5.384] 	compiled for 1.13.0, module version = 6.99.99
[     5.384] 	Module class: X.Org Video Driver
[     5.384] 	ABI class: X.Org Video Driver, version 13.0
[     5.384] (II) LoadModule: "vesa"
[     5.384] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.384] (II) Module vesa: vendor="X.Org Foundation"
[     5.384] 	compiled for 1.12.99.902, module version = 2.3.2
[     5.384] 	Module class: X.Org Video Driver
[     5.384] 	ABI class: X.Org Video Driver, version 13.0
[     5.384] (II) LoadModule: "modesetting"
[     5.384] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.384] (II) Module modesetting: vendor="X.Org Foundation"
[     5.384] 	compiled for 1.13.0, module version = 0.5.0
[     5.384] 	Module class: X.Org Video Driver
[     5.384] 	ABI class: X.Org Video Driver, version 13.0
[     5.384] (II) LoadModule: "fbdev"
[     5.385] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.385] (II) Module fbdev: vendor="X.Org Foundation"
[     5.385] 	compiled for 1.12.99.902, module version = 0.4.3
[     5.385] 	Module class: X.Org Video Driver
[     5.385] 	ABI class: X.Org Video Driver, version 13.0
[     5.385] (==) Matched fglrx as autoconfigured driver 0
[     5.385] (==) Matched ati as autoconfigured driver 1
[     5.385] (==) Matched vesa as autoconfigured driver 2
[     5.385] (==) Matched modesetting as autoconfigured driver 3
[     5.385] (==) Matched fbdev as autoconfigured driver 4
[     5.385] (==) Assigned the driver to the xf86ConfigLayout
[     5.385] (II) LoadModule: "fglrx"
[     5.385] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     5.396] (EE) Failed to load /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: noXFree86DRIExtension
[     5.396] (II) UnloadModule: "fglrx"
[     5.396] (II) Unloading fglrx
[     5.396] (EE) Failed to load module "fglrx" (loader failed, 7)
[     5.396] (II) LoadModule: "ati"
[     5.396] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     5.396] (II) Module ati: vendor="X.Org Foundation"
[     5.396] 	compiled for 1.13.0, module version = 6.99.99
[     5.396] 	Module class: X.Org Video Driver
[     5.396] 	ABI class: X.Org Video Driver, version 13.0
[     5.396] (II) LoadModule: "vesa"
[     5.396] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.396] (II) Module vesa: vendor="X.Org Foundation"
[     5.396] 	compiled for 1.12.99.902, module version = 2.3.2
[     5.396] 	Module class: X.Org Video Driver
[     5.396] 	ABI class: X.Org Video Driver, version 13.0
[     5.396] (II) UnloadModule: "vesa"
[     5.396] (II) Unloading vesa
[     5.396] (II) Failed to load module "vesa" (already loaded, 7)
[     5.396] (II) LoadModule: "modesetting"
[     5.397] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.397] (II) Module modesetting: vendor="X.Org Foundation"
[     5.397] 	compiled for 1.13.0, module version = 0.5.0
[     5.397] 	Module class: X.Org Video Driver
[     5.397] 	ABI class: X.Org Video Driver, version 13.0
[     5.397] (II) UnloadModule: "modesetting"
[     5.397] (II) Unloading modesetting
[     5.397] (II) Failed to load module "modesetting" (already loaded, 7)
[     5.397] (II) LoadModule: "fbdev"
[     5.397] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.397] (II) Module fbdev: vendor="X.Org Foundation"
[     5.397] 	compiled for 1.12.99.902, module version = 0.4.3
[     5.397] 	Module class: X.Org Video Driver
[     5.397] 	ABI class: X.Org Video Driver, version 13.0
[     5.397] (II) UnloadModule: "fbdev"
[     5.397] (II) Unloading fbdev
[     5.397] (II) Failed to load module "fbdev" (already loaded, 7)
[     5.397] (II) RADEON: Driver for ATI Radeon chipsets:
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
[     5.399] (II) VESA: driver for VESA chipsets: vesa
[     5.399] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.399] (II) FBDEV: driver for framebuffer: fbdev
[     5.399] (++) using VT number 7

[     5.399] (II) [KMS] drm report modesetting isn't supported.
[     5.400] vesa: Ignoring device with a bound kernel driver
[     5.400] vesa: Ignoring device with a bound kernel driver
[     5.400] (WW) Falling back to old probe method for vesa
[     5.400] (EE) open /dev/dri/card0: No such file or directory
[     5.400] (EE) open /dev/dri/card0: No such file or directory
[     5.400] (WW) Falling back to old probe method for modesetting
[     5.400] (EE) open /dev/dri/card0: No such file or directory
[     5.400] (EE) open /dev/dri/card0: No such file or directory
[     5.400] (II) Loading sub module "fbdevhw"
[     5.400] (II) LoadModule: "fbdevhw"
[     5.400] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.400] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.400] 	compiled for 1.13.0, module version = 0.0.2
[     5.400] 	ABI class: X.Org Video Driver, version 13.0
[     5.400] (**) FBDEV(5): claimed PCI slot 4@0:0:0
[     5.400] (II) FBDEV(5): using default device
[     5.400] (EE) Screen 0 deleted because of no matching config section.
[     5.400] (II) UnloadModule: "radeon"
[     5.400] (EE) Screen 0 deleted because of no matching config section.
[     5.400] (II) UnloadModule: "vesa"
[     5.400] (EE) Screen 0 deleted because of no matching config section.
[     5.400] (II) UnloadModule: "vesa"
[     5.400] (EE) Screen 0 deleted because of no matching config section.
[     5.400] (II) UnloadModule: "modesetting"
[     5.400] (EE) Screen 0 deleted because of no matching config section.
[     5.400] (II) UnloadModule: "modesetting"
[     5.400] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     5.400] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     5.400] (==) FBDEV(0): RGB weight 888
[     5.400] (==) FBDEV(0): Default visual is TrueColor
[     5.400] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.400] (II) FBDEV(0): hardware: VESA VGA (video memory: 5824kB)
[     5.400] (II) FBDEV(0): checking modes against framebuffer device...
[     5.400] (II) FBDEV(0): checking modes against monitor...
[     5.400] (--) FBDEV(0): Virtual size is 1400x1050 (pitch 1400)
[     5.400] (**) FBDEV(0):  Built-in mode "current": 147.0 MHz, 83.2 kHz, 77.4 Hz
[     5.400] (II) FBDEV(0): Modeline "current"x0.0  147.04  1400 1432 1600 1768  1050 1054 1058 1074 -hsync -vsync -csync (83.2 kHz b)
[     5.400] (==) FBDEV(0): DPI set to (96, 96)
[     5.400] (II) Loading sub module "fb"
[     5.400] (II) LoadModule: "fb"
[     5.400] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.400] (II) Module fb: vendor="X.Org Foundation"
[     5.400] 	compiled for 1.13.0, module version = 1.0.0
[     5.400] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     5.400] (**) FBDEV(0): using shadow framebuffer
[     5.400] (II) Loading sub module "shadow"
[     5.400] (II) LoadModule: "shadow"
[     5.400] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     5.401] (II) Module shadow: vendor="X.Org Foundation"
[     5.401] 	compiled for 1.13.0, module version = 1.1.0
[     5.401] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     5.401] (==) Depth 24 pixmap format is 32 bpp
[     5.401] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     5.401] (==) FBDEV(0): Backing store disabled
[     5.401] (==) FBDEV(0): DPMS enabled
[     5.401] (==) RandR enabled
[     5.405] (EE) GLX error: Can not get required symbols.
[     5.412] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.414] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     5.414] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.414] (II) LoadModule: "evdev"
[     5.414] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.414] (II) Module evdev: vendor="X.Org Foundation"
[     5.414] 	compiled for 1.13.0, module version = 2.7.3
[     5.414] 	Module class: X.Org XInput Driver
[     5.414] 	ABI class: X.Org XInput driver, version 18.0
[     5.414] (II) Using input driver 'evdev' for 'Power Button'
[     5.414] (**) Power Button: always reports core events
[     5.414] (**) evdev: Power Button: Device: "/dev/input/event1"
[     5.414] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.414] (--) evdev: Power Button: Found keys
[     5.414] (II) evdev: Power Button: Configuring as keyboard
[     5.414] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     5.414] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.414] (**) Option "xkb_rules" "evdev"
[     5.414] (**) Option "xkb_model" "pc105"
[     5.414] (**) Option "xkb_layout" "ch"
[     5.414] (**) Option "xkb_variant" "fr"
[     5.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-53A4CFD27CBE694B87E57086754C176B71A8EEB5.xkm
[     5.416] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.416] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.416] (II) Using input driver 'evdev' for 'Power Button'
[     5.416] (**) Power Button: always reports core events
[     5.416] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.416] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.416] (--) evdev: Power Button: Found keys
[     5.416] (II) evdev: Power Button: Configuring as keyboard
[     5.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     5.416] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     5.416] (**) Option "xkb_rules" "evdev"
[     5.416] (**) Option "xkb_model" "pc105"
[     5.416] (**) Option "xkb_layout" "ch"
[     5.416] (**) Option "xkb_variant" "fr"
[     5.417] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event5)
[     5.417] (II) No input driver specified, ignoring this device.
[     5.417] (II) This device may have been added with another device file.
[     5.417] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event2)
[     5.417] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[     5.417] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[     5.417] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[     5.417] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event2"
[     5.417] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[     5.417] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[     5.417] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[     5.417] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input2/event2"
[     5.417] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 8)
[     5.417] (**) Option "xkb_rules" "evdev"
[     5.417] (**) Option "xkb_model" "pc105"
[     5.417] (**) Option "xkb_layout" "ch"
[     5.417] (**) Option "xkb_variant" "fr"
[     5.417] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[     5.417] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[     5.417] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[     5.417] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[     5.417] (**) evdev: Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[     5.418] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Vendor 0x45e Product 0xdd
[     5.418] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[     5.418] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[     5.418] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found relative axes
[     5.418] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing relative x/y axes to exist.
[     5.418] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[     5.418] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Forcing absolute x/y axes to exist.
[     5.418] (--) evdev: Microsoft Comfort Curve Keyboard 2000: Found keys
[     5.418] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[     5.418] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[     5.418] (II) evdev: Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[     5.418] (**) evdev: Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[     5.418] (**) evdev: Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.418] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input3/event3"
[     5.418] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD, id 9)
[     5.418] (**) Option "xkb_rules" "evdev"
[     5.418] (**) Option "xkb_model" "pc105"
[     5.418] (**) Option "xkb_layout" "ch"
[     5.418] (**) Option "xkb_variant" "fr"
[     5.418] (II) evdev: Microsoft Comfort Curve Keyboard 2000: initialized for relative axes.
[     5.418] (WW) evdev: Microsoft Comfort Curve Keyboard 2000: ignoring absolute axes.
[     5.418] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[     5.418] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[     5.418] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[     5.418] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[     5.418] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/event4)
[     5.418] (**) Logitech USB Gaming Mouse: Applying InputClass "evdev pointer catchall"
[     5.418] (II) Using input driver 'evdev' for 'Logitech USB Gaming Mouse'
[     5.418] (**) Logitech USB Gaming Mouse: always reports core events
[     5.418] (**) evdev: Logitech USB Gaming Mouse: Device: "/dev/input/event4"
[     5.418] (--) evdev: Logitech USB Gaming Mouse: Vendor 0x46d Product 0xc049
[     5.418] (--) evdev: Logitech USB Gaming Mouse: Found 20 mouse buttons
[     5.418] (--) evdev: Logitech USB Gaming Mouse: Found scroll wheel(s)
[     5.418] (--) evdev: Logitech USB Gaming Mouse: Found relative axes
[     5.418] (--) evdev: Logitech USB Gaming Mouse: Found x and y relative axes
[     5.418] (II) evdev: Logitech USB Gaming Mouse: Configuring as mouse
[     5.418] (II) evdev: Logitech USB Gaming Mouse: Adding scrollwheel support
[     5.418] (**) evdev: Logitech USB Gaming Mouse: YAxisMapping: buttons 4 and 5
[     5.418] (**) evdev: Logitech USB Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     5.418] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4/event4"
[     5.418] (II) XINPUT: Adding extended input device "Logitech USB Gaming Mouse" (type: MOUSE, id 10)
[     5.418] (II) evdev: Logitech USB Gaming Mouse: initialized for relative axes.
[     5.418] (**) Logitech USB Gaming Mouse: (accel) keeping acceleration scheme 1
[     5.418] (**) Logitech USB Gaming Mouse: (accel) acceleration profile 0
[     5.418] (**) Logitech USB Gaming Mouse: (accel) acceleration factor: 2.000
[     5.418] (**) Logitech USB Gaming Mouse: (accel) acceleration threshold: 4
[     5.419] (II) config/udev: Adding input device Logitech USB Gaming Mouse (/dev/input/mouse0)
[     5.419] (II) No input driver specified, ignoring this device.
[     5.419] (II) This device may have been added with another device file.
[     5.422] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    10.095] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
[    10.095] (II) No input driver specified, ignoring this device.
[    10.095] (II) This device may have been added with another device file.
[    10.096] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event6)
[    10.096] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    10.096] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[    10.096] (**) PS/2 Generic Mouse: always reports core events
[    10.096] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event6"
[    10.096] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[    10.096] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[    10.096] (--) evdev: PS/2 Generic Mouse: Found relative axes
[    10.096] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[    10.096] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[    10.096] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    10.096] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.096] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    10.096] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 11)
[    10.096] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[    10.096] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[    10.096] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[    10.096] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[    10.096] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    12.824] (II) config/udev: Adding input device ROCCAT ROCCAT Valo (/dev/input/event8)
[    12.824] (**) ROCCAT ROCCAT Valo: Applying InputClass "evdev keyboard catchall"
[    12.824] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Valo'
[    12.824] (**) ROCCAT ROCCAT Valo: always reports core events
[    12.824] (**) evdev: ROCCAT ROCCAT Valo: Device: "/dev/input/event8"
[    12.824] (--) evdev: ROCCAT ROCCAT Valo: Vendor 0x1e7d Product 0x3201
[    12.824] (--) evdev: ROCCAT ROCCAT Valo: Found keys
[    12.824] (II) evdev: ROCCAT ROCCAT Valo: Configuring as keyboard
[    12.824] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input8/event8"
[    12.824] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Valo" (type: KEYBOARD, id 12)
[    12.824] (**) Option "xkb_rules" "evdev"
[    12.824] (**) Option "xkb_model" "pc105"
[    12.824] (**) Option "xkb_layout" "ch"
[    12.824] (**) Option "xkb_variant" "fr"
[    12.826] (II) config/udev: Adding input device ROCCAT ROCCAT Valo (/dev/input/mouse2)
[    12.826] (II) No input driver specified, ignoring this device.
[    12.826] (II) This device may have been added with another device file.
[    12.826] (II) config/udev: Adding input device ROCCAT ROCCAT Valo (/dev/input/event7)
[    12.826] (**) ROCCAT ROCCAT Valo: Applying InputClass "evdev pointer catchall"
[    12.826] (**) ROCCAT ROCCAT Valo: Applying InputClass "evdev keyboard catchall"
[    12.826] (II) Using input driver 'evdev' for 'ROCCAT ROCCAT Valo'
[    12.826] (**) ROCCAT ROCCAT Valo: always reports core events
[    12.826] (**) evdev: ROCCAT ROCCAT Valo: Device: "/dev/input/event7"
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Vendor 0x1e7d Product 0x3201
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Found 9 mouse buttons
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Found scroll wheel(s)
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Found relative axes
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Found x and y relative axes
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Found absolute axes
[    12.826] (II) evdev: ROCCAT ROCCAT Valo: Forcing absolute x/y axes to exist.
[    12.826] (--) evdev: ROCCAT ROCCAT Valo: Found keys
[    12.826] (II) evdev: ROCCAT ROCCAT Valo: Configuring as mouse
[    12.826] (II) evdev: ROCCAT ROCCAT Valo: Configuring as keyboard
[    12.826] (II) evdev: ROCCAT ROCCAT Valo: Adding scrollwheel support
[    12.826] (**) evdev: ROCCAT ROCCAT Valo: YAxisMapping: buttons 4 and 5
[    12.826] (**) evdev: ROCCAT ROCCAT Valo: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    12.826] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input7/event7"
[    12.826] (II) XINPUT: Adding extended input device "ROCCAT ROCCAT Valo" (type: KEYBOARD, id 13)
[    12.826] (**) Option "xkb_rules" "evdev"
[    12.826] (**) Option "xkb_model" "pc105"
[    12.826] (**) Option "xkb_layout" "ch"
[    12.826] (**) Option "xkb_variant" "fr"
[    12.826] (II) evdev: ROCCAT ROCCAT Valo: initialized for relative axes.
[    12.826] (WW) evdev: ROCCAT ROCCAT Valo: ignoring absolute axes.
[    12.826] (**) ROCCAT ROCCAT Valo: (accel) keeping acceleration scheme 1
[    12.826] (**) ROCCAT ROCCAT Valo: (accel) acceleration profile 0
[    12.826] (**) ROCCAT ROCCAT Valo: (accel) acceleration factor: 2.000
[    12.826] (**) ROCCAT ROCCAT Valo: (accel) acceleration threshold: 4
[    13.229] (II) config/udev: Adding input device C-Media USB Audio Device    (/dev/input/event9)
[    13.229] (**) C-Media USB Audio Device   : Applying InputClass "evdev keyboard catchall"
[    13.229] (II) Using input driver 'evdev' for 'C-Media USB Audio Device   '
[    13.229] (**) C-Media USB Audio Device   : always reports core events
[    13.229] (**) evdev: C-Media USB Audio Device   : Device: "/dev/input/event9"
[    13.229] (--) evdev: C-Media USB Audio Device   : Vendor 0xd8c Product 0x8
[    13.229] (--) evdev: C-Media USB Audio Device   : Found keys
[    13.229] (II) evdev: C-Media USB Audio Device   : Configuring as keyboard
[    13.229] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.3/input/input9/event9"
[    13.229] (II) XINPUT: Adding extended input device "C-Media USB Audio Device   " (type: KEYBOARD, id 14)
[    13.229] (**) Option "xkb_rules" "evdev"
[    13.229] (**) Option "xkb_model" "pc105"
[    13.229] (**) Option "xkb_layout" "ch"
[    13.229] (**) Option "xkb_variant" "fr"
[    13.598] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    13.605] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    94.635] (II) XKB: reuse xkmfile /var/lib/xkb/server-2E48696FBE4936A26EDD0BC6043189FEF62EA9E0.xkm
```

---

### Post by Rollback91 on 2012-11-10
Some weeks ago i read that fglrx is not supported on xorg 1.3 and the new ubuntu use it..
May it be the problem?

read this topic, it talks about it 
[http://ubuntuforums.org/showthread.php?p=12314020#post12314020](http://ubuntuforums.org/showthread.php?p=12314020#post12314020)

Btw is there any problems for you switching to the open-source driver?

[edit] this post too: [http://ubuntuforums.org/showthread.php?t=2069243&page=2](http://ubuntuforums.org/showthread.php?t=2069243&page=2)

---

### Post by rXp on 2012-11-10
> **Rollback91 said:**
> Some weeks ago i read that fglrx is not supported on xorg 1.3 and the new ubuntu use it..
May it be the problem?

read this topic, it talks about it 
[http://ubuntuforums.org/showthread.php?p=12314020#post12314020](http://ubuntuforums.org/showthread.php?p=12314020#post12314020)

Btw is there any problems for you switching to the open-source driver?

[edit] this post too: [http://ubuntuforums.org/showthread.php?t=2069243&page=2](http://ubuntuforums.org/showthread.php?t=2069243&page=2)
Thank you I will try with kubuntu 12.04 and tell how it works.
And about the open-source driver it wouldn't be worth it because this is my "gaming pc" and I doing the dual boot to beta-test steam on it and later throw windows away ;)

---

### Post by Rollback91 on 2012-11-10
> **rXp said:**
> Thank you I will try with kubuntu 12.04 and tell how it works.
And about the open-source driver it wouldn't be worth it because this is my "gaming pc" and I doing the dual boot to beta-test steam on it and later throw windows away ;)
Allright, I had problems with the ATI driver too (hybrid muxless ATI/ATI) and i tried installing the open-source driver and now everything works fine, I can even play world of warcraft with an high frame rate.. Just saying that the open-suorce driver are not bad at all!
Btw have a nice beta testing! :D

---

### Post by rXp on 2012-11-10
Hi again,

It works with kubuntu 12.04 ! THANK YOU !
I have my extend desktop setup, both my screens have 120hz settings and 3D acceleration is working :) 
Thank you again ! I would never have found this solution :)

---

### Post by Rollback91 on 2012-11-10
> **rXp said:**
> Hi again,

It works with kubuntu 12.04 ! THANK YOU !
I have my extend desktop setup, both my screens have 120hz settings and 3D acceleration is working :) 
Thank you again ! I would never have found this solution :)

Wow, im glad you resolve :) your problem please mark it as [solved] so other people may find this helpfull! and if you can make a comparison between the ATI driver and the open-source one using Steam it would be greate :D

---

