---
title: "Problem getting GDM to restart following an attempted driver install"
date: 2010-03-09
forum: Hardware
---

### Post by Kir_B on 2010-03-09
[SIZE=1]Hey all. My cousin and I are in dire need of some help, and any and all  help would be much appreciated. Please keep in mind that we are  relatively new to linux, but aren't completely green.

 We are having a nightmare restarting the GDM after a failed attempt at  installing the drivers for a [/SIZE]  [SIZE=1][GeForce FX 5200 256MB 128-bit DDR PCI]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16814133233").

 I know that the one question that a lot of you will want to know is, why  didn't we just use the drivers in the Synaptic or the ones supplied in  the Hardware drivers via Administration. The answer is as follows; the  computer is fairly old and near as we can tell, the motherboard, an  ASRock P4i45GV, doesn't have any onboard graphics and so it won't allow  us to install any drivers without the new card installed. [/SIZE]  [SIZE=1]

 Initially with the new card _installed_, we couldn't get anything past the  grub screen into Ubuntu {Karmic}, and all we could get is the black  screen of death. [/SIZE]  [SIZE=1]

 Following the attempted installation of the [UNIX]("http://www.nvidia.com/object/unix.html") [/SIZE]  [SIZE=1]drivers supplied from  the [NVIDIA]("http://www.nvidia.com/object/unix.html")[/SIZE][SIZE=1] site, which required us to stop the GDM, we are no longer  able to restart the GDM making it quite impossible for us to advance our  little project. 

 Everything works fine in the Windows XP, but when we try to get into  Ubuntu in normal mode, with it installed, all we get is a black screen,  but after doing a Control+Alt we get the "(initramfs)" prompt. If we try  to get into Ubuntu in recovery kernel mode with the new card installed,  all we get is the "(initramfs)" prompt.[/SIZE]  [SIZE=1]

 With the new card _not installed_, we get the following message (no  mattter which Kernel is used): "Ubuntu is running in low-graphics mode.  The following error was encountered. You may need to update your  configuration to solve this. (EE) No devices detected."[/SIZE]  [SIZE=1]

 We realize that you all might require further information to further our  cause and more info will be supplied upon request as we didn't want to  over supply data.[/SIZE]  [SIZE=1]

 Thanks so much everyone. Kir_b[/SIZE]

---

### Post by Kir_B on 2010-03-09
[SIZE=1]Thanks to everyone that is looking into our huge problem, you have no idea just how much we appreciate your time.

We're trying to compile a little more information on just what has  gotten us to this point, but to figure out and post everything in the  correct order is going to be impossible, as we've been working on this  for more than a week. We know that waiting this long was not wise, but  life got in the way.

At one point we were given the idea that there was a problem concerning  the XORG file, so we ran some commands on it (copy, backup, Etc.) We're going to include the related files here for you all to  peruse.

[/SIZE][HTML]xorg.conf
**************************************************************************************
Section  "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section  "Screen"
    Identifier    "Default Screen"
    Monitor         "Configured Monitor"
    Device        "Configured Video Device"
     DefaultDepth    24
EndSection

Section "Device"
     Identifier    "Configured Video Device"
    Driver    "nvidia"
EndSection[/HTML][SIZE=1]
[/SIZE][HTML]xorg.conf.failsafe
************************************************************************************
Section  "Device"
    Identifier    "Configured Video Device"
     Driver        "vesa"
EndSection

Section "Monitor"
     Identifier    "Configured Monitor"
EndSection

Section "Screen"
     Identifier    "Default Screen"
    Monitor        "Configured  Monitor"
    Device        "Configured Video Device"
EndSection[/HTML][SIZE=1]

[/SIZE][HTML]Xorg.0.log
***********************************************************************************

X.Org  X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11,  Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current  Operating System: Linux stphill-desktop 2.6.31-14-generic  #48-Ubuntu  SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic   root=UUID=0a4bf2f0-2930-4be4-ad82-7f05330f9ea7 ro quiet splash
Build  Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2  (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to  make sure that you have the latest version.
Markers: (--) probed,  (**) from config file, (==) default setting,
    (++) from command  line, (!!) notice, (II) informational,
    (WW) warning, (EE) error,  (NI) not implemented, (??) unknown.
(==) Log file:  "/var/log/Xorg.0.log", Time: Tue Mar  9 01:48:51 2010
(==) Using  config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the  first Screen section.
(**) |-->Screen "Default Screen" (0)
(**)  |   |-->Monitor "Configured Monitor"
(**) |   |-->Device  "Configured Video Device"
(==) Automatically adding devices
(==)  Automatically enabling devices
(WW) The directory  "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry  deleted from font path.
(==) FontPath set to:
     /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
     /usr/share/fonts/X11/75dpi/:unscaled,
     /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
     /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
     built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II)  Cannot locate a core pointer device.
(II) Cannot locate a core  keyboard device.
(II) The server relies on HAL to provide the list of  input devices.
    If no devices become available, reconfigure HAL  or disable  AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module  ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video  Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server  Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--)  PCI:*(0:0:2:0) 8086:2562:1849:2562 Intel Corporation   82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @   0xd0000000/134217728, 0xdff80000/524288
(WW) Open ACPI failed  (/var/run/acpid.socket) (No such file or  directory)
(II) No APM  support in BIOS or kernel
(II) System resource ranges:
    [0]  -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0     0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000  - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 -  0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff  (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II)  LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II)  Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4,  module version = 1.0.0
    Module class: X.Org Server Extension
     ABI class: X.Org Server Extension, version 2.0
(II) Loading  extension MIT-SCREEN-SAVER
(II) Loading extension  XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II)  Loading extension DPMS
(II) Loading extension XVideo
(II) Loading  extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II)  LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II)  Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module  version = 1.0.0
    Module class: X.Org Server Extension
    ABI  class: X.Org Server Extension, version 2.0
(II) Loading extension  DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading  /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx:  vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version =  1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX  Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009
(II) Loading  extension GLX
(II) LoadModule: "record"
(II) Loading  /usr/lib/xorg/modules/extensions//librecord.so
(II) Module  record: vendor="X.Org Foundation"
    compiled for 1.6.4, module  version = 1.13.0
    Module class: X.Org Server Extension
    ABI  class: X.Org Server Extension, version 2.0
(II) Loading extension  RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II)  Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module  version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II)  Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II)  Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module  dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module  version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II)  Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading  /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia:  vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version =  1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X  Driver  173.14.20  Thu Jun 25 19:28:52 PDT 2009
(II) NVIDIA Unified  Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI  00@00:02:0
(EE) No devices detected.

Fatal server error:
no  screens found

Please consult the The X.Org Foundation support 
      at http://wiki.x.org
 for  help. 
Please also check the log file at "/var/log/Xorg.0.log" for  additional  information.

 ddxSigGiveUp: Closing log[/HTML]I hope this information helps, at least a little bit. Oh and we do have the use of a Ubuntu livecd, just in case that helps our cause in some small way.

Thanks again everyone. Kirby.

---

