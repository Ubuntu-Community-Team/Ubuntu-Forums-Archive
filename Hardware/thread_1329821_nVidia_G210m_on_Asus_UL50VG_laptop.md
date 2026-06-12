---
title: "nVidia G210m on Asus UL50VG laptop"
date: 2009-11-17
forum: Hardware
---

### Post by azerty88 on 2009-11-17
Hi!
I am having some serious problem with nVidia G210m graphics card.
My laptop has two GC's. By default ubuntu 9.10 uses integrated intel's GC but i would like to use G210m instead. I've installed nvidia drivers and tried many possible configurations for X server but i still can't make it work.

I hope someone can help me.

here is my xorg.conf
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:1:0:0" 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

and here is what i get from lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
03:00.0 Network controller: Intel Corporation WiFi Link 100 Series
04:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

```

---

### Post by blackened07 on 2009-11-18
Well I do have the same problem, I tried adding to the /etc/apt/sources.list, also installing from the nvidia webpage, and from hardware drives, and all i can get is a black screen after reboot, I already posted sth related to the problem but seems I'm running out of luck, since nobody ask back, what a shame I can't get to work my ubuntu properly...

Maybe if you could tell me what you have tried might be useful, ir might help to keep looking for info, since I can't find too many on the net, hope that helps a bit, think we have the same issue.

Greetings

---

### Post by azerty88 on 2009-11-18
I've tried solution found here
[http://www.nvnews.net/vbulletin/showthread.php?t=140482]("http://www.nvnews.net/vbulletin/showthread.php?t=140482")

and I also used different drivers. Curently I'm trying nvidia's newest CUDA driver but no improvement.

Here is Xorg.0.log
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=16dfb73b-7776-4db9-9fb8-c1fc7d927e80 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 18 09:52:02 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:1043:1af2 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xfcc00000/4194304, 0xd0000000/268435456, I/O @ 0x0000cc00/8
(--) PCI: (0:1:0:0) 10de:0a74:1043:1af2 nVidia Corporation rev 162, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.18  Wed Jul 22 19:06:03 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.18  Wed Jul 22 18:37:18 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:02:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Nov 18 09:52:03 NVIDIA(0): Enabling RENDER acceleration
(II) Nov 18 09:52:03 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Nov 18 09:52:03 NVIDIA(0):     enabled.
(EE) Nov 18 09:52:03 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) Nov 18 09:52:03 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Nov 18 09:52:03 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Nov 18 09:52:03 NVIDIA(0):     README for additional information.
(EE) Nov 18 09:52:03 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

and output from dmesg
```

[ 1505.802480] NVRM: failed to copy vbios to system memory.
[ 1505.802779] NVRM: RmInitAdapter failed! (0x30:0xffffffff:899)
[ 1505.802786] NVRM: rm_init_adapter(0) failed

```

---

### Post by blackened07 on 2009-11-18
hi, thanks for asking me back, I just checked the link you gave me, and 
It Worked For Me ! 

I have the sony VPCCW17FX, and I have the nvidia Geforce G210M and 

I did exactly what egghead3 says, don't know if the model is the issue, but it worked for me, Thanks again, sorry I can't be any help for you, but the problem it's the screen, well the bug that comes with the nvidia drivers.

Did you try exactly what egghead3 says?, I'm still thinking you should give it another try :) 
by the way I installed the driver from the nvidia Webpage
Greetings

---

### Post by azerty88 on 2009-11-18
Heh, I'm glad I could help you ;)
unfortunately this solution doesn't work for me.
I believe this is a bigger problem.
After installation of CUDA driver and successful compilation of example CUDA programs. I tried to start one of them and i got message that it couldn't find a CUDA compatible device. So even if my xorg.conf is good it just won't work.

---

### Post by blackened07 on 2009-11-19
have you tried with the "nv" drivers?

---

### Post by azerty88 on 2009-11-19
yes. even vesa driver doesn't work :/

---

### Post by blackened07 on 2009-11-19
Well it's too strange because I had the 'nv' drivers and at least I had Graphics without 3d aceleration, I could watch videos, flash animations and everything else but videogames and compiz.

It's very strange, maybe posting in an nvidia forum may help, don't know.

Greetings.

---

### Post by budhe888 on 2009-11-20
I am having the same problem with the G210M on my Toshiba laptop.  Both the 185 and 190 drivers cause my system to crash, however my behavior is a bit different.

I am able to get to the Ubuntu splash screen, but then soon after I get some discolored pixels and the system freezes.  There must be more of us out there who have had this same problem.  I didn't try the suggestion in the link above because his problem was about not even starting the monitor, but that is definitely not my issue.

---

### Post by blackened07 on 2009-11-20
that's right, that bug is when the nvidia logo must appear right before the login screen should appear, the screen goes totally black.

---

### Post by lanuser on 2009-12-13
[FONT=&quot]This about [/FONT]  [FONT=&quot]Asus' UL80Vt (some type of hardware)[/FONT]
[FONT=&quot]CULV processors are typically paired with Intel's _GS45 Express chipset, whose integrated Graphics Media Accelerator X4500MHD offers abysmal gaming performance and spotty compatibility_. Fortunately, the _chipset has 16 lanes of second-generation PCI Express connectivity_, which the UL80Vt _links to a GeForce G210M discrete graphics processor. _[/FONT]    Toggling between the GeForce G210M and GMA X4500MHD is as easy as switching between power plans, which can be done with the touch of a button located above the keyboard. The process isn't entirely seamless; the screen goes blank for a few seconds when you switch graphics modes. ([http://techreport.com/articles.x/17939](http://techreport.com/articles.x/17939)) I want to use linux or XP, but so can't enable G210, driver show me that the display is not connected to G210. May be we need to use some special util to swith GPUs.

---

### Post by avilella on 2009-12-14
This has happened before: the sony vaio z-series laptops also have had troubles informing the BIOS to switch on/off the discrete graphics card.
For the z-series, the solution was to dump and inspect the DSDT table, then call the appropriate method to switch on/off the card from the BIOS.

Unfortunately nobody has produced DSDT table dump yet, but it's very easy to do:

Please attach your DSDT information to this Launchpad bug report specifying your laptop model:

[https://bugs.launchpad.net/bugs/312756](https://bugs.launchpad.net/bugs/312756)

To compile your DSDT information, install if you haven't already the acpidump and iasl tools:
sudo apt-get install acpidump iasl           # on Debian-based systems

Then run the following commands:

sudo acpidump > acpidump.txt
sudo acpixtract acpidump.txt
iasl -d DSDT.dat

This will create a DSDT.dsl file that you can attach to the bug report. This information will allow the developers to fully implement the hybrid graphics features for Linux.

Thanks!


> **lanuser said:**
> [FONT=&quot]This about [/FONT]  [FONT=&quot]Asus' UL80Vt (some type of hardware)[/FONT]
[FONT=&quot]CULV processors are typically paired with Intel's _GS45 Express chipset, whose integrated Graphics Media Accelerator X4500MHD offers abysmal gaming performance and spotty compatibility_. Fortunately, the _chipset has 16 lanes of second-generation PCI Express connectivity_, which the UL80Vt _links to a GeForce G210M discrete graphics processor. _[/FONT]    Toggling between the GeForce G210M and GMA X4500MHD is as easy as switching between power plans, which can be done with the touch of a button located above the keyboard. The process isn't entirely seamless; the screen goes blank for a few seconds when you switch graphics modes. ([http://techreport.com/articles.x/17939](http://techreport.com/articles.x/17939)) I want to use linux or XP, but so can't enable G210, driver show me that the display is not connected to G210. May be we need to use some special util to swith GPUs.

---

