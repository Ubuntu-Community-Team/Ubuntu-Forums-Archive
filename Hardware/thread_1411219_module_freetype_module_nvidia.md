---
title: "module freetype module nvidia"
date: 2010-02-19
forum: Hardware
---

### Post by poloMontreal on 2010-02-19
I start by saying a really a beginner in ubuntu, I was triying to config my desktop, I exicut this commande
 'sudo nvidia-xconfig --add-argb-glx-visuals -d 24'
I saw some warning... after I restart the trouble begane 'no module freetype, no module nvidia, no driver' and my laptop start to run on low graphic mode

you can see my Xorg.0.log

******************************

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux abdenour-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: root=UUID=fa3f5796-1384-4562-863e-3f8ea72033a7 ro quiet splash 
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 19 16:07:31 2010
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
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:27a2:1025:0107 Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd0100000/524288, 0xb0000000/268435456, 0xd0200000/262144, I/O @ 0x00001800/8
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
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
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
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
 
**********************************

any idea to fix it ?

---

### Post by poloMontreal on 2010-02-19
this is my xorg.conf

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "False"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by lidex on 2010-02-19
Looks like you have intel graphics not nvidia.
Run this command in a terminal:
```
sudo mv /etc/X11/xorg.conf xorg_conf.old 
```

[SIZE="5"]**Reboot**[/SIZE]

---

### Post by poloMontreal on 2010-02-19
thats workkkkkkkkk , thankssssssssssssssssssssssssss , really thank you =;

---

### Post by poloMontreal on 2010-02-19
please take at the attached picture
my laptop is working, but now I can change the king of resolution, only low quality, when I tried it's start to look for "driver" after refuse to make a resolution change

any idea ?
should I remove nvidia ?

---

### Post by lidex on 2010-02-19
Yes, remove nvidia.

Then try this command;
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

Have a look at this page as well:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")

---

### Post by poloMontreal on 2010-02-19
witch one ?  I have 3 packages 
1 nvidia browser X
2 driver nvidia X.org
3 EnvyNG

---

### Post by lidex on 2010-02-19
Do me a favor and post the output of this command:
```
lspci -nn | grep VGA
```

---

### Post by poloMontreal on 2010-02-19
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
 

I just remove nvidia with ' sudo envyng -t' 
reboot
after I use 'sudo dpkg-reconfigure -phigh xserver-xorg '

but nothing new

---

### Post by lidex on 2010-02-19
Don't use envy again and you can remove any nvidia packages. Try this:
```
sudo nvidia-settings --uninstall
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

Oh yeah, reboot!

---

### Post by poloMontreal on 2010-02-20
when I use 'sudo nvidia-settings --uninstall
 I have this response
nvidia-settings: unrecognized option: "--uninstall"

ERROR: Invalid commandline, please run `nvidia-settings --help` for usage
       information.

---

### Post by lidex on 2010-02-20
Yeah, I was wondering about that command. Try this:
```
sudo apt-get remove nvidia-settings
``` 
The other commands work OK?

---

### Post by poloMontreal on 2010-02-20
yes all instruction are working, but I still have a same problem, screen an unknown at 0HZ and I cant make change, only low screen resolution, because he search for 'driver' after the screen turn dark for few second

I post a picture for my screen

---

### Post by lidex on 2010-02-20
OK. Next go here:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")
and add the repository per the instructions.

---

### Post by poloMontreal on 2010-02-20
and I remember have seen my screen at 65hz or 55hz (I'm not sure) this morning before executing the command

---

### Post by poloMontreal on 2010-02-20
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) **jaunty** maindeb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) **jaunty** main

I'm on ubuntu 9.10 Karmic
I remove jaunty and put karmic ??

---

### Post by poloMontreal on 2010-02-20
I replay fast with out reading all the webpage, ok I get it, there is a section with karmic, I followed all instruction, and update my softwear  and reboot, but nothing happend still a same thing, screen low resolution, unknown, and at 0hz

---

### Post by lidex on 2010-02-20
OK. Now click on compiz-check in my signature. On that web page you will find instructions for downloading and running that script. It should give us an idea why effects cannot be enabled. Hang in there :P

---

### Post by lidex on 2010-02-20
Once you've posted the output of that script re-run the previous command:
```
sudo mv /etc/X11/xorg.conf xorg_conf.old 
```
Allow it to overwrite if prompted. Now reboot and when your desktop comes back up run this command and post results:
```
cat /etc/X11/xorg.conf
```

---

### Post by poloMontreal on 2010-02-21
/etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: no comand found


./compiz-check


Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

its workinggggggggg thank you so match

---

### Post by poloMontreal on 2010-02-21
:-(  very new thing happen, my laptop reboot 2 times, and ask me to relog, it's never never happen before, a first time when I click in my desk, a second time when I click in url link

---

### Post by poloMontreal on 2010-02-22
in one day it happen 9time, its not a total reboot, its log out and ask me to relog

---

### Post by poloMontreal on 2010-02-23
help me please

---

### Post by poloMontreal on 2010-02-23
in my user.log I have this
Feb 23 17:14:11 abdenour-laptop pulseaudio[4335]: pid.c: Stale PID file, overwriting.
Feb 23 17:14:14 abdenour-laptop pulseaudio[4335]: module-x11-xsmp.c: X11 session manager not running.
Feb 23 17:14:14 abdenour-laptop pulseaudio[4335]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by lidex on 2010-02-23
Run these commands from the terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot when complete.

---

### Post by lidex on 2010-02-23
> **poloMontreal said:**
> in my user.log I have this
Feb 23 17:14:11 abdenour-laptop pulseaudio[4335]: pid.c: Stale PID file, overwriting.
Feb 23 17:14:14 abdenour-laptop pulseaudio[4335]: module-x11-xsmp.c: X11 session manager not running.
Feb 23 17:14:14 abdenour-laptop pulseaudio[4335]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

Do you have any third-party repositories enabled, especially for pulseaudio?

---

### Post by poloMontreal on 2010-02-23
my audio work well 
I have this in my user.log


Feb 23 20:27:39 abdenour-laptop pulseaudio[3168]: pid.c: Stale PID file, overwriting.
Feb 23 20:27:42 abdenour-laptop pulseaudio[3168]: module-x11-xsmp.c: X11 session manager not running.
Feb 23 20:27:42 abdenour-laptop pulseaudio[3168]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 23 20:36:33 abdenour-laptop bonobo-activation-server (abdenour-3727): could not associate with desktop session: Failed to connect to socket /tmp/dbus-nDSaM85COv: Connexion refusée

---

### Post by poloMontreal on 2010-02-23
I execute all command but it happen again

Feb 23 21:04:47 abdenour-laptop bonobo-activation-server (abdenour-2281): could not associate with desktop session: Failed to connect to socket /tmp/dbus-CixINwOfKA: Connexion refusée
Feb 23 21:05:21 abdenour-laptop pulseaudio[2372]: pid.c: Stale PID file, overwriting.
Feb 23 21:05:24 abdenour-laptop pulseaudio[2372]: module-x11-xsmp.c: X11 session manager not running.
Feb 23 21:05:24 abdenour-laptop pulseaudio[2372]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by lidex on 2010-02-23
Check your ~/.dbus directory. If it, or any files/folders in it are owned by root, change permissions back to you.

---

### Post by poloMontreal on 2010-02-23
No, all files are mine 

[email]abdenour@abdenour-laptop:~/.dbus[/email]$ ls -al
total 12
drwx------  3 abdenour abdenour 4096 2010-02-18 00:44 .
drwxr-xr-x 70 abdenour abdenour 4096 2010-02-23 22:16 ..
drwx------  2 abdenour abdenour 4096 2010-02-19 03:31 session-bus

---

### Post by lidex on 2010-02-23
> **poloMontreal said:**
> No, all files are mine 

[email]abdenour@abdenour-laptop:~/.dbus[/email]$ ls -al
total 12
drwx------  3 abdenour abdenour 4096 2010-02-18 00:44 .
drwxr-xr-x 70 abdenour abdenour 4096 2010-02-23 22:16 ..
drwx------  2 abdenour abdenour 4096 2010-02-19 03:31 session-bus

I don't think that's showing the contents of ~/.dbus/session-bus

---

### Post by poloMontreal on 2010-02-23
[email]abdenour@abdenour-laptop:~/.dbus[/email]/session-bus$ ls -al
total 16
drwx------ 2 abdenour abdenour 4096 2010-02-19 03:31 .
drwx------ 3 abdenour abdenour 4096 2010-02-18 00:44 ..
-rw-r--r-- 1 abdenour abdenour  464 2010-02-23 22:58 9da7445eee2dcb69d0758b004b7c18bd-0
-rw-r--r-- 1 abdenour abdenour  464 2010-02-23 19:12 9da7445eee2dcb69d0758b004b7c18bd-1

---

### Post by poloMontreal on 2010-02-24
[email]essai@abdenour-laptop:~/.dbus[/email]/session-bus$ ls -al
total 24
drwx------ 2 essai essai 4096 2010-02-23 19:37 .
drwx------ 3 essai essai 4096 2010-02-22 00:15 ..
-rwxr-xr-x 1 essai essai  464 2010-02-24 22:57 9da7445eee2dcb69d0758b004b7c18bd-0
-rwxr-xr-x 1 essai essai  464 2010-02-24 23:11 9da7445eee2dcb69d0758b004b7c18bd-1
-rwxr-xr-x 1 essai essai  464 2010-02-23 19:35 9da7445eee2dcb69d0758b004b7c18bd-2
-rwxr-xr-x 1 essai essai  463 2010-02-23 19:37 9da7445eee2dcb69d0758b004b7c18bd-3

---

