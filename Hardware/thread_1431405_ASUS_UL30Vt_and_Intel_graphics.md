---
title: "ASUS UL30Vt and Intel graphics"
date: 2010-03-16
forum: Hardware
---

### Post by prebenh on 2010-03-16
Hi

I've tried getting the nvidia driver working for my laptop with both a G210M nvidia graphics card and the intel (Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) graphics card.

Since nvidia doesn't support the G210M i've decided to try to get the intel driver working. So far no luck and I have no OpenGL functionality in X.

My Xorg.conf looks like this:
```
Section "Device"
    Identifier          "Device0"
    Driver              "i915"
    VendorName          "Intel"
    BusID               "PCI:0:2:0"
    Option              "ConnectedMonitor"      "DFP-0"
    Option              "CustomEDID"            "DFP-0:/etc/X11/edid.bin"
EndSection

```The output of the lspci -v | grep VGA is:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)

```The Xorg.1.log file:
```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux UL30VT 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-20-generic root=UUID=64d56229-e824-41bc-ad70-8162335be6f3 ro quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Mar 16 20:04:44 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
(**) |   |-->Device "Device0"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
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
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
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
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
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
(II) LoadModule: "i915"
(WW) Warning, couldn't open module i915
(II) UnloadModule: "i915"
(EE) Failed to load module "i915" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

```and to be sure that the driver works, I just used locate:
```

preben@UL30VT:~$ locate i915
/lib/modules/2.6.31-14-generic/kernel/drivers/gpu/drm/i915
/lib/modules/2.6.31-14-generic/kernel/drivers/gpu/drm/i915/i915.ko
/lib/modules/2.6.31-19-generic/kernel/drivers/gpu/drm/i915
/lib/modules/2.6.31-19-generic/kernel/drivers/gpu/drm/i915/i915.ko
/lib/modules/2.6.31-20-generic/kernel/drivers/gpu/drm/i915
/lib/modules/2.6.31-20-generic/kernel/drivers/gpu/drm/i915/i915.ko
/usr/include/drm/i915_drm.h
/usr/lib/dri/i915_dri.so
/usr/lib32/dri/i915_dri.so
/usr/src/linux-headers-2.6.31-14/drivers/gpu/drm/i915
/usr/src/linux-headers-2.6.31-14/drivers/gpu/drm/i915/Makefile
/usr/src/linux-headers-2.6.31-14/include/drm/i915_drm.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/drm/i915
/usr/src/linux-headers-2.6.31-14-generic/include/config/drm/i915.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/drm/i915/kms.h
/usr/src/linux-headers-2.6.31-19/drivers/gpu/drm/i915
/usr/src/linux-headers-2.6.31-19/drivers/gpu/drm/i915/Makefile
/usr/src/linux-headers-2.6.31-19/include/drm/i915_drm.h
/usr/src/linux-headers-2.6.31-19-generic/include/config/drm/i915
/usr/src/linux-headers-2.6.31-19-generic/include/config/drm/i915.h
/usr/src/linux-headers-2.6.31-19-generic/include/config/drm/i915/kms.h
/usr/src/linux-headers-2.6.31-20/drivers/gpu/drm/i915
/usr/src/linux-headers-2.6.31-20/drivers/gpu/drm/i915/Makefile
/usr/src/linux-headers-2.6.31-20/include/drm/i915_drm.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/drm/i915
/usr/src/linux-headers-2.6.31-20-generic/include/config/drm/i915.h
/usr/src/linux-headers-2.6.31-20-generic/include/config/drm/i915/kms.h
preben@UL30VT:~$

```
I've attached all the Xorg.*.log files for convenience.

Hope someone can help. I just get a black screen with two small lines in the top of the screen. Have to press the power button for 5 seconds to kill and reboot in safe mode.


Best regards,
Preben

---

### Post by dakilla on 2010-03-17
try: 
Driver "intel" 

in xorg.conf

for Nvidia:
got the same error. if you upgrade to 10.04, you get an blank screen without the two white/gray lines. 

i have to say as every one else does..
"

Solution? SEND BUG REPORTS TO NVIDIA.

From Nvidia's web site:
To submit Linux bug reports please email (In English only) [email]linux-bugs@nvidia.com[/email] or [email]linux-nforce-bugs@nvidia.com[/email] please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh".

"

i think you can hax it if you run a distro who still uses xorg.conf
there are a thread on nvidia forums where they extract a edid file from windows and uses it in linux. they have got the g210m card to work that way, but i am not sure they had ul30vt laptops, or even hybrid graphics.

---

### Post by prebenh on 2010-03-18
As you can see - I already tried to extract the edid using the suggested windows software. And it doesn't work. My point is, that something is completely wrong since: the integrated Intel graphics card doesn't work and the nvidia doesn't work either.

I don't think it has anything to do with the nvidia card - it is the same with the intel card. No matter what I do it helps. I need OpenGL support on the computer. Intel graphics is fine even though it doesn't perform as well as the nvidia!


- Preben

---

### Post by dakilla on 2010-04-25
i got some opengl accel on my intel card with mesa. try to install ubuntu 10.04, it works fine for me, still looking for a way to get my nvidia-card to work...

---

### Post by dakilla on 2010-05-02
ok this is so dame simple, have been locking for a solution for months.

this is how you get g210m to work on ubuntu 9.10 / 10.04. 

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

Anyone more then me who want to hit the people who wrote the bios? 
running the latest bios. ends with 10.

---

### Post by sebulator on 2010-05-10
Is it possible to have this solution in combination with the one where the nVidia card is disabled by loading a kernel module? So that I can start my computer and "choose" (through BIOS) which graphic card to use.

---

### Post by karl3 on 2010-05-18
thnx, i got nvidia running with these instructions :))) 

but i can't find the way to switch back to intel graphics when i need longer battery life.

---

### Post by veloek on 2010-05-20
> **karl3 said:**
> thnx, i got nvidia running with these instructions :))) 

but i can't find the way to switch back to intel graphics when i need longer battery life.

I have the same problem. It seems like the Intel graphic card is deactivated when you select compatible in the SATA section in the bios, and that explains why it fixes the problem in Ubuntu, since it strips down Ubuntu's choise of grafic card to only one.

In my case it kinda sucks tho, because I dual-boot Ubuntu and Windows, and I like the opportunity to make the graphic switch in Windows to save battery life, but it's to much of a hassel to go through the bios everytime I want to switch OS.

Can't wait till the option to switch between graphic cards in Ubuntu becomes available.

---

### Post by Vermind on 2010-07-23
I have an ASUS UL30Vt with Ubuntu 10.04 64-bit.
I can get nvidia to work with the bios hack.
I'd like to get 3d accel for the intel card,
without the bios hack. Has anyone done that?
I have 2d desktop with the intel card with a blank xorg.conf.
Even when I specify I want the intel driver in the xorg.conf,
I get
```
Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```
in Xorg.0.log. I wonder why it tries to find an nvidia driver?

---

