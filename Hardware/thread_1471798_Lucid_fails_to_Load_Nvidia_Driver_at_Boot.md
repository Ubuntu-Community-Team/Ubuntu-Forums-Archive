---
title: "Lucid fails to Load Nvidia Driver at Boot"
date: 2010-05-03
forum: Hardware
---

### Post by linuxyogi on 2010-05-03
Hi. 

 I am using NVIDIA proprietary driver for my onboard Nvidia 7025 GPU.

The problem is sometimes while booting Lucid fails to load the Nvidia driver. A dialog box appears saying "Ubuntu is running in low graphics mode". Available options includes restart x, run in low graphics mode, exit to console login.

What I do usually is restart the PC & the system boots normally.

I installed Lucid during its developmental stage but I haven't missed any updates. 

I thought because it was an beta release these things are expected and will go away as all the updates are installed but the matter of worry is this problem is persisting.


Note: Karmic was running fine with the Nvidia proprietary driver installed. 

Please help.

---

### Post by causeitsme on 2010-05-13
Same here. Anyone know what's going on?

---

### Post by rowanseymour on 2010-05-14
[SIZE=2]Me too - Dell XPS Studio 13 with nVidia [/SIZE][SIZE=2]9500M

Using Lucid 10.04 AMD64 - never had a problem with Karmic AMD64

Seems to happen about half of the times I boot[/SIZE]

---

### Post by K1mp3 on 2010-05-16
I did an upgrade to 10.04, initially everything worked but yesterday there was an update (a long list of packages got updated, I suppose nVidia drivers being one of them) and now the nVidia-kernel driver fails to load for me as well... not very satisfied with 10.04 as with 9.10 everything was working fine, wish I could downgrade

my HW is nVidia Geforce 8800

---

### Post by K1mp3 on 2010-05-22
After a few days of investigations I realised that the upgrade to 10.04 had failed to update my grub menu so I was loading the old Kernel version. Had to change from kernel 2.6.31-17-generic to kernel 2.6.32-21-generic in (/boot/grub/menu.lst) and now nVidia driver loads and works just fine.

---

### Post by Don_Shifty on 2010-05-22
same problem for me!
couldn't get the driver working... i'm on grub 2 though, so its not a grub problem...
any ideas?

---

### Post by linuxyogi on 2010-05-24
The problem hasn't occurred at my end for quite some time now.

I guess the NVIDIA driver & kernel update fixed it.

My kernel version is 2.6.32-22-generic.

Still, I am not 100% sure that its fixed.

Anyone who's updates are pending can update their system & see if it fixes the problem.

:P

---

### Post by dino99 on 2010-05-24
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by linuxyogi on 2010-05-27
> **linuxyogi said:**
> The problem hasn't occurred at my end for quite some time now.

I guess the NVIDIA driver & kernel update fixed it.

My kernel version is 2.6.32-22-generic.

Still, I am not 100% sure that its fixed.

Anyone who's updates are pending can update their system & see if it fixes the problem.

:P
SORRY I was wrong.

The driver failed to load again, today.

But, one thing I must mention & that is the number of times this problem is occurring is significantly lower in comparison to the previous version of the driver/kernel.

Sorry again.

The problem exists.

---

### Post by serprex on 2010-06-03
Had the issue yesterday. apt-get updated linux headers to 2.6.32-22, happened again after restart. I downloaded my 195.36.24 driver off of Nvidia's site

I'm on a 64bit desktop system from system76, packaged with an ION GPU

---

### Post by randyklein99 on 2010-06-03
I'm having the same problem.

---

### Post by serprex on 2010-06-05
randy: Are you on a 64bit system?

The following is /var/log/Xorg.0.log after a subsequent failure

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux demur 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=d234266d-b9ec-4e2d-b2d7-799577baa99a ro ipv6.disabled=1
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  5 11:30:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "BlankTime" "0"
(**) Option "StandbyTime" "0"
(**) Option "SuspendTime" "0"
(**) Option "OffTime" "0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:0:3:5) 10de:0aa3:19da:a108 nVidia Corporation MCP79 Co-processor rev 177, Mem @ 0xfae80000/524288
(--) PCI:*(0:3:0:0) 10de:087d:19da:a108 nVidia Corporation ION VGA rev 177, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

Where Xorg.conf is

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "0"
EndSection

Section "ServerFlags"
    Option          "BlankTime"     "0"
    Option          "StandbyTime"   "0"
    Option          "SuspendTime"   "0"
    Option          "OffTime"       "0"
EndSection

Section "Files"
    ModulePath      "/usr/lib/xorg/modules"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "built-ins"
EndSection

Section "Module"
    Load           "extmod"
    Load           "record"
    Load           "dbe"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "LCD-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "ION VGA"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "LCD-0"
    Option         "metamodes" "1152x864 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by randyklein99 on 2010-06-05
I am 64 bit, but I seemed to have fixed the problem.  Although I'm not sure I could retrace my steps as to what I did.  But essentially, I removed the proprietary driver installed through jockey, and then installed nvidia-current instead.

---

### Post by olegsmall on 2010-06-09
I had exact same problem.
video card nvidia geforce go 6100, ubuntu 10.04 x64, nvidia-current driver installed.
How I fix:
**sudo gedit /etc/modprobe.d/blacklist.conf**

At the end of this file, paste the following:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]

method is taken from this thread
[http://ubuntuforums.org/showthread.php?t=1466150&page=5](http://ubuntuforums.org/showthread.php?t=1466150&page=5)


Now I have another issue that I described it in this thread
[http://ubuntuforums.org/showthread.php?t=1505437](http://ubuntuforums.org/showthread.php?t=1505437)

---

### Post by rowanseymour on 2010-07-06
Latest 2.6.32-23 kernel, latest nvidia-current... still same problem

---

### Post by linuxyogi on 2010-07-11
> **olegsmall said:**
> 
At the end of this file, paste the following:
[B]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv[/B]



It worked. Thanks

---

