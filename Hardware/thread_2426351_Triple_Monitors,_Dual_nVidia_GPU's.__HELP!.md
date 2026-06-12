---
title: "Triple Monitors, Dual nVidia GPU's.  HELP!"
date: 2019-09-07
forum: Hardware
---

### Post by xstrada2501 on 2019-09-07
[SIZE=3][COLOR=#242729][FONT=Arial]Here's some backstory: Dual boot: Windows 10 on it's own drive (working perfectly), Ubuntu 18.04 on it's own drive. (So, dual drive/dual boot config) Grub 2 bootloader working as intended. Fresh install and config/update Ubuntu 18.04 LTS (so no previous crap to sift through).
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]3 monitors (40", 2x 23") 1920 x 1080 res. Two nVidia cards: (GeForce GTX 980ti & 660ti) driver ver. 430 (prop). 980ti runs the 40" via HDMI to a reciever. (working properly) 660ti runs the 23" via DVI. (this is where the problem begins)
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This configuration works perfectly on Win 10. Problem only presents in Ubuntu 18.04. Not pointing fingers as I adore this distro and want to resolve this.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Everything works - surprisingly - except any life from the 660ti (which is detected) or my 23" monitors (which are also detected, but disabled in xServer and WILL NOT display when enabled/applied). This was not an issue with Nouveau drivers, (Ubuntu display handled extended displays and worked as intented), but screen tearing and lag was. I have tried enabling and configuring my displays in xServer, but upon restart, I get a black screen, bootloop and my only fix is to wipe the drive and start again as recovery option does nothing.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am reluctant to do much of anything with xServer right now without solid info regarding configuration, since I'm just happy that Ubuntu itself is booting and working. Getting my two other monitors working would be a HUGE plus.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thank you in advance for any help and please don't hesitate to ask more questions regarding my rig.[/FONT][/COLOR][/SIZE]

---

### Post by Autodave on 2019-09-07
Where did you get the Nvidia driver from?  You should only use the drivers in the repositories. 

After you installed and updated 18.04, the proper driver would have been in the repositories and also available in Settings -> Additional Drivers.

---

### Post by CatKiller on 2019-09-07
> **xstrada2501 said:**
> I am reluctant to do much of anything with xServer right now without solid info regarding configuration, since I'm just happy that Ubuntu itself is booting and working. Getting my two other monitors working would be a HUGE plus.
One thing that would make a difference is whether your configuration is static. Setting up an xorg.conf isn't that bad - the settings are pretty straightforward and are documented well in the nvidia readme - but it's clunky in regard to changes. You don't *need* an xorg.conf these days, so if it all goes pear-shaped you can just delete (or rename) the file to be back where you are now.

There are a handful of different ways to set up your multimonitor arrangement, each with pros and cons: an X Screen for each monitor, one massive Screen, or TwinView which I can't remember much about. Having two cards rather than one with multiple outputs may limit which methods you can use. It's a long time since I last played with it, so I can't remember all the details, but the documentation is good.

---

### Post by xstrada2501 on 2019-09-07
I did get the driver from the official repository.  Main 40" monitor and 980ti works, 23" ones don't.  660ti is seen by xServer and Ubuntu itself, but is not being used and I cannot for the life of me find out how to get it working.

---

### Post by xstrada2501 on 2019-09-07
> **CatKiller said:**
> One thing that would make a difference is whether your configuration is static. Setting up an xorg.conf isn't that bad - the settings are pretty straightforward and are documented well in the nvidia readme - but it's clunky in regard to changes. You don't *need* an xorg.conf these days, so if it all goes pear-shaped you can just delete (or rename) the file to be back where you are now.

There are a handful of different ways to set up your multimonitor arrangement, each with pros and cons: an X Screen for each monitor, one massive Screen, or TwinView which I can't remember much about. Having two cards rather than one with multiple outputs may limit which methods you can use. It's a long time since I last played with it, so I can't remember all the details, but the documentation is good.

The set-up I am looking for is an xScreen for each monitor.  The main one (40") in the middle controlled by the 980ti, the 23" to the left and right controlled by the 660ti.  Again, this configuration is working as intended in win 10, but in Ubuntu and xServer only the main display (40" 980ti) is working and although the 23" and 660ti is present and detected, it's simply not being used and I cannot get it going.

Messing with xServer and the config files it creates when I try to save configs is what locks up Ubuntu and, as I said, booting into recovery and using the tools there did nothing.  THAT is why I'm scared to do anything with xServer untill I find a solid fix because I don't want to have re-install AGAIN.  But I will look up the documentation you speak of and see what I can find.

---

### Post by CatKiller on 2019-09-07
If it boots to a black screen (which can be scary when you're new) it just means that the display didn't start: you don't need to reinstall.

By far the easiest way to fix things when it's all gone wrong, particularly if you have no display, is to just boot the install image. It's a fully-fictional Linux environment, with all the file managers, text editors, and (crucially) web browsers that you're used to. The fix is generally editing or removing a file somewhere; it's nicer to not have to do that from a limited shell.

From memory, if you're doing a static config in xorg.conf, you'll want to define each Monitor (only the name is essential, but also anything that doesn't get autoconfigured to your taste), each Device (which would be your two graphics cards), each Screen (which would be a pairing of one named Monitor with one output of a named Device), and a ServerLayout which describes which Screen you want where.

You get a copy of Nvidia's readme with the driver, plus there are copies online. I'm typing on my phone, otherwise I'd look up the path of it for you.

---

### Post by xstrada2501 on 2019-09-07
Ok, so something of a breakthrough...  (Appologies if I came across as a little hostile earlier)

Just for shits and giggles, I saved a baseline config file from the xServer after creating a disk image for Ubuntu in case something went wrong.  File saved in /etc/x11/xorg.conf where it was supposed to.  Rebooted and all went well.  Had a lookie through the .conf file and discovered no listing for my 660ti.  Which means despite it being THERE in xServer, and despite it being in Ubuntu's "Additional Drivers" tab (with the most recent driver installed), Ubuntu is ignoring it and it's essentially catatonic.

So what do I do now?

---

### Post by CatKiller on 2019-09-07
Don't forget that case is important: capital X in /etc/X11/xorg.conf.

As I mentioned earlier, you don't *need* an xorg.conf these days; it's generally all automatically detected. One used to have to do all this by hand for every machine.

The log is at /var/log/Xorg.0.log. You may find that both cards are being initialised even without an entry in xorg.conf for the 660 Ti. Or it might have just initialised the primary card. There is an xorg.conf option to make the log file even more verbose, but I can't remember it off the top of my head.

In case you didn't find the readme, there's a copy [here](http://us.download.nvidia.com/XFree86/Linux-x86_64/430.40/README/index.html). **man xorg.conf** also has good information.

It's also possible that the nvidia settings application can do some of this stuff without playing around with xorg.conf: the last time I was playing around with multiple graphics cards, manual editing was the only game in town. The nvidia-xconfig method of automatically generating an xorg.conf file produces hideous results: if you generate one for reference you'll still likely want to rewrite it.

---

### Post by xstrada2501 on 2019-09-07
> **CatKiller said:**
> Don't forget that case is important: capital X in /etc/X11/xorg.conf.

As I mentioned earlier, you don't *need* an xorg.conf these days; it's generally all automatically detected. One used to have to do all this by hand for every machine.

The log is at /var/log/Xorg.0.log. You may find that both cards are being initialised even without an entry in xorg.conf for the 660 Ti. Or it might have just initialised the primary card. There is an xorg.conf option to make the log file even more verbose, but I can't remember it off the top of my head.

In case you didn't find the readme, there's a copy [here]("http://us.download.nvidia.com/XFree86/Linux-x86_64/430.40/README/index.html"). **man xorg.conf** also has good information.

It's also possible that the nvidia settings application can do some of this stuff without playing around with xorg.conf: the last time I was playing around with multiple graphics cards, manual editing was the only game in town. The nvidia-xconfig method of automatically generating an xorg.conf file produces hideous results: if you generate one for reference you'll still likely want to rewrite it.

Ok, so now that I know where the files and logs are, what am I supposed to be looking for?  I have only the barest understanding of lua and html/css code - I can somewhat read this, but I'm not sure what to focus?  And what good will it do me if I can't get Ubuntu to pay attention to the card?  I have messed about with BIOS settings to see if it's a PCIE issue, my board doesn't have secure boot...
I have stipped out all traces of Nouveau drivers and they were the only ones that worked - badly - with my 660ti.
Do I have to try the "nomodset" thing I have seen?  I'd rather not.  This tinkering is getting hairy and I don't want to keep poking this bear.

To be clear - the 980ti is working.  The 660ti is not.  BOTH have the correct and latest driver from Ubuntu repositories installed.  Both cards work flawlessly in Windows 10.  This is NOT a driver issue - least I don't think it is.

Open to suggestions.

---

### Post by CatKiller on 2019-09-08
> **xstrada2501 said:**
> Ok, so now that I know where the files and logs are, what am I supposed to be looking for? 

You'll see a section where your 980 gets initialised and configured. You're interested in whether your 660 also gets initialised, and what the X server chooses to do with it. 

>  And what good will it do me if I can't get Ubuntu to pay attention to the card?   

It knows about the card, it just doesn't know what you want to do with it. That's why you specify that with your configuration. If you had a headless number-crunching cluster, for example, you wouldn't want an X server started on all of your compute units. It's not just desktop machines that Linux gets used for. 

> Do I have to try the "nomodset" thing I have seen?  I'd rather not.   

No. nomodeset is because the nouveau driver isn't as good at identifying the available resolutions as the nvidia driver, so it sometimes sets the monitor to the wrong mode; nomodeset tells it not to bother. You aren't using nouveau, and you *do* want the driver to set the mode. 

>  This tinkering is getting hairy and I don't want to keep poking this bear. 

The tinkering is fun!

If it goes wrong, the worst case scenario is that you need to boot from a thumb drive and rename a file, which takes a couple of minutes.

In going through the process you'll realise how configurable everything is, and at any point you can stop tinkering and be in the same place you are now.

---

### Post by xstrada2501 on 2019-09-08
Ok, so I will link the .log file.  I can see where the 660ti comes up, but I can't figure out what's being done with it.

I don't expect you to to go through this for me, but please know I really do appreciate your help and expertise.

```
[    27.106] (--) Log file renamed from "/var/log/Xorg.pid-1940.log" to "/var/log/Xorg.0.log"[    27.116] 
X.Org X Server 1.20.4
X Protocol Version 11, Revision 0
[    27.116] Build Operating System: Linux 4.4.0-148-generic x86_64 Ubuntu
[    27.116] Current Operating System: Linux Virgil-Linux 5.0.0-27-generic #28~18.04.1-Ubuntu SMP Thu Aug 22 03:00:32 UTC 2019 x86_64
[    27.116] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-27-generic root=UUID=0a32abd3-239f-4c81-8d57-7091d51f3754 ro quiet splash vt.handoff=1
[    27.116] Build Date: 02 May 2019  08:06:54AM
[    27.116] xorg-server-hwe-18.04 2:1.20.4-1ubuntu3~18.04.1 (For technical support please see http://www.ubuntu.com/support) 
[    27.116] Current version of pixman: 0.34.0
[    27.116]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    27.116] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.116] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep  9 07:47:47 2019
[    27.126] (==) Using config file: "/etc/X11/xorg.conf"
[    27.126] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.176] (==) ServerLayout "Layout0"
[    27.176] (**) |-->Screen "Screen0" (0)
[    27.176] (**) |   |-->Monitor "Monitor0"
[    27.189] (**) |   |-->Device "Device0"
[    27.189] (**) |-->Input Device "Keyboard0"
[    27.189] (**) |-->Input Device "Mouse0"
[    27.189] (**) Option "Xinerama" "0"
[    27.189] (==) Automatically adding devices
[    27.189] (==) Automatically enabling devices
[    27.189] (==) Automatically adding GPU devices
[    27.189] (==) Automatically binding GPU devices
[    27.189] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    27.189] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.189]     Entry deleted from font path.
[    27.189] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.189]     Entry deleted from font path.
[    27.189] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.189]     Entry deleted from font path.
[    27.189] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.189]     Entry deleted from font path.
[    27.189] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.189]     Entry deleted from font path.
[    27.189] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.189] (==) ModulePath set to "/usr/lib/xorg/modules"
[    27.189] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    27.189] (WW) Disabling Keyboard0
[    27.189] (WW) Disabling Mouse0
[    27.189] (II) Loader magic: 0x55ce4f817020
[    27.189] (II) Module ABI versions:
[    27.189]     X.Org ANSI C Emulation: 0.4
[    27.189]     X.Org Video Driver: 24.0
[    27.189]     X.Org XInput driver : 24.1
[    27.189]     X.Org Server Extension : 10.0
[    27.190] (++) using VT number 1


[    27.193] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c3
[    27.194] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.195] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 12 paused 0
[    27.195] (II) xfree86: Adding drm device (/dev/dri/card1)
[    27.196] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 13 paused 0
[    27.198] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia-430/xorg,/usr/lib/xorg/modules"
[    27.198] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia-430/xorg,/usr/lib/x86_64-linux-gnu/nvidia-430/xorg,/usr/lib/xorg/modules"
[    27.199] (--) PCI:*(1@0:0:0) 10de:17c8:3842:4993 rev 161, Mem @ 0xf6000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/131072
[    27.200] (--) PCI: (2@0:0:0) 10de:1183:1043:841e rev 161, Mem @ 0xf4000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    27.200] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    27.200] (II) LoadModule: "dbe"
[    27.200] (II) Module "dbe" already built-in
[    27.200] (II) LoadModule: "extmod"
[    27.200] (II) Module "extmod" already built-in
[    27.200] (II) LoadModule: "glx"
[    27.256] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.296] (II) Module glx: vendor="X.Org Foundation"
[    27.296]     compiled for 1.20.4, module version = 1.0.0
[    27.296]     ABI class: X.Org Server Extension, version 10.0
[    27.296] (II) LoadModule: "nvidia"
[    27.296] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia-430/xorg/nvidia_drv.so
[    27.406] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.406]     compiled for 1.6.99.901, module version = 1.0.0
[    27.406]     Module class: X.Org Video Driver
[    27.426] (II) NVIDIA dlloader X Driver  430.26  Tue Jun  4 17:52:10 CDT 2019
[    27.426] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    27.436] (II) systemd-logind: releasing fd for 226:0
[    27.446] (II) Loading sub module "fb"
[    27.446] (II) LoadModule: "fb"
[    27.446] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.476] (II) Module fb: vendor="X.Org Foundation"
[    27.476]     compiled for 1.20.4, module version = 1.0.0
[    27.476]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.476] (II) Loading sub module "wfb"
[    27.476] (II) LoadModule: "wfb"
[    27.476] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.506] (II) Module wfb: vendor="X.Org Foundation"
[    27.506]     compiled for 1.20.4, module version = 1.0.0
[    27.506]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.506] (II) Loading sub module "ramdac"
[    27.506] (II) LoadModule: "ramdac"
[    27.506] (II) Module "ramdac" already built-in
[    27.516] (II) systemd-logind: releasing fd for 226:1
[    27.517] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    27.517] (==) NVIDIA(0): RGB weight 888
[    27.518] (==) NVIDIA(0): Default visual is TrueColor
[    27.518] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.526] (II) Applying OutputClass "nvidia" options to /dev/dri/card0
[    27.526] (**) NVIDIA(0): Option "Stereo" "0"
[    27.526] (**) NVIDIA(0): Option "nvidiaXineramaInfoOrder" "DFP-1"
[    27.526] (**) NVIDIA(0): Option "SLI" "Off"
[    27.526] (**) NVIDIA(0): Option "MultiGPU" "Off"
[    27.526] (**) NVIDIA(0): Option "BaseMosaic" "off"
[    27.526] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[    27.526] (**) NVIDIA(0): Stereo disabled by request
[    27.526] (**) NVIDIA(0): NVIDIA SLI disabled.
[    27.526] (**) NVIDIA(0): NVIDIA Multi-GPU disabled.
[    27.526] (**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
[    27.526] (**) NVIDIA(0): Enabling 2D acceleration
[    27.526] (II) Loading sub module "glxserver_nvidia"
[    27.526] (II) LoadModule: "glxserver_nvidia"
[    27.527] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia-430/xorg/libglxserver_nvidia.so
[    28.206] (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
[    28.206]     compiled for 1.6.99.901, module version = 1.0.0
[    28.206]     Module class: X.Org Server Extension
[    28.216] (II) NVIDIA GLX Module  430.26  Tue Jun  4 17:50:01 CDT 2019
[    28.550] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    28.550] (--) NVIDIA(0):     CRT-0
[    28.550] (--) NVIDIA(0):     DFP-0
[    28.550] (--) NVIDIA(0):     DFP-1 (boot)
[    28.550] (--) NVIDIA(0):     DFP-2
[    28.550] (--) NVIDIA(0):     DFP-3
[    28.550] (--) NVIDIA(0):     DFP-4
[    28.550] (--) NVIDIA(0):     DFP-5
[    28.550] (--) NVIDIA(0):     DFP-6
[    28.550] (--) NVIDIA(0):     DFP-7
[    28.551] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 980 Ti (GM200-A) at PCI:1:0:0 (GPU-0)
[    28.551] (--) NVIDIA(0): Memory: 6291456 kBytes
[    28.551] (--) NVIDIA(0): VideoBIOS: 84.00.36.00.90
[    28.551] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    28.555] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    28.555] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    28.555] (--) NVIDIA(GPU-0): 
[    28.559] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    28.559] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    28.559] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    28.559] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): connected
[    28.590] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): Internal TMDS
[    28.590] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): 600.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    28.590] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    28.590] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    28.590] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    28.590] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    28.590] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    28.590] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    28.590] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    28.590] (--) NVIDIA(GPU-0): DFP-5: 165.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    28.590] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    28.590] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.590] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    28.590] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    28.590] (--) NVIDIA(GPU-0): DFP-7: 165.0 MHz maximum pixel clock
[    28.590] (--) NVIDIA(GPU-0): 
[    28.594] (II) NVIDIA(0): Validated MetaModes:
[    28.594] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    28.594] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    28.597] (--) NVIDIA(0): DPI set to (54, 54); computed from "UseEdidDpi" X config
[    28.597] (--) NVIDIA(0):     option
[    28.837] (--) NVIDIA(0): Valid display device(s) on GPU-1 at PCI:2:0:0
[    28.837] (--) NVIDIA(0):     CRT-0
[    28.837] (--) NVIDIA(0):     DFP-0 (boot)
[    28.837] (--) NVIDIA(0):     DFP-1
[    28.837] (--) NVIDIA(0):     DFP-2
[    28.837] (--) NVIDIA(0):     DFP-3
[    28.837] (--) NVIDIA(0):     DFP-4
[    28.844] (--) NVIDIA(GPU-1): CRT-0: disconnected
[    28.844] (--) NVIDIA(GPU-1): CRT-0: 400.0 MHz maximum pixel clock
[    28.844] (--) NVIDIA(GPU-1): 
[    28.860] (--) NVIDIA(GPU-1): HP x23LED (DFP-0): connected
[    28.860] (--) NVIDIA(GPU-1): HP x23LED (DFP-0): Internal TMDS
[    28.860] (--) NVIDIA(GPU-1): HP x23LED (DFP-0): 330.0 MHz maximum pixel clock
[    28.860] (--) NVIDIA(GPU-1): 
[    28.860] (--) NVIDIA(GPU-1): DFP-1: disconnected
[    28.860] (--) NVIDIA(GPU-1): DFP-1: Internal TMDS
[    28.860] (--) NVIDIA(GPU-1): DFP-1: 165.0 MHz maximum pixel clock
[    28.860] (--) NVIDIA(GPU-1): 
[    28.860] (--) NVIDIA(GPU-1): DFP-2: disconnected
[    28.860] (--) NVIDIA(GPU-1): DFP-2: Internal TMDS
[    28.860] (--) NVIDIA(GPU-1): DFP-2: 165.0 MHz maximum pixel clock
[    28.860] (--) NVIDIA(GPU-1): 
[    28.867] (--) NVIDIA(GPU-1): HP W2371d (DFP-3): connected
[    28.867] (--) NVIDIA(GPU-1): HP W2371d (DFP-3): Internal TMDS
[    28.867] (--) NVIDIA(GPU-1): HP W2371d (DFP-3): 330.0 MHz maximum pixel clock
[    28.867] (--) NVIDIA(GPU-1): 
[    28.867] (--) NVIDIA(GPU-1): DFP-4: disconnected
[    28.867] (--) NVIDIA(GPU-1): DFP-4: Internal DisplayPort
[    28.867] (--) NVIDIA(GPU-1): DFP-4: 960.0 MHz maximum pixel clock
[    28.867] (--) NVIDIA(GPU-1): 
[    28.887] (II) NVIDIA(GPU-1): NVIDIA GPU GeForce GTX 660 Ti (GK104) at PCI:2:0:0 (GPU-1)
[    28.887] (--) NVIDIA(GPU-1): Memory: 2097152 kBytes
[    28.887] (--) NVIDIA(GPU-1): VideoBIOS: 80.04.4b.00.5a
[    28.887] (II) NVIDIA(GPU-1): Detected PCI Express Link width: 16X
[    28.887] (II) NVIDIA: Using 6144.00 MB of virtual memory for indirect memory
[    28.887] (II) NVIDIA:     access.
[    29.050] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
[    29.206] (==) NVIDIA(0): Disabling shared memory pixmaps
[    29.206] (==) NVIDIA(0): Backing store enabled
[    29.206] (==) NVIDIA(0): Silken mouse enabled
[    29.226] (**) NVIDIA(0): DPMS enabled
[    29.256] (II) Loading sub module "dri2"
[    29.256] (II) LoadModule: "dri2"
[    29.256] (II) Module "dri2" already built-in
[    29.256] (II) NVIDIA(0): [DRI2] Setup complete
[    29.256] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    29.265] (II) Initializing extension Generic Event Extension
[    29.266] (II) Initializing extension SHAPE
[    29.266] (II) Initializing extension MIT-SHM
[    29.266] (II) Initializing extension XInputExtension
[    29.276] (II) Initializing extension XTEST
[    29.276] (II) Initializing extension BIG-REQUESTS
[    29.276] (II) Initializing extension SYNC
[    29.276] (II) Initializing extension XKEYBOARD
[    29.276] (II) Initializing extension XC-MISC
[    29.277] (II) Initializing extension SECURITY
[    29.277] (II) Initializing extension XFIXES
[    29.277] (II) Initializing extension RENDER
[    29.277] (II) Initializing extension RANDR
[    29.277] (II) Initializing extension COMPOSITE
[    29.277] (II) Initializing extension DAMAGE
[    29.277] (II) Initializing extension MIT-SCREEN-SAVER
[    29.278] (II) Initializing extension DOUBLE-BUFFER
[    29.278] (II) Initializing extension RECORD
[    29.278] (II) Initializing extension DPMS
[    29.278] (II) Initializing extension Present
[    29.278] (II) Initializing extension DRI3
[    29.278] (II) Initializing extension X-Resource
[    29.278] (II) Initializing extension XVideo
[    29.279] (II) Initializing extension XVideo-MotionCompensation
[    29.279] (II) Initializing extension SELinux
[    29.279] (II) SELinux: Disabled on system
[    29.279] (II) Initializing extension GLX
[    29.279] (II) Initializing extension GLX
[    29.279] (II) Indirect GLX disabled.
[    29.279] (II) GLX: Another vendor is already registered for screen 0
[    29.279] (II) Initializing extension XFree86-VidModeExtension
[    29.279] (II) Initializing extension XFree86-DGA
[    29.279] (II) Initializing extension XFree86-DRI
[    29.285] (II) Initializing extension DRI2
[    29.286] (II) Initializing extension NV-GLX
[    29.286] (II) Initializing extension NV-CONTROL
[    29.286] (II) Initializing extension XINERAMA
[    29.566] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.566] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    29.566] (II) LoadModule: "libinput"
[    29.566] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    29.590] (II) Module libinput: vendor="X.Org Foundation"
[    29.590]     compiled for 1.20.1, module version = 0.28.1
[    29.590]     Module class: X.Org XInput Driver
[    29.590]     ABI class: X.Org XInput driver, version 24.1
[    29.590] (II) Using input driver 'libinput' for 'Power Button'
[    29.591] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 45 paused 0
[    29.591] (**) Power Button: always reports core events
[    29.591] (**) Option "Device" "/dev/input/event1"
[    29.591] (**) Option "_source" "server/udev"
[    29.592] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    29.592] (II) event1  - Power Button: device is a keyboard
[    29.592] (II) event1  - Power Button: device removed
[    29.592] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    29.592] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.592] (**) Option "xkb_model" "pc105"
[    29.592] (**) Option "xkb_layout" "us"
[    29.592] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    29.592] (II) event1  - Power Button: device is a keyboard
[    29.593] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.593] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    29.593] (II) Using input driver 'libinput' for 'Power Button'
[    29.594] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 48 paused 0
[    29.594] (**) Power Button: always reports core events
[    29.594] (**) Option "Device" "/dev/input/event0"
[    29.594] (**) Option "_source" "server/udev"
[    29.594] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    29.594] (II) event0  - Power Button: device is a keyboard
[    29.594] (II) event0  - Power Button: device removed
[    29.594] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.594] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    29.594] (**) Option "xkb_model" "pc105"
[    29.594] (**) Option "xkb_layout" "us"
[    29.595] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    29.595] (II) event0  - Power Button: device is a keyboard
[    29.595] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event16)
[    29.595] (II) No input driver specified, ignoring this device.
[    29.595] (II) This device may have been added with another device file.
[    29.595] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event17)
[    29.595] (II) No input driver specified, ignoring this device.
[    29.595] (II) This device may have been added with another device file.
[    29.595] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event18)
[    29.595] (II) No input driver specified, ignoring this device.
[    29.595] (II) This device may have been added with another device file.
[    29.596] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event19)
[    29.596] (II) No input driver specified, ignoring this device.
[    29.596] (II) This device may have been added with another device file.
[    29.596] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event20)
[    29.596] (II) No input driver specified, ignoring this device.
[    29.596] (II) This device may have been added with another device file.
[    29.597] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event21)
[    29.597] (II) No input driver specified, ignoring this device.
[    29.597] (II) This device may have been added with another device file.
[    29.597] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event22)
[    29.597] (II) No input driver specified, ignoring this device.
[    29.597] (II) This device may have been added with another device file.
[    29.597] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event23)
[    29.597] (II) No input driver specified, ignoring this device.
[    29.597] (II) This device may have been added with another device file.
[    29.598] (II) config/udev: Adding input device SteelSeries SteelSeries Arctis 5 (/dev/input/event12)
[    29.598] (**) SteelSeries SteelSeries Arctis 5: Applying InputClass "libinput keyboard catchall"
[    29.598] (II) Using input driver 'libinput' for 'SteelSeries SteelSeries Arctis 5'
[    29.599] (II) systemd-logind: got fd for /dev/input/event12 13:76 fd 49 paused 0
[    29.599] (**) SteelSeries SteelSeries Arctis 5: always reports core events
[    29.599] (**) Option "Device" "/dev/input/event12"
[    29.599] (**) Option "_source" "server/udev"
[    29.599] (II) event12 - SteelSeries SteelSeries Arctis 5: is tagged by udev as: Keyboard
[    29.599] (II) event12 - SteelSeries SteelSeries Arctis 5: device is a keyboard
[    29.599] (II) event12 - SteelSeries SteelSeries Arctis 5: device removed
[    29.599] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.5/0003:1038:1250.0004/input/input15/event12"
[    29.599] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Arctis 5" (type: KEYBOARD, id 8)
[    29.599] (**) Option "xkb_model" "pc105"
[    29.599] (**) Option "xkb_layout" "us"
[    29.600] (II) event12 - SteelSeries SteelSeries Arctis 5: is tagged by udev as: Keyboard
[    29.600] (II) event12 - SteelSeries SteelSeries Arctis 5: device is a keyboard
[    29.601] (II) config/udev: Adding input device SteelSeries SteelSeries Rival 500 Gaming Mouse (/dev/input/event9)
[    29.601] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse: Applying InputClass "libinput pointer catchall"
[    29.601] (II) Using input driver 'libinput' for 'SteelSeries SteelSeries Rival 500 Gaming Mouse'
[    29.658] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 50 paused 0
[    29.658] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse: always reports core events
[    29.658] (**) Option "Device" "/dev/input/event9"
[    29.658] (**) Option "_source" "server/udev"
[    29.658] (II) event9  - SteelSeries SteelSeries Rival 500 Gaming Mouse: is tagged by udev as: Mouse
[    29.658] (II) event9  - SteelSeries SteelSeries Rival 500 Gaming Mouse: device is a pointer
[    29.658] (II) event9  - SteelSeries SteelSeries Rival 500 Gaming Mouse: device removed
[    29.659] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.1/0003:1038:170E.0002/input/input12/event9"
[    29.659] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Rival 500 Gaming Mouse" (type: MOUSE, id 9)
[    29.659] (**) Option "AccelerationScheme" "none"
[    29.659] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse: (accel) selected scheme none/0
[    29.659] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse: (accel) acceleration factor: 2.000
[    29.659] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse: (accel) acceleration threshold: 4
[    29.659] (II) event9  - SteelSeries SteelSeries Rival 500 Gaming Mouse: is tagged by udev as: Mouse
[    29.659] (II) event9  - SteelSeries SteelSeries Rival 500 Gaming Mouse: device is a pointer
[    29.660] (II) config/udev: Adding input device SteelSeries SteelSeries Rival 500 Gaming Mouse (/dev/input/mouse0)
[    29.660] (II) No input driver specified, ignoring this device.
[    29.660] (II) This device may have been added with another device file.
[    29.661] (II) config/udev: Adding input device SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard (/dev/input/event10)
[    29.661] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: Applying InputClass "libinput keyboard catchall"
[    29.661] (II) Using input driver 'libinput' for 'SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard'
[    29.661] (II) systemd-logind: got fd for /dev/input/event10 13:74 fd 51 paused 0
[    29.661] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: always reports core events
[    29.662] (**) Option "Device" "/dev/input/event10"
[    29.662] (**) Option "_source" "server/udev"
[    29.662] (II) event10 - SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: is tagged by udev as: Keyboard
[    29.662] (II) event10 - SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: device is a keyboard
[    29.662] (II) event10 - SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: device removed
[    29.662] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/0003:1038:170E.0003/input/input13/event10"
[    29.662] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard" (type: KEYBOARD, id 10)
[    29.662] (**) Option "xkb_model" "pc105"
[    29.662] (**) Option "xkb_layout" "us"
[    29.663] (II) event10 - SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: is tagged by udev as: Keyboard
[    29.663] (II) event10 - SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: device is a keyboard
[    29.663] (II) config/udev: Adding input device SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control (/dev/input/event11)
[    29.663] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: Applying InputClass "libinput keyboard catchall"
[    29.663] (II) Using input driver 'libinput' for 'SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control'
[    29.664] (II) systemd-logind: got fd for /dev/input/event11 13:75 fd 52 paused 0
[    29.664] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: always reports core events
[    29.664] (**) Option "Device" "/dev/input/event11"
[    29.664] (**) Option "_source" "server/udev"
[    29.664] (II) event11 - SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: is tagged by udev as: Keyboard
[    29.664] (II) event11 - SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: device is a keyboard
[    29.664] (II) event11 - SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: device removed
[    29.664] (II) libinput: SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: needs a virtual subdevice
[    29.664] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/0003:1038:170E.0003/input/input14/event11"
[    29.664] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control" (type: MOUSE, id 11)
[    29.664] (**) Option "AccelerationScheme" "none"
[    29.665] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: (accel) selected scheme none/0
[    29.665] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: (accel) acceleration factor: 2.000
[    29.665] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: (accel) acceleration threshold: 4
[    29.665] (II) event11 - SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: is tagged by udev as: Keyboard
[    29.665] (II) event11 - SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: device is a keyboard
[    29.665] (II) config/udev: Adding input device DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA (/dev/input/event13)
[    29.665] (**) DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: Applying InputClass "libinput keyboard catchall"
[    29.665] (II) Using input driver 'libinput' for 'DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA'
[    29.666] (II) systemd-logind: got fd for /dev/input/event13 13:77 fd 53 paused 0
[    29.666] (**) DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: always reports core events
[    29.666] (**) Option "Device" "/dev/input/event13"
[    29.666] (**) Option "_source" "server/udev"
[    29.667] (II) event13 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: is tagged by udev as: Keyboard
[    29.667] (II) event13 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: device is a keyboard
[    29.667] (II) event13 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: device removed
[    29.667] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/0003:04B4:0101.0005/input/input16/event13"
[    29.667] (II) XINPUT: Adding extended input device "DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA" (type: KEYBOARD, id 12)
[    29.667] (**) Option "xkb_model" "pc105"
[    29.667] (**) Option "xkb_layout" "us"
[    29.668] (II) event13 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: is tagged by udev as: Keyboard
[    29.668] (II) event13 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: device is a keyboard
[    29.668] (II) config/udev: Adding input device DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control (/dev/input/event14)
[    29.668] (**) DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: Applying InputClass "libinput keyboard catchall"
[    29.668] (II) Using input driver 'libinput' for 'DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control'
[    29.668] (II) systemd-logind: got fd for /dev/input/event14 13:78 fd 54 paused 0
[    29.669] (**) DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: always reports core events
[    29.669] (**) Option "Device" "/dev/input/event14"
[    29.669] (**) Option "_source" "server/udev"
[    29.669] (II) event14 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: is tagged by udev as: Keyboard
[    29.669] (II) event14 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: device is a keyboard
[    29.669] (II) event14 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: device removed
[    29.669] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/0003:04B4:0101.0006/input/input17/event14"
[    29.669] (II) XINPUT: Adding extended input device "DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control" (type: KEYBOARD, id 13)
[    29.669] (**) Option "xkb_model" "pc105"
[    29.669] (**) Option "xkb_layout" "us"
[    29.670] (II) event14 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: is tagged by udev as: Keyboard
[    29.670] (II) event14 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: device is a keyboard
[    29.671] (II) config/udev: Adding input device DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control (/dev/input/event15)
[    29.671] (**) DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: Applying InputClass "libinput keyboard catchall"
[    29.671] (II) Using input driver 'libinput' for 'DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control'
[    29.671] (II) systemd-logind: got fd for /dev/input/event15 13:79 fd 55 paused 0
[    29.671] (**) DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: always reports core events
[    29.671] (**) Option "Device" "/dev/input/event15"
[    29.671] (**) Option "_source" "server/udev"
[    29.672] (II) event15 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: is tagged by udev as: Keyboard
[    29.672] (II) event15 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: device is a keyboard
[    29.672] (II) event15 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: device removed
[    29.672] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/0003:04B4:0101.0006/input/input18/event15"
[    29.672] (II) XINPUT: Adding extended input device "DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control" (type: KEYBOARD, id 14)
[    29.672] (**) Option "xkb_model" "pc105"
[    29.672] (**) Option "xkb_layout" "us"
[    29.673] (II) event15 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: is tagged by udev as: Keyboard
[    29.673] (II) event15 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: device is a keyboard
[    29.673] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event7)
[    29.673] (II) No input driver specified, ignoring this device.
[    29.673] (II) This device may have been added with another device file.
[    29.673] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event8)
[    29.673] (II) No input driver specified, ignoring this device.
[    29.673] (II) This device may have been added with another device file.
[    29.674] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event2)
[    29.674] (II) No input driver specified, ignoring this device.
[    29.674] (II) This device may have been added with another device file.
[    29.674] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event3)
[    29.674] (II) No input driver specified, ignoring this device.
[    29.674] (II) This device may have been added with another device file.
[    29.674] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event4)
[    29.674] (II) No input driver specified, ignoring this device.
[    29.674] (II) This device may have been added with another device file.
[    29.674] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[    29.674] (II) No input driver specified, ignoring this device.
[    29.675] (II) This device may have been added with another device file.
[    29.675] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event6)
[    29.675] (II) No input driver specified, ignoring this device.
[    29.675] (II) This device may have been added with another device file.
[    29.680] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: Applying InputClass "libinput keyboard catchall"
[    29.680] (II) Using input driver 'libinput' for 'SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control'
[    29.680] (II) systemd-logind: returning pre-existing fd for /dev/input/event11 13:75
[    29.680] (**) SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: always reports core events
[    29.680] (**) Option "Device" "/dev/input/event11"
[    29.680] (**) Option "_source" "_driver/libinput"
[    29.680] (II) libinput: SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: is a virtual subdevice
[    29.680] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/0003:1038:170E.0003/input/input14/event11"
[    29.680] (II) XINPUT: Adding extended input device "SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control" (type: KEYBOARD, id 15)
[    29.680] (**) Option "xkb_model" "pc105"
[    29.680] (**) Option "xkb_layout" "us"
[    34.613] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    34.613] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    34.613] (--) NVIDIA(GPU-0): 
[    34.618] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    34.618] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    34.618] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    34.618] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): connected
[    34.649] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): Internal TMDS
[    34.649] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): 600.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    34.649] (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
[    34.649] (--) NVIDIA(GPU-0): DFP-2: 960.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    34.649] (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
[    34.649] (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    34.649] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[    34.649] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): DFP-5: disconnected
[    34.649] (--) NVIDIA(GPU-0): DFP-5: Internal TMDS
[    34.649] (--) NVIDIA(GPU-0): DFP-5: 165.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): DFP-6: disconnected
[    34.649] (--) NVIDIA(GPU-0): DFP-6: Internal DisplayPort
[    34.649] (--) NVIDIA(GPU-0): DFP-6: 960.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    34.649] (--) NVIDIA(GPU-0): DFP-7: disconnected
[    34.649] (--) NVIDIA(GPU-0): DFP-7: Internal TMDS
[    34.649] (--) NVIDIA(GPU-0): DFP-7: 165.0 MHz maximum pixel clock
[    34.649] (--) NVIDIA(GPU-0): 
[    53.649] (**) Option "fd" "45"
[    53.649] (II) event1  - Power Button: device removed
[    53.649] (**) Option "fd" "48"
[    53.649] (II) event0  - Power Button: device removed
[    53.649] (**) Option "fd" "49"
[    53.649] (II) event12 - SteelSeries SteelSeries Arctis 5: device removed
[    53.649] (**) Option "fd" "50"
[    53.649] (II) event9  - SteelSeries SteelSeries Rival 500 Gaming Mouse: device removed
[    53.649] (**) Option "fd" "51"
[    53.649] (II) event10 - SteelSeries SteelSeries Rival 500 Gaming Mouse Keyboard: device removed
[    53.649] (**) Option "fd" "52"
[    53.650] (**) Option "fd" "53"
[    53.650] (II) event13 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA: device removed
[    53.650] (**) Option "fd" "54"
[    53.650] (II) event14 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA System Control: device removed
[    53.650] (**) Option "fd" "55"
[    53.650] (II) event15 - DATACOMP SteelS&#49153;&#772;&#1033;&#786;DATA Consumer Control: device removed
[    53.650] (**) Option "fd" "52"
[    53.650] (II) event11 - SteelSeries SteelSeries Rival 500 Gaming Mouse Consumer Control: device removed
[    53.883] (II) systemd-logind: got pause for 13:76
[    53.883] (II) systemd-logind: got pause for 13:77
[    53.883] (II) systemd-logind: got pause for 13:64
[    53.883] (II) systemd-logind: got pause for 13:73
[    53.883] (II) systemd-logind: got pause for 13:79
[    53.883] (II) systemd-logind: got pause for 13:78
[    53.883] (II) systemd-logind: got pause for 13:65
[    53.883] (II) systemd-logind: got pause for 13:75
[    53.883] (II) systemd-logind: got pause for 13:74
```

---

### Post by CatKiller on 2019-09-08
You're in good shape. You can see from the log that it's your xorg.conf that's *stopping* the multimonitor setup. Was it an auto-generated one? 

```
[    27.126] (==) Using config file: "/etc/X11/xorg.conf"
[    27.126] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.176] (==) ServerLayout "Layout0"
[    27.176] (**) |-->Screen "Screen0" (0)
[    27.176] (**) |   |-->Monitor "Monitor0"
[    27.189] (**) |   |-->Device "Device0"
[    27.189] (**) |-->Input Device "Keyboard0"
[    27.189] (**) |-->Input Device "Mouse0"
[    27.189] (**) Option "Xinerama" "0"
```

But both graphics cards and all the monitors seem to be successfully detected and configured.

```
[    28.550] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    28.551] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 980 Ti (GM200-A) at PCI:1:0:0 (GPU-0)
[    28.590] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): connected
[    28.590] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): Internal TMDS
[    28.590] (--) NVIDIA(GPU-0): Pioneer Electronic Corporation VSX-921 (DFP-1): 600.0 MHz maximum pixel clock
[    28.594] (II) NVIDIA(0): Validated MetaModes:
[    28.594] (II) NVIDIA(0):     "nvidia-auto-select+0+0"
[    28.594] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    28.837] (--) NVIDIA(0): Valid display device(s) on GPU-1 at PCI:2:0:0
[    28.860] (--) NVIDIA(GPU-1): HP x23LED (DFP-0): connected
[    28.860] (--) NVIDIA(GPU-1): HP x23LED (DFP-0): Internal TMDS
[    28.860] (--) NVIDIA(GPU-1): HP x23LED (DFP-0): 330.0 MHz maximum pixel clock
[    28.867] (--) NVIDIA(GPU-1): HP W2371d (DFP-3): connected
[    28.867] (--) NVIDIA(GPU-1): HP W2371d (DFP-3): Internal TMDS
[    28.867] (--) NVIDIA(GPU-1): HP W2371d (DFP-3): 330.0 MHz maximum pixel clock
[    28.887] (II) NVIDIA(GPU-1): NVIDIA GPU GeForce GTX 660 Ti (GK104) at PCI:2:0:0 (GPU-1)
[    29.050] (II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
```

Interestingly, you appear to have enough outputs to run all three monitors off the 980 Ti, which would make things easier. I'm not sure that the 660 Ti is bringing anything to the table.

You should have enough there to make a start, I think.

Edit: when you're reading the xorg.conf manpage or the nvidia readme it's worth remembering that the X11 protocol is over 30 years old; not everything that's in there is relevant any more. You'll only need to setup the structure of the thing and let most things be automatically handled. Just so that you aren't sitting there thinking, "what the heck is a RAMDAC?" or similar. Names and the relationship between one thing and another thing is what you're primarily interested in.

Edit 2: it's also worth remembering that *12 monitors and 12 sets of keyboard/mouse independently connected to one machine* and *12 GPUs and none of them used for display* are both perfectly sensible configurations of a Linux box. There just isn't the scope for a one-size-fits-all zero-configuration option. Whereas with Windows you can only have what Windows gives you.

---

### Post by xstrada2501 on 2019-09-08
> **CatKiller said:**
> You're in good shape. You can see from the log that it's your xorg.conf that's *stopping* the multimonitor setup. Was it an auto-generated one? 

Yes, but I have since deleted it and the old log files.  Rebooted, no problem.  New log files generated.

> But both graphics cards and all the monitors seem to be successfully detected and configured.

So why is the 660ti and my 23's still not showing up?

> Interestingly, you appear to have enough outputs to run all three monitors off the 980 Ti, which would make things easier. I'm not sure that the 660 Ti is bringing anything to the table.

That is true.  It has a DVI port and a bunch of display ports which would require me purchasing a DVI/Display Port adapter cable.  But that's not what I want.  I want my 660 working and displaying.  Which it is not, currently.

---

### Post by CatKiller on 2019-09-08
> **xstrada2501 said:**
> So why is the 660ti and my 23's still not showing up?
They are; they're right there in the log. But X doesn't know whether you want a different Screen for each monitor, one for each graphic card, one that covers all three (and whether that one uses Xinerama, TwinView, or something else entirely). You need to tell it what you want. It can autoconfigure one monitor for the primary display, which is how your BIOS is set up, because there's only really one way of doing that. Any other configuration relies on your choices.

---

### Post by xstrada2501 on 2019-09-08
Ok, so...  progress?

I went into XServer and enabled my screens.  40" screen 0 - absolute.  23" screens 1 & 2 - left and right.  Fresh xorg file for each config change to avoid copying or overlapping.  Both screens are now alive (yay!) - BUT - both are black, cursor is a cross and I cannot drag windows between displays.

Is this the point I enable xinerama and hope for the best or is this where mosaic comes into play?

---

### Post by CatKiller on 2019-09-08
> **xstrada2501 said:**
> Ok, so...  progress?

I went into XServer and enabled my screens.  40" screen 0 - absolute.  23" screens 1 & 2 - left and right.  Fresh xorg file for each config change to avoid copying or overlapping.  Both screens are now alive (yay!) - BUT - both are black, cursor is a cross and I cannot drag windows between displays.

Is this the point I enable xinerama and hope for the best or is this where mosaic comes into play?

Awesome. Not being able to drag windows between displays is a function of having them as separate screens: they are independent of each other as far as the window manager is concerned.

I think (although I'm hazy) that Xinerama required applications to be aware of it, and most weren't.

As far as I can tell, the nvidia default would be to have a Screen for each GPU, which in your case would mean that windows could be dragged from the right screen to the left, completely bypassing the one in the middle. Not what you want, but pretty funny.

I *think* that what you want is to have everything defined as one Screen, with a defined meta-mode of (edit: effectively) 5760×1080. It was a long time ago that I played with this stuff, and quite a bit has changed in the meantime. The documentation should specify the options that are available to you. 

As I recall, Xinerama was a bit iffy with applications that weren't aware of it, TwinView only works for one GPU, XRandR makes things a lot easier by being able to specify your own stuff (like custom resolutions and having things rotated), and Nvidia like to do their own thing that makes sense to them rather than what anyone else is doing.

I'm glad to hear you're making progress :)

Edit: Chapter 13 of the Nvidia readme is probably where you should be looking. It describes the syntax of having your meta-mode for the three monitors, and you can do all sorts of neat things where the resolution of the screen is different to the resolution of the monitor, and placed arbitrarily.

---

### Post by xstrada2501 on 2019-09-08
Ok, I'm stuck again.  This is my xorg.config with black 23" and cross cursor.

```
# nvidia-settings: X configuration file generated by nvidia-settings# nvidia-settings:  version 390.77  (buildd@lcy01-amd64-022)  Thu Sep  6 07:51:39 UTC 2018


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 0
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Pioneer Electronic Corporation VSX-921"
    HorizSync       14.0 - 70.0
    VertRefresh     48.0 - 62.0
    Option         "DPMS"
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP x23LED"
    HorizSync       24.0 - 83.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "HP W2371d"
    HorizSync       24.0 - 94.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 980 Ti"
    BusID          "PCI:1:0:0"
EndSection


Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection


Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DVI-I-1: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-3"
    Option         "metamodes" "DVI-D-0: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

I understand that since the displays are on separate gpu's and are stand alone xscreens window dragging might not work.  Although I'd prefer it to be otheerwise, that's ok.  I can live with that.

The next step is to get them actually displaying an image or a functioning screen.

Edit:  Xinerama is not an option as I tried that, and got a login bootloop.  Had to recovery in and delete the xorg file from root.  At least I learned how to do that.  The pipeline thing doesn't work either and I have no option for Twinview.
        So, yeh.  I'm stuck.

---

### Post by CatKiller on 2019-09-08
So interestingly Nvidia changed the chapter numbering between the version of the readme I linked to earlier and the version I was having a look at on my phone. So, for the version I linked to before, it's [Chapter 12: Configuring Multiple Monitors On One X Screen]("http://us.download.nvidia.com/XFree86/Linux-x86_64/430.40/README/configtwinview.html"). So, apologies if that caused any confusion.

With your login issue, desktop environments store their own configuration for the desktop resolution in ~/.config/monitors.xml. If the configuration changes suddenly (because, for example, the monitor has disappeared and been replaced by one three times the size that uses Xinerama) things can get confused. Since you're using X and Nvidia to fiddle around with the resolution you don't actually care what that file says: it can safely be deleted if it's causing trouble, and it can be recreated at will.

Just as a sanity check: you are aware that the Nvidia driver comes with its own configuration tool in addition to Gnome's Monitor settings, yes? The Monitors setting is quite limited compared to what you're trying to achieve.

Your xorg.conf has a bunch of stuff that you don't need to specify; I guess because it came from nvidia-xconfig initially. And it's in a weird order, for the same reason. So all the module stuff and input stuff you won't need (and these days you can get away with having just snippets in xorg.conf.d to configure those rather than having a full xorg.conf, which is nice: I no longer need the whole shebang just to turn off mouse acceleration). The names are also very much machine-generated, which makes it hard to read. It doesn't actually matter what you call things, as long as it's consistent.

So something like
```

Section "Monitor"
    Identifier     "VSX-921"
EndSection

Section "Monitor"
    Identifier     "x23LED"
EndSection

Section "Monitor"
    Identifier     "W2371d"
EndSection

Section "Device"
    Identifier     "980-DFP-1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 980 Ti"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "660-DFP-0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "660-DFP-3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 660 Ti"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection
```

Should be fine for those bits. That leaves just the Screen and (possible) ServerLayout sections that tie them all together.

Using a meta-mode to span all three monitors is something that Nvidia call "Dynamic TwinView" because marketing. It's possible that you won't even need to define a Screen Section: you might be able to put the MetaMode in the Device Sections. There is also the option of having a Modes Section with the same structure as the other Sections: Section "Modes" followed by what you want in it followed by EndSection. It's also possible that because the GPUs are dissimilar and aren't connected by SLI, it won't work at all. We'll see :)

As far as I can tell, the MetaMode you're after would be something like

```
   Option    "MetaModes"    "GPU-1.DFP-0: nvidia-auto-select, GPU-0.DFP-1: nvidia-auto-select, GPU-1.DFP-3: nvidia-auto-select"
```

I need to stop for now, but I'll check back with how you're doing later.

---

### Post by xstrada2501 on 2019-09-09
CatKiller, thankyou so much for all your help, expertise and suggestions.

I wish I had better news, but I've decided to give up.  I just cannot get any configuration to behave and my 980 has been throwing hissy fits and flickering over to a magenta screen.  Over heating issue?  Maybe.  It has happened before but it's so random and I thought I had it figured out after a BIOS update pre all this, but all this tinkering has caused it to happen again.

I'll go back to my previous statement of not wanting to poke this bear.

I don't game on Ubuntu, so the need for the extra screens is not really there.  Plus I can plug one of my monitors into the DVI socket on my 980 with no issues if I need another monitor - which is frequently.  I just wish I didn't have to do that.

Again, thankyou so very, very much for all you have done.

---

### Post by CatKiller on 2019-09-09
No problem; happy to help, and I expect that you've got a lot more confident with tinkering with your machine with this process even though you ultimately didn't manage to scratch the particular itch.

I do have some longer term good news for you, though.

When Optimus - pairing integrated Intel graphics with Nvidia graphics in laptops - first appeared, Nvidia weren't at all interested in making it work on Linux; they said it was Windows-only technology. With the proprietary nature of the driver, and the state of both X and OpenGL at the time the community came up with their own solutions, but they were a bit clunky. However, with the creation of Vulkan and Wayland, and using GPUs for computation, and developments in DirectX (which steers Nvidia's driver development, even on Linux) they're revisiting that decision. Work is being done on no longer treating GPUs as framebuffers to be written into, but instead being able to add generic combinations of graphics cards in more arbitrary configurations. You probably saw references to MultiGpu in the documentation and the logs: that's what that's about.

So what you've been trying to do here - addressing two quite different GPUs at the same time - should be quite a lot easier in the future if you decide to revisit it.

---

### Post by pannerrammer on 2019-10-07
Hi. I have 2 boxes, one running 16.04 the other 18.04. Both connected to 2 iiyama E2482HD monitors (via kvm). Both setups arranged so I have 3840px wide dual-screen; both monitors appeared in both systems on installation (or connection in the case of 16.04 box) without me doing anything clever. Saturday I did a fresh install of 18.04 on the 'old' 16.04 box. It has an nvidia gpu and radeon pci-e card, and only the gpu-connected monitor appeared. 
Following this thread, I established both were being detected. 
The old 16.04 had no /etc/X11/xorg.conf but a ~/.config/monitors.xml file identifying 2 devices. Copied this across, reboot, no joy.
So I went into the pc bios and changed the video boot/preference order (ie. pci-e first). And both monitors are up and running. 
Not sure if this helps, but it solved my issue

---

