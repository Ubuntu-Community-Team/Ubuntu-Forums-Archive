---
title: "Ubuntu 10.10 and Dell XPS L401X nVidia GeForce GT 420M Driver Issues"
date: 2010-11-30
forum: Hardware
---

### Post by yoshtamagosh on 2010-11-30
Hello!

I'm new to Ubuntu and I'm trying to attach an external monitor to my laptop. 

With all the bugs reported on the web there appears to be a driver issue with nVidia however none of those reports had a working solution for me. 

So... to spill the beans:

Configuration:
- Ubuntu 10.10
- nVidia GeForce GT 420M 

Issue:
- Get "Fatal server error: no screens found" after I run "nvidia-xconfig"
- If I delete the xorg.conf that "nvidia-xconfig" generates then I can do "startx" to get back to X but NVIDIA Settings reports no driver detected

Thank you very much in advance!

---

### Post by PhilEvans on 2010-12-02
I have the same issue, and it seems that the current Ubuntu package of nvidia drivers does not support the 420M -- you can check this by installing the drivers then doing 
zless /usr/share/doc/nvidia-current/README.txt.gz -- towards the end is a list of supported cards.

However, if you go to the nvidia website you can download linux drivers for this card, and indeed there is a page on the ubuntuforums walking through installation of this:

[http://georgia.ubuntuforums.org/showthread.php?t=1579444](http://georgia.ubuntuforums.org/showthread.php?t=1579444)

---

### Post by yoshtamagosh on 2010-12-02
Yeah, I've tried that and it doesn't work, same issue.

---

### Post by themadukrainian on 2010-12-02
To whomever handles this thread, could problem be corrected by installing current Nvidia drivers in 10.4 before upgrading to 10.10? I just ran into this Nvidia problem today myself. Installed 10.4 onto blank drive and then immediately did upgrade to 10.10. Right now I am reloading 10.4 on the same drive, full wipe, starting over. I will try loading the current Nvidia driver on 10.4 and then perform the upgrade to 10.10 and will repost my results.:idea:

---

### Post by yoshtamagosh on 2010-12-02
Thank you please let me know if that works. 

I've tried so many things at this point I've lost track but I think the drivers weren't working on 10.04 either.

---

### Post by akand074 on 2010-12-02
Did you guy's install your proprietary Nvidia graphics drivers after you installed Ubuntu? To do so you can go to System > Administration > Additional Drivers. Otherwise, the graphics drivers shown in Ubuntu are not always the most up to date. [Here]("http://www.nvidia.com/object/linux-display-amd64-260.19.21-driver.html") is the most up to date drivers for your graphics card from NVidia.

---

### Post by yoshtamagosh on 2010-12-02
Yes sir, the Nvidia graphics drivers were installed after Ubuntu. I have the 32-bit version of Ubuntu setup and tried the 32-bit driver.

Should I try the 64-bit?

---

### Post by akand074 on 2010-12-02
> **yoshtamagosh said:**
> Yes sir, the Nvidia graphics drivers were installed after Ubuntu. I have the 32-bit version of Ubuntu setup and tried the 32-bit driver.

Should I try the 64-bit?

No not unless you have 64 bit Ubuntu installed on a system that supports 64 bit. I haven't ever plugged a monitor into my laptop but you should be able to set it up by going to System > Administration > NVidia XServer Settings. Plug in your monitor and select "Detect Displays" from the X Server Display Configurations. Your on your own from there but if it recognizes it you should be good from there.

---

### Post by yoshtamagosh on 2010-12-02
That's the issue, when I go into NVidia XServer Settings it says 

'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file and restart the X server.'

And when I do that then I get the "No screens found" error and can't get back into X unless I delete the xorg.conf file that was created.

---

### Post by akand074 on 2010-12-02
> **yoshtamagosh said:**
> That's the issue, when I go into NVidia XServer Settings it says 

'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file and restart the X server.'

And when I do that then I get the "No screens found" error and can't get back into X unless I delete the xorg.conf file that was created.

Try going back to System > Administration > Additional Drivers. Uninstall the NVidia drivers. Restart your computer. Reinstall the NVidia drivers and restart again. The xorg configuration files should be automatically made. Mine looks like this:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

(/etc/X11/xorg.conf)

---

### Post by yoshtamagosh on 2010-12-02
My xorg.conf looks the exact same but when I restart it goes to Terminal and when I try "startx" I get the "No screens found".

---

### Post by akand074 on 2010-12-02
> **yoshtamagosh said:**
> My xorg.conf looks the exact same but when I restart it goes to Terminal and when I try "startx" I get the "No screens found".

Do you have both onboard and dedicated graphics? That could cause problems if they are both enabled. Try this command in the Terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

then

```
startx
```

---

### Post by yoshtamagosh on 2010-12-03
The sad reality is I can't afford anymore downtown, have to go back to Windows 7.

Thanks for all your help.

---

### Post by howtieatie on 2010-12-03
well i am also suffering for that

---

### Post by jsonder on 2010-12-03
How do I evaluate if there is an onboard video chip active?  Hardinfo shows I/O ports 2000-207f dedicated to an nVidia Corp. device {VGA controller}.

I don't see anything that looks like another video controller.

Hardware = Dell XPS L501X dual booting, win7 and Ubuntu 10.10 (64-bit).

---

### Post by esteban.feldman on 2010-12-04
Same problem here Dell XPS 14, any way to make this working?

---

### Post by -Null on 2010-12-11
Hi guys, I've been struggling with the same problem. I'm on a Dell XPS 14 equipped with an NVIDIA GeForce GT 420M. after some xorg.conf editing, reinstallation of drivers, and even reinstallation of Ubuntu, I was able to start X Server with no fatal error, but instead, experienced a blank screen after the Ubuntu splash. 

From what I've gathered from forum threads concerning this issue is that the problem involves NVIDIA's Optimus technology. Apparently a development team is being organized to tackle the issue ([https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)), so it may be only a matter of time. Here's hoping...

---

### Post by rfdparker2002 on 2010-12-11
Hey guys,

I've just happened to have ordered a new laptop (a Acer Aspire 5742G) which has an nVidia Geforce GT 420M - and just stumbled on this thread - from the looks of it you've tried the normal [propreitary] driver in the Ubuntu Lucid repos, as well as the newest driver from nVidia's site. Just a few things I was wondering:
[LIST]
[*]if anyone has tried getting the newest driver via the ["Ubuntu-X" PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") (which contains updated X and nVidia driver packages, amongst other stuff), and whether that was of any advanatge? (doing so from a 'fresh' install - aka after not having messed with xorg.conf - adding the PPA and refreshing repos before install the newest driver via 'Additional Drivers')
[*]whether this is issue is occurring when just using a laptop's integrated display (I am likely to be doing most of time), or just when trying to use an external display? (and via VGA and/or HDMI if so?)
[/LIST]

Thanks.

---

### Post by lfersim on 2010-12-17
I have the same problem here. I have a DELL XPS L501X with the same configuration. I have installed both, the latest [NVidia certified drivers 260.19.29]("http://www.nvidia.com/object/linux-display-amd64-260.19.29-driver.html") and the ones available in Ubuntu's repositories, and in both cases I have had the same result -- No display found --

---

### Post by malsmith3044 on 2011-01-05
I've spent this afternoon with my new Dell L401X with its NVIDIA 420M card.  Tried everything here - including activating, downloading and installing latest NVIDIA.com 64-bit drivers and I've also tried the Swat X PPA updates which also don't work.

No luck - in all cases, my startup hangs right after "Checking Battery State" when the X Server starts.  

I am willing to try any other suggestions including building sources etc.

My nvidia xorg.conf file is here:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.29  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Wed Dec  8 12:27:39 PST 2010

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

---

### Post by malsmith3044 on 2011-01-05
Not to load up on the thread - but here is the Xorg.0.log file on my most recent attempt using the nvidia drivers

```

[    50.291] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    50.295] X Protocol Version 11, Revision 0
[    50.296] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    50.297] Current Operating System: Linux malsmith-XPS-L401X 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[    50.298] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=062b519d-4b2b-47a4-9663-c5cdad265e20 ro single
[    50.300] Build Date: 16 September 2010  06:18:41PM
[    50.301] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    50.303] Current version of pixman: 0.18.4
[    50.304] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    50.307] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    50.311] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  5 17:03:59 2011
[    50.312] (==) Using config file: "/etc/X11/xorg.conf"
[    50.314] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    50.316] (==) ServerLayout "Layout0"
[    50.316] (**) |-->Screen "Screen0" (0)
[    50.316] (**) |   |-->Monitor "Monitor0"
[    50.316] (**) |   |-->Device "Device0"
[    50.316] (**) |-->Input Device "Keyboard0"
[    50.316] (**) |-->Input Device "Mouse0"
[    50.316] (==) Automatically adding devices
[    50.316] (==) Automatically enabling devices
[    50.316] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    50.316] 	Entry deleted from font path.
[    50.316] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    50.316] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    50.316] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    50.316] (WW) Disabling Keyboard0
[    50.316] (WW) Disabling Mouse0
[    50.316] (II) Loader magic: 0x7d0200
[    50.316] (II) Module ABI versions:
[    50.316] 	X.Org ANSI C Emulation: 0.4
[    50.316] 	X.Org Video Driver: 8.0
[    50.316] 	X.Org XInput driver : 11.0
[    50.316] 	X.Org Server Extension : 4.0
[    50.317] (--) PCI:*(0:0:2:0) 8086:0046:1028:0468 rev 24, Mem @ 0xfa400000/4194304, 0xb0000000/268435456, I/O @ 0x0000f080/8
[    50.317] (--) PCI: (0:1:0:0) 10de:0df1:1028:0468 rev 161, Mem @ 0xf9000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    50.317] (II) Open ACPI successful (/var/run/acpid.socket)
[    50.317] (II) LoadModule: "extmod"
[    50.319] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    50.319] (II) Module extmod: vendor="X.Org Foundation"
[    50.319] 	compiled for 1.9.0, module version = 1.0.0
[    50.319] 	Module class: X.Org Server Extension
[    50.319] 	ABI class: X.Org Server Extension, version 4.0
[    50.319] (II) Loading extension MIT-SCREEN-SAVER
[    50.319] (II) Loading extension XFree86-VidModeExtension
[    50.319] (II) Loading extension XFree86-DGA
[    50.319] (II) Loading extension DPMS
[    50.319] (II) Loading extension XVideo
[    50.319] (II) Loading extension XVideo-MotionCompensation
[    50.319] (II) Loading extension X-Resource
[    50.319] (II) LoadModule: "dbe"
[    50.319] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    50.319] (II) Module dbe: vendor="X.Org Foundation"
[    50.319] 	compiled for 1.9.0, module version = 1.0.0
[    50.319] 	Module class: X.Org Server Extension
[    50.319] 	ABI class: X.Org Server Extension, version 4.0
[    50.319] (II) Loading extension DOUBLE-BUFFER
[    50.319] (II) LoadModule: "glx"
[    50.319] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    50.393] (II) Module glx: vendor="NVIDIA Corporation"
[    50.394] 	compiled for 4.0.2, module version = 1.0.0
[    50.394] 	Module class: X.Org Server Extension
[    50.394] (II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
[    50.394] (II) Loading extension GLX
[    50.394] (II) LoadModule: "record"
[    50.394] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    50.394] (II) Module record: vendor="X.Org Foundation"
[    50.394] 	compiled for 1.9.0, module version = 1.13.0
[    50.394] 	Module class: X.Org Server Extension
[    50.394] 	ABI class: X.Org Server Extension, version 4.0
[    50.394] (II) Loading extension RECORD
[    50.394] (II) LoadModule: "dri"
[    50.394] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    50.395] (II) Module dri: vendor="X.Org Foundation"
[    50.395] 	compiled for 1.9.0, module version = 1.0.0
[    50.395] 	ABI class: X.Org Server Extension, version 4.0
[    50.395] (II) Loading extension XFree86-DRI
[    50.395] (II) LoadModule: "dri2"
[    50.395] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    50.395] (II) Module dri2: vendor="X.Org Foundation"
[    50.395] 	compiled for 1.9.0, module version = 1.2.0
[    50.395] 	ABI class: X.Org Server Extension, version 4.0
[    50.395] (II) Loading extension DRI2
[    50.395] (II) LoadModule: "nvidia"
[    50.395] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    50.401] (II) Module nvidia: vendor="NVIDIA Corporation"
[    50.402] 	compiled for 4.0.2, module version = 1.0.0
[    50.402] 	Module class: X.Org Video Driver
[    50.404] (II) NVIDIA dlloader X Driver  260.19.29  Wed Dec  8 12:10:14 PST 2010
[    50.404] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    50.404] (--) using VT number 7

[    50.406] (EE) No devices detected.
[    50.406] 
Fatal server error:
[    50.406] no screens found
[    50.406] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    50.406] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    50.406] 

```

---

### Post by rkmbinant_ on 2011-01-06
Hi there,

I followed the thread and I was just curious to ask whether running 10.10 relying only on intel HD chipset (without installing ANY nvidia drivers) worked so as to plug the laptop to an external monitor at 1080p.

I was planning to purchase a XPS 14 but then saw all the issues with nVidia Optimus tech. From this other thread [http://ubuntuforums.org/archive/index.php/t-1645074.html](http://ubuntuforums.org/archive/index.php/t-1645074.html) it seems that best thing to do, while waiting for some support, is dual boot with propietary OS to benefit from GT420M video card.

In any case, can any one confirm that you can still use 10.10 with intel's HD chipset and plug an external monitor at 1080p at ease?

Thx a lot. If I find anything regarding optimus tech support for linux I will post it here. Meanwhile; angry faces to nVidia...

Best,

---

### Post by fi2 on 2011-06-04
I found a detailed explanation here:

[http://ubuntuforums.org/showthread.php?t=1657660&highlight=nvidia+optimus]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=nvidia+optimus")

---

