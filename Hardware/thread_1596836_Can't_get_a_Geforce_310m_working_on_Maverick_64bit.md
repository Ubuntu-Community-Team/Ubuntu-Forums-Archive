---
title: "Can't get a Geforce 310m working on Maverick 64bit"
date: 2010-10-14
forum: Hardware
---

### Post by changomuc on 2010-10-14
Hi there!

first of all, excuse me for my bad english! :)

I really hope you can help me getting the GPU on my notebook up and running, I have no idea what I should try at this point. The notebook is an Asus P42Jc, the GPU is a Nvidia GeForce 310 (Optimus), the System running is Ubuntu 10.10 64 bit.

What I've already done:
I installed the propietary driver (nvidia-current, it says version 260.19.06
I removed the nouveau driver (and blacklisted it)
I did the "sudo nvidia-xconfig", the section Device says
[I]Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection[/I]

And then comes the problem, after rebooting. I get the shell, the nvidia module is loaded (or that is what lsmod says to me), lspci -k says:
[I]01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 14c2
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

[/I]So I think everything should be ok, but when I type "startx" it doesn't work

And here is what /var/log/Xorg.0.log says after that:
[I]
[   275.235] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   275.241] X Protocol Version 11, Revision 0
[   275.243] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   275.244] Current Operating System: Linux ASUS-P42JC 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64
[   275.245] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=2d7394d7-5a97-43a5-b37c-8bb0334e4de3 ro nouveau.modset=0 quiet splash
[   275.247] Build Date: 16 September 2010  06:18:41PM
[   275.248] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   275.250] Current version of pixman: 0.18.4
[   275.252]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   275.255] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   275.260] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 14 22:24:39 2010
[   275.262] (==) Using config file: "/etc/X11/xorg.conf"
[   275.263] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   275.265] (==) ServerLayout "Layout0"
[   275.265] (**) |-->Screen "Screen0" (0)
[   275.265] (**) |   |-->Monitor "Monitor0"
[   275.265] (**) |   |-->Device "Device0"
[   275.265] (**) |-->Input Device "Keyboard0"
[   275.265] (**) |-->Input Device "Mouse0"
[   275.265] (==) Automatically adding devices
[   275.265] (==) Automatically enabling devices
[   275.265] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   275.265]     Entry deleted from font path.
[   275.265] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   275.265] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   275.265] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   275.265] (WW) Disabling Keyboard0
[   275.265] (WW) Disabling Mouse0
[   275.265] (II) Loader magic: 0x7d0200
[   275.265] (II) Module ABI versions:
[   275.265]     X.Org ANSI C Emulation: 0.4
[   275.265]     X.Org Video Driver: 8.0
[   275.265]     X.Org XInput driver : 11.0
[   275.265]     X.Org Server Extension : 4.0
[   275.266] (--) PCI:*(0:0:2:0) 8086:0046:1043:14c2 rev 24, Mem @ 0xd3400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e080/8
[   275.266] (--) PCI: (0:1:0:0) 10de:0a70:1043:14c2 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[   275.266] (II) Open ACPI successful (/var/run/acpid.socket)
[   275.266] (II) LoadModule: "extmod"
[   275.267] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   275.267] (II) Module extmod: vendor="X.Org Foundation"
[   275.267]     compiled for 1.9.0, module version = 1.0.0
[   275.267]     Module class: X.Org Server Extension
[   275.267]     ABI class: X.Org Server Extension, version 4.0
[   275.267] (II) Loading extension MIT-SCREEN-SAVER
[   275.267] (II) Loading extension XFree86-VidModeExtension
[   275.267] (II) Loading extension XFree86-DGA
[   275.267] (II) Loading extension DPMS
[   275.267] (II) Loading extension XVideo
[   275.267] (II) Loading extension XVideo-MotionCompensation
[   275.267] (II) Loading extension X-Resource
[   275.267] (II) LoadModule: "dbe"
[   275.267] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   275.267] (II) Module dbe: vendor="X.Org Foundation"
[   275.267]     compiled for 1.9.0, module version = 1.0.0
[   275.267]     Module class: X.Org Server Extension
[   275.267]     ABI class: X.Org Server Extension, version 4.0
[   275.267] (II) Loading extension DOUBLE-BUFFER
[   275.267] (II) LoadModule: "glx"
[   275.268] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[   275.274] (II) Module glx: vendor="NVIDIA Corporation"
[   275.274]     compiled for 4.0.2, module version = 1.0.0
[   275.274]     Module class: X.Org Server Extension
[   275.274] (II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
[   275.274] (II) Loading extension GLX
[   275.274] (II) LoadModule: "record"
[   275.275] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   275.275] (II) Module record: vendor="X.Org Foundation"
[   275.275]     compiled for 1.9.0, module version = 1.13.0
[   275.275]     Module class: X.Org Server Extension
[   275.275]     ABI class: X.Org Server Extension, version 4.0
[   275.275] (II) Loading extension RECORD
[   275.275] (II) LoadModule: "dri"
[   275.275] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   275.275] (II) Module dri: vendor="X.Org Foundation"
[   275.275]     compiled for 1.9.0, module version = 1.0.0
[   275.275]     ABI class: X.Org Server Extension, version 4.0
[   275.275] (II) Loading extension XFree86-DRI
[   275.275] (II) LoadModule: "dri2"
[   275.276] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   275.276] (II) Module dri2: vendor="X.Org Foundation"
[   275.276]     compiled for 1.9.0, module version = 1.2.0
[   275.276]     ABI class: X.Org Server Extension, version 4.0
[   275.276] (II) Loading extension DRI2
[   275.276] (II) LoadModule: "nvidia"
[   275.276] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   275.276] (II) Module nvidia: vendor="NVIDIA Corporation"
[   275.276]     compiled for 4.0.2, module version = 1.0.0
[   275.276]     Module class: X.Org Video Driver
[   275.276] (II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
[   275.276] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   275.276] (--) using VT number 8

[   275.279] (EE) No devices detected.
[   275.279] 
Fatal server error:
[   275.279] no screens found
[   275.279] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   275.280] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   275.280] 

[/I]I hope someone can help me getting this running before I get a Windows 7 license :(

Regards from Munich,

changomuc

---

### Post by gschuager on 2010-10-14
Same problem here with a laptop Dell Vostro 3400

---

### Post by changomuc on 2010-10-15
Now I also tried installing the nvidia driver downloaded from nvidia.com, after installing the same issue. My screen is not beeing recognized :(

---

### Post by ellgor on 2010-10-16
Hi,

Have the nvidia driver easy to hand, example

/home/gordon/Downloads/NVIDIA-Linux-x86_64-195.36.24-pkg2.run

Open a terminal and stop the gdm manager with:

sudo gdm-stop

A black screen with terminal access will be presented, cd to the nvidia file and start it with this:

sudo sh NVIDIA-Linux-x86_64-260.19.12.run (change this to match the one you have)

Follow the nvidia guide during which it will ask to remove any previous files, agree

Once done restart the gdm with:

sudo service gdm start

Regards, Ellgor.

---

### Post by changomuc on 2010-10-17
```

chango@ASUS-P42JC:~$ sudo gdm stop

** (gdm-binary:2362): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:2362): WARNING **: Could not acquire name; bailing out

```

this is new :(

---

### Post by ellgor on 2010-10-17
Hi,

There is a dash between gdm and stop, gdm-stop, it is essential for the correct running of the command.

Regards, Ellgor.

---

### Post by changomuc on 2010-10-18
I tried that way first! With this result:
```

schango@ASUS-P42JC:~$ sudo gdm-stop
[sudo] password for chango: 
sudo: gdm-stop: command not found
```

---

### Post by ellgor on 2010-10-19
Hi,

Just noticed that your on Maverick 64bit, the gdm-stop refers to GnomeDisplayManager, I'm not using that particular brand (I'm on Mint9, ignore the stats) so whether Maverick still uses that particular mode, I dont know, I have heard Plymouth mentioned but as I say I'm not on Maverick, sorry. 

Regards, Ellgor.

---

### Post by Samsagax on 2011-01-03
> **ellgor said:**
> Hi,

Have the nvidia driver easy to hand, example

/home/gordon/Downloads/NVIDIA-Linux-x86_64-195.36.24-pkg2.run

Open a terminal and stop the gdm manager with:

sudo gdm-stop

(...)

Once done restart the gdm with:

sudo service gdm start

Regards, Ellgor.

Ok.
I've stoped gdm with this command:
```
sudo /etc/init.d/gdm stop
```To restart it just type in the console:
```
sudo /etc/init.d/gdm restart
```Tried every installation on the nvidia.com drivers options and got allways the same problem. The boot-up ends in a console. The X server is unable to find screens or devices even changing the xorg.conf file, giving a customEDID file or explicitly give the PCI port of the card.

I'm on a Dell Vostro 3500 Laptop. 

Is there anyway i can help/contribute with this issue? I'm able to do and undo the "nvidia mess" successfully for now.

---

### Post by changomuc on 2011-01-03
I think it has something to do (in my case) with the Optimus Technology of Nvidia. I think Linux drivers still don't support this kind of graphic cards.

Regards,

changomuc

---

### Post by realzippy on 2011-01-03
> **changomuc said:**
> I think it has something to do (in my case) with the Optimus Technology of Nvidia. I think Linux drivers still don't support this kind of graphic cards.

Regards,

changomuc


Indeed.
[http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus)

---

