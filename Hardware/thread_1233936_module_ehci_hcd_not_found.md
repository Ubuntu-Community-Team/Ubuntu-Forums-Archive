---
title: "module ehci_hcd not found"
date: 2009-08-07
forum: Hardware
---

### Post by jomex on 2009-08-07
my usb drive is terrible slow (1MB/sec)
some other posts advice to:
sudo modprobe ehci_hcd
but it says
FATAL: Module ehci_hcd not found.

Ubuntu 9.04 Alt. AMD64

---

### Post by jomex on 2009-08-07
usb filesystem is NTFS

[quote="lsusb"]
Bus 002 Device 005: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/quote]

[quote="lsmod|grep usb"]
usb_storage           115392  1 
usbhid                 47040  0 
[/quote]

---

### Post by fennec_fox on 2009-08-07
[http://ubuntuforums.org/archive/index.php/t-968547.html](http://ubuntuforums.org/archive/index.php/t-968547.html)

[http://www.linuxquestions.org/questions/linux-software-2/fatal-no-usb-module-found-183225/](http://www.linuxquestions.org/questions/linux-software-2/fatal-no-usb-module-found-183225/)

Seems like a kernel upgrade will fix it. Are you using 9.04 or an older version? Either way, you can just upgrade the kernel to a newer version and it will probably work. I was just curious if it was the out of the box 9.04 kernel.

---

### Post by jomex on 2009-08-07
Ubuntu 9.04 Alt. AMD64

uname -a
> 2.6.28-14-generic

newest kernel corresponding to kernel.org
> 2.6.30.4

apt-get and synaptic won't update


i just set the SATA RAID configuration in BIOS from AHCI to IDE and the rate is now 3MB/sec though they shouldn't be connected o_O

---

### Post by fennec_fox on 2009-08-07
That's kind of what I was afraid of. I was hoping you'd have 8.04 or 8.10 with an older kernel you could just update. I'm not sure how well the newest kernel works with 9.04. It's available but, I've heard there are graphic driver problems with the newest. 

An upgrade would probably solve your problem but, it might cause another like graphics driver problems. 

Ubuntu has compiled kernels here including the newest but, I'm not sure it's something you want to do.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm not too familiar with this and don't have a system I can test on right now so I can't test it for you. 

Hopefully someone more ubuntu oriented could help with that.

---

### Post by jomex on 2009-08-07
hmm, someone more Ubuntu oriented?

*BUMP*
>_<

---

### Post by fennec_fox on 2009-08-07
Sorry if that wasn't helpful. I'm just not sure how to fix it without a kernel update. I mean you can try going back to 8.10. That would probably take care of it. Unfortunately, this isn't a problem I am familiar with. I mean you can try compiling your own kernel but, I don't know if that would do anything.

Sorry!

---

### Post by jomex on 2009-08-10
kernel update works (2.6.30.4), USB is now 10-20MB/sec
nvidia drivers are not working. installed version is 180, current stable is 185. how do i convince the update manager about that?

*oh Ubuntu, why are you testing me?*

---

### Post by fennec_fox on 2009-08-10
I'm not on a ubuntu system at the moment because I am out of town but, does it list options of which driver to install in the restricted driver manager? I recall on 8.10 several nvidia drivers are listed for restricted hardware drivers and I can choose which to install. 

If you have several options you should be able to choose a different one. You might be able to choose 185 and the update manager will run with it. It's possible that 180 is enabled in there and the update manager won't update because it's specified as 180 in there.

---

### Post by jomex on 2009-08-10
in "Hardware Drivers" (formerly "restricted driver manager" i think) i have 3 options: 180, 173, 96
clicking "activate" on any of them doesn't work

---

### Post by jomex on 2009-08-11
argl. when i booted my computer today i got a 800x600 resolution :confused:
how can i turn it back, even without 3d acceleration

---

### Post by fennec_fox on 2009-08-11
I would get the nvidia settings program from add/remove or synaptic. If the drivers won't activate you can try installing the ones from the nvidia site. Then you can probably use nvidia settings under - system - administration and tweak your graphics to what you want. I am only guessing though because I can't test that. That's what I did a few releases back when I had some graphics issues and it worked out. I wouldn't get your hopes up too much doing it that way.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) 


If that doesn't help you can try to get envy from add/remove or synaptic. Envy finds the right driver, installs it and configures X for you.

---

### Post by jomex on 2009-08-11
sudo apt-get install envyng-qt

vboxdrv cannot compile, kernel headers missing
envyng cannot use 180-44 driver, kernel headers missing

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.4/linux-headers-2.6.30-02063004-generic_2.6.30-02063004_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.4/linux-headers-2.6.30-02063004-generic_2.6.30-02063004_amd64.deb")

install

Error: Dependency is not satisfiable: linux-headers-2.6.30-02063004

---

### Post by fennec_fox on 2009-08-12
Did you try installing the nvidia drivers from their site? If you download the one from the site that might work. 

To run it you'll have to 

1. logout
2. hit ctrl alt f3
3. login 
4. type 'sudo killall gdm'
5. cd to the directory the nvidia installer is in. If you put it in your home directory you won't have to cd anywhere.
6. type 'sudo sh NVIDIA........'    The '........' will vary on what driver you get. After you type NVIDIA in caps you can just hit tab and it should finish the typing for you. 
7. Go through the install and you'll get the option to download a working kernel module or build one. If one doesn't work, try the other.
8. when it's installed, type 'startx' and login.

That might work. It's fairly easy. Let me know any problems that come up.

---

### Post by jomex on 2009-08-17
okay, found some spare time to tackle that problem again...

> sudo sh NVIDIA...

in console mode using the newest kernel gives me

"The CC version check failed... need gcc 4.2, have gcc 4.3"
=> ignore

"ERROR: unable to find the kernel source tree for the currently running kernel... --kernel-source-path me not be set correctly"

i accidentally built the NVIDIA drivers using the old kernel version 2.6.28.15 first, which used to have working graphics and now they configuration isn't working anymore. when gnome is starting i get the "Ubuntu is running low-graphics mode" window with several options which are all broke.

QUESTIONS:
1) how to i set the default option in grub back to 2.6.28.15? KGRUBeditor doesn't show up.
2) how to i set the graphics configuration and drivers back to the old version? the NVIDIA installer stated that it created a backup configuration. "Hardware Drivers" states that activated driver is 180, the one i built however is 185.
3) how do i install the kernel headers for the newest kernel so i can use envy? i get: "Error: Dependency is not satisfiable: linux-headers-2.6.30-0206300"
4) how do i set the --kernel-source-path so i can use the nvidia-installer?

> **"/var/log/nvidia-installer.log with NEW kernel"]
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Aug 17 10:58:35 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 185.18.31.
-> There appears to already be a driver installed on your system (version: 185.
   18.31).  As part of installing this driver (version: 185.18.31), the existin
   g driver will be uninstalled.  Are you sure you want to continue? ('no' will
   abort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel said:**
> ftp://download.nvidia.com)?[/URL] (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").


[quote="/var/log/Xorg.0.log"]
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux comp4 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 17 10:51:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI: (0@0:18:0) nVidia Corporation GeForce 7050 PV / nForce 630a rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(--) PCI:*(0@2:0:0) nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xe8000000/67108864, 0xe0000000/134217728, 0xee000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.31  Tue Jul 28 19:34:01 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
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
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.31  Tue Jul 28 18:13:23 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
[/quote]

---

### Post by jomex on 2009-08-19
following this how-to:
[http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+kernel+185](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+kernel+185)
i got the drivers running on 2.6.28-15 again

USB 2.0 is still working though the rate is constantly dropping from 18 MB/sec down to 300 KB/sec (NTFS)

KGRUBEditor starts with gksudo

---

