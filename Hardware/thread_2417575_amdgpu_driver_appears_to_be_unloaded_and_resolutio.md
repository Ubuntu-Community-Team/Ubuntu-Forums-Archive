---
title: "amdgpu driver appears to be unloaded and resolution is stuck at 1024x768@76Hz"
date: 2019-04-24
forum: Hardware
---

### Post by ragstosacs on 2019-04-24
Now a lot of people have this problem many of whom have the same device.```
inxi -Fzx
System:    Host: bhasker-Rev-1-0 Kernel: 5.0.9-050009-generic x86_64
           bits: 64 gcc: 8.3.0
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: LENOVO product: IdeaPad Y560 v: Rev 1.0 serial: N/A
           Mobo: Lenovo model: KL3 v: Rev 1.0 serial: N/A
           BIOS: LENOVO v: 30CN71WW date: 01/28/2011
Battery    BAT1: charge: 21.0 Wh 41.7% condition: 50.4/60.7 Wh (83%)
           model: SONY L09N6D16 status: Charging
CPU:       Quad core Intel Core i7 Q 740 (-MT-MCP-) 
           arch: Nehalem rev.5 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 13831
           clock speeds: max: 1734 MHz 1: 963 MHz 2: 956 MHz 3: 938 MHz
           4: 967 MHz 5: 937 MHz 6: 965 MHz 7: 967 MHz 8: 938 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5730 / 6570M]
           bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon,amdgpu)
           Resolution: 1024x768@76.00hz
           OpenGL: renderer: N/A version: N/A Direct Render: N/A
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 5 Series/3400 Series High Def. Audio
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k5.0.9-050009-generic
Network:   Card-1: Intel Centrino Wireless-N 1000 [Condor Peak]
           driver: iwlwifi bus-ID: 05:00.0
           IF: wlp5s0 state: up mac: <filter>
           Card-2: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe
           driver: tg3 v: 3.137 bus-ID: 09:00.0
           IF: enp9s0 state: down mac: <filter>
Drives:    HDD Total Size: 563.5GB (2.5% used)
           ID-1: /dev/sda model: RD size: 63.4GB
           ID-2: /dev/sdb model: WDC_WD5000BEVT size: 500.1GB
Partition: ID-1: / size: 58G used: 14G (25%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 67.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 242 Uptime: 37 min Memory: 1165.5/7906.5MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56

``` Two of the posts from 2017 and 2018
[https://ubuntuforums.org/showthread.php?t=2355643](https://ubuntuforums.org/showthread.php?t=2355643)
[https://ubuntuforums.org/showthread.php?t=2393156&p=13854118#post13854118](https://ubuntuforums.org/showthread.php?t=2393156&p=13854118#post13854118)

There is a page on Canonical's website can't remember the address right now but on that page I could find instructions to install the amdgpu driver and underneath these instructions there are names of a number of supported devices. This list does include my card under "REDWOOD"

---

### Post by him610 on 2019-04-24
> Graphics:  Card: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5730 / 6570M]
           ....  
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon,amdgpu)
Neither amdgpu or radeon driver are loaded.

---

### Post by ragstosacs on 2019-04-30
That was what I had said. That is the problem but hey thanks for noticing this and for trying to help by actually leaving a response

---

### Post by Autodave on 2019-04-30
What version of 'buntu are you running?  Was this a clean install or did you upgrade?

---

### Post by him610 on 2019-04-30
> **Autodave said:**
> What version of 'buntu are you running?  Was this a clean install or did you upgrade?
Yes, that is something I just noticed...
> System:    Host: bhasker-Rev-1-0 Kernel: 5.0.9-050009-generic x86_64
           bits: 64 gcc: 8.3.0
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.2 LTS

This is what mine looks like...
> System:    Host: x1910 Kernel: 5.0.0-13-generic x86_64 bits: 64 Desktop: Xfce 4.13.3 
           Distro: Ubuntu 19.10 (Eoan EANIMAL) 

Looks like an incomplete upgrade. Kernel 5+ does not belong with LTS 18.04+.

---

### Post by Yellow Pasque on 2019-05-02
> **him610 said:**
> Kernel 5+ does not belong with LTS 18.04+.

False. It's the updated HWE kernel from Ubuntu 19.04 (and it will be used in Ubuntu 18.04.3 point release): [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Kernel.2FSupport-1.A18.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#Kernel.2FSupport-1.A18.04.x_Ubuntu_Kernel_Support)

---

### Post by Yellow Pasque on 2019-05-02
> **ragstosacs said:**
> There is a page on Canonical's website can't remember the address right now but on that page I could find instructions to install the amdgpu driver and underneath these instructions there are names of a number of supported devices. This list does include my card under "REDWOOD"

Your GPU is based on Terascale2: [https://en.wikipedia.org/wiki/TeraScale_(microarchitecture)#TeraScale_2](https://en.wikipedia.org/wiki/TeraScale_(microarchitecture)#TeraScale_2)
It should use the 'radeon' kernel driver. AFAIK, amdgpu only supports GCN 1.0 (i.e. RadeonHD 7000 series) and later.

^That is not something you should have to worry about though. The radeon module should be automatically loaded and used by default. See what happens when you try to load it manually:
```
sudo modprobe -v radeon
```
Also, post a copy of /var/log/Xorg.0.log to see if it has any clues. Please use code tags as you did in your initial post because it's a lot of text.

---

### Post by ragstosacs on 2019-05-12
I'm sorry for the delayed response but I didn't receive any notification for this (email or otherwise) even though I get all kinds of notifications for far less crucial private messages. I was only keeping an eye on this by arriving at this page by occasionally googling/duckduckgoing my username and I didn't expect to see any actual responses so it is nice to see 3 people here.
```
sudo modprobe -v radeon
```

I think someone else had given me the same advice but I've tried it again and it made the screen go _**OFF **_  not blank/black but off. Whenever the screen should go OFF after a few minutes of inactivity it  goes black instead and it resumes back to normal when it should. The screen never goes off unless I were to suspend the system in which case it never comes back on again without rebooting. 
Should I try:```
sudo modprobe -v amdgpu
```

?


Are you sure it doesn't support [SIZE=2]evergreen[/SIZE]? The installation media only works with ```
nomodeset
``` I have tried installing fatgog64, lUbuntu and Ubuntu 16.04, 16.10, 17.10 and now 18.04. A really old version of SLAX is the only one that works perfectly right-away without installing any drivers and it probably uses a really old version of an x-Org driver. With anything newer I have to use[SIZE=4] _**nomodeset**_[SIZE=2] but everything works perfectly with SLAX and it's older version of a preinstalled driver so I think this is just an issue with a newer driver that came about years ago. So far it seems to have been neglected.

I had talked about this in response to that other post. I could load up that old version of SLAX right now to tell you guys more about the old open-source driver which actually works perfectly. Should I do that? I could even get more info on what else is different in with older versions of everything. It only works in a live session so I won't be altering anything in my current installation. Do you think that information would help in anyway?
[/SIZE][/SIZE]

---

### Post by ragstosacs on 2019-05-12
This was the list that I was referring to: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
The little green tick was the reason why I had any hope of getting it to work with Ubuntu 16 but I couldn't even get the keyboard to work with nomodeset.



[https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)
[https://llvm.org/docs/AMDGPUUsage.html](https://llvm.org/docs/AMDGPUUsage.html)

---

### Post by ragstosacs on 2019-05-14
I've captured three screenshots from slax anyway. I would have used this instead of Ubuntu if I could install it and if it weren't so outdated. Here's the Xorg log also from slax:```
[    38.821] 
X.Org X Server 1.13.2
Release Date: 2013-01-24
[    38.824] X Protocol Version 11, Revision 0
[    38.825] Build Operating System: Slackware 14.0 Slackware Linux Project
[    38.827] Current Operating System: Linux slax 3.8.2 #1 SMP Tue Mar 12 03:43:27 AKDT 2013 x86_64
[    38.829] Kernel command line: 

```

It was too long so I had to remove most of it this response was really about screenshots though.

---

### Post by ragstosacs on 2019-05-14
> **Yellow Pasque said:**
> Also, post a copy of /var/log/Xorg.0.log to see if it has any clues. Please use code tags as you did in your initial post because it's a lot of text.

here it is in chunks:```
[     7.773] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[     7.773] X Protocol Version 11, Revision 0
[     7.773] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[     7.773] Current Operating System: Linux bhasker-Rev-1-0 5.0.9-050009-generic #201904200830 SMP Sat Apr 20 08:32:44 UTC 2019 x86_64
[     7.773] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.0.9-050009-generic root=UUID=75569eec-99ab-43a0-8442-69775e13479d ro quiet splash radeon.modeset=1 vt.handoff=1
[     7.773] Build Date: 25 October 2018  04:11:27PM
[     7.773] xorg-server 2:1.19.6-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[     7.773] Current version of pixman: 0.34.0
[     7.773]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     7.773] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.773] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 14 17:57:25 2019
[     7.774] (==) Using config file: "/etc/X11/xorg.conf"
[     7.774] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.777] (==) No Layout section.  Using the first Screen section.
[     7.777] (==) No screen section available. Using defaults.
[     7.777] (**) |-->Screen "Default Screen Section" (0)
[     7.777] (**) |   |-->Monitor "<default monitor>"
[     7.778] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[     7.778] (**) |   |-->Device "AMDGPU"
[     7.778] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     7.778] (==) Automatically adding devices
[     7.778] (==) Automatically enabling devices
[     7.778] (==) Automatically adding GPU devices
[     7.778] (==) Automatically binding GPU devices
[     7.778] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     7.785] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.785]     Entry deleted from font path.
[     7.785] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.785]     Entry deleted from font path.
[     7.785] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.785]     Entry deleted from font path.
[     7.788] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.788]     Entry deleted from font path.
[     7.788] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.788]     Entry deleted from font path.
[     7.788] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     7.788] (**) ModulePath set to "/opt/amdgpu-pro/lib/xorg/modules,/opt/amdgpu/lib/xorg/modules,/usr/lib/xorg/modules"
[     7.788] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.789] (II) Loader magic: 0x5629208e9020
[     7.789] (II) Module ABI versions:
[     7.789]     X.Org ANSI C Emulation: 0.4
[     7.789]     X.Org Video Driver: 23.0
[     7.789]     X.Org XInput driver : 24.1
[     7.789]     X.Org Server Extension : 10.0
[     7.790] (++) using VT number 7

[     7.790] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     7.796] (--) PCI:*(0:1:0:0) 1002:68c0:17aa:3927 rev 0, Mem @ 0xd0000000/268435456, 0xe8400000/131072, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[     7.796] (II) LoadModule: "glx"
[     7.798] (II) Loading /opt/amdgpu-pro/lib/xorg/modules/extensions/libglx.so
[     7.819] (II) Module glx: vendor="X.Org Foundation"
[     7.819]     compiled for 1.19.0, module version = 1.0.0
[     7.819]     ABI class: X.Org Server Extension, version 10.0
[     7.819] (II) LoadModule: "amdgpu"
[     7.820] (II) Loading /opt/amdgpu/lib/xorg/modules/drivers/amdgpu_drv.so
[     7.824] (II) Module amdgpu: vendor="X.Org Foundation"
[     7.824]     compiled for 1.19.6, module version = 18.0.99
[     7.824]     Module class: X.Org Video Driver
[     7.824]     ABI class: X.Org Video Driver, version 23.0
[     7.824] (II) AMDGPU: Driver for AMD Radeon:
    All GPUs supported by the amdgpu kernel driver
[     7.943] (II) AMDGPU(0): [KMS] drm report modesetting isn't supported.
[     7.943] (EE) Screen 0 deleted because of no matching config section.
[     7.943] (II) UnloadModule: "amdgpu"
[     7.943] (EE) Device(s) detected, but none match those in the config file.
[     7.943] (==) Matched ati as autoconfigured driver 0
[     7.943] (==) Matched modesetting as autoconfigured driver 1
[     7.943] (==) Matched fbdev as autoconfigured driver 2
[     7.943] (==) Matched vesa as autoconfigured driver 3
[     7.943] (==) Assigned the driver to the xf86ConfigLayout
[     7.943] (II) LoadModule: "ati"
[     7.947] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     7.948] (II) Module ati: vendor="X.Org Foundation"
[     7.948]     compiled for 1.19.6, module version = 19.0.1
[     7.948]     Module class: X.Org Video Driver
[     7.948]     ABI class: X.Org Video Driver, version 23.0
[     8.031] (II) LoadModule: "radeon"
[     8.031] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     8.046] (II) Module radeon: vendor="X.Org Foundation"
[     8.046]     compiled for 1.19.6, module version = 19.0.1
[     8.046]     Module class: X.Org Video Driver
[     8.046]     ABI class: X.Org Video Driver, version 23.0
[     8.046] (II) LoadModule: "modesetting"
[     8.046] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     8.049] (II) Module modesetting: vendor="X.Org Foundation"
[     8.049]     compiled for 1.19.6, module version = 1.19.6
[     8.049]     Module class: X.Org Video Driver
[     8.049]     ABI class: X.Org Video Driver, version 23.0
[     8.049] (II) LoadModule: "fbdev"
[     8.049] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     8.051] (II) Module fbdev: vendor="X.Org Foundation"
[     8.051]     compiled for 1.19.3, module version = 0.4.4
[     8.051]     Module class: X.Org Video Driver
[     8.051]     ABI class: X.Org Video Driver, version 23.0
[     8.051] (II) LoadModule: "vesa"
[     8.051] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     8.052] (II) Module vesa: vendor="X.Org Foundation"
[     8.052]     compiled for 1.19.3, module version = 2.3.4
[     8.052]     Module class: X.Org Video Driver
[     8.052]     ABI class: X.Org Video Driver, version 23.0
[     8.052] (II) AMDGPU: Driver for AMD Radeon:
    All GPUs supported by the amdgpu kernel driver
[     8.052] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
    ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI FireGL V3400, ATI Mobility FireGL V5250,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[     8.057] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     8.057] (II) FBDEV: driver for framebuffer: fbdev
[     8.057] (II) VESA: driver for VESA chipsets: vesa
[     8.058] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     8.058] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[     8.059] (II) [KMS] drm report modesetting isn't supported.
[     8.059] (EE) open /dev/dri/card0: No such file or directory
[     8.059] (WW) Falling back to old probe method for modesetting
[     8.059] (EE) open /dev/dri/card0: No such file or directory
[     8.059] (II) Loading sub module "fbdevhw"
[     8.059] (II) LoadModule: "fbdevhw"
[     8.059] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     8.060] (II) Module fbdevhw: vendor="X.Org Foundation"
[     8.060]     compiled for 1.19.6, module version = 0.0.2
[     8.060]     ABI class: X.Org Video Driver, version 23.0
[     8.061] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     8.061] (II) FBDEV(2): using default device
[     8.061] (WW) Falling back to old probe method for vesa
[     8.061] (EE) Screen 0 deleted because of no matching config section.
[     8.061] (II) UnloadModule: "radeon"
[     8.061] (EE) Screen 0 deleted because of no matching config section.
[     8.061] (II) UnloadModule: "modesetting"
[     8.061] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     8.061] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     8.061] (==) FBDEV(0): RGB weight 888
[     8.061] (==) FBDEV(0): Default visual is TrueColor
[     8.061] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.061] (II) FBDEV(0): hardware: VESA VGA (video memory: 3072kB)
[     8.061] (II) FBDEV(0): checking modes against framebuffer device...
[     8.061] (II) FBDEV(0): checking modes against monitor...
[     8.061] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[     8.061] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[     8.061] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[     8.061] (==) FBDEV(0): DPI set to (96, 96)
[     8.061] (II) Loading sub module "fb"
[     8.061] (II) LoadModule: "fb"
[     8.061] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.063] (II) Module fb: vendor="X.Org Foundation"
[     8.063]     compiled for 1.19.6, module version = 1.0.0
[     8.063]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.063] (**) FBDEV(0): using shadow framebuffer
[     8.063] (II) Loading sub module "shadow"
[     8.063] (II) LoadModule: "shadow"
[     8.063] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     8.064] (II) Module shadow: vendor="X.Org Foundation"
[     8.064]     compiled for 1.19.6, module version = 1.1.0
[     8.064]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.064] (II) UnloadModule: "vesa"
[     8.064] (II) Unloading vesa
[     8.064] (==) Depth 24 pixmap format is 32 bpp
[     8.065] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     8.068] (==) FBDEV(0): Backing store enabled
[     8.069] (==) FBDEV(0): DPMS enabled
[     8.070] (==) RandR enabled
[     8.076] (II) SELinux: Disabled on system
[     8.077] (II) AIGLX: Screen 0 is not DRI2 capable
[     8.077] (EE) AIGLX: reverting to software rendering
[     8.194] (EE) AIGLX error: amdgpu does not export required DRI extension
[     8.210] (EE) GLX: could not load software renderer
[     8.210] (II) GLX: no usable GL providers found for screen 0
[     8.285] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     8.285] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     8.285] (II) LoadModule: "libinput"
[     8.286] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     8.292] (II) Module libinput: vendor="X.Org Foundation"
[     8.292]     compiled for 1.19.6, module version = 0.27.1
[     8.292]     Module class: X.Org XInput Driver
[     8.292]     ABI class: X.Org XInput driver, version 24.1
[     8.292] (II) Using input driver 'libinput' for 'Power Button'
[     8.292] (**) Power Button: always reports core events
[     8.292] (**) Option "Device" "/dev/input/event3"
[     8.293] (**) Option "_source" "server/udev"
[     8.293] (II) event3  - Power Button: is tagged by udev as: Keyboard
[     8.293] (II) event3  - Power Button: device is a keyboard
[     8.293] (II) event3  - Power Button: device removed
[     8.312] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     8.312] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     8.312] (**) Option "xkb_model" "pc105"
[     8.312] (**) Option "xkb_layout" "us"
[     8.313] (II) event3  - Power Button: is tagged by udev as: Keyboard
[     8.313] (II) event3  - Power Button: device is a keyboard
[     8.313] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     8.313] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[     8.313] (II) Using input driver 'libinput' for 'Video Bus'
[     8.313] (**) Video Bus: always reports core events
[     8.313] (**) Option "Device" "/dev/input/event5"
[     8.313] (**) Option "_source" "server/udev"
[     8.314] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[     8.314] (II) event5  - Video Bus: device is a keyboard
[     8.314] (II) event5  - Video Bus: device removed
[     8.336] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input8/event5"
[     8.336] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     8.336] (**) Option "xkb_model" "pc105"
[     8.336] (**) Option "xkb_layout" "us"
[     8.337] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[     8.337] (II) event5  - Video Bus: device is a keyboard
[     8.337] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.337] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     8.337] (II) Using input driver 'libinput' for 'Power Button'
[     8.337] (**) Power Button: always reports core events
[     8.337] (**) Option "Device" "/dev/input/event1"
[     8.337] (**) Option "_source" "server/udev"
[     8.338] (II) event1  - Power Button: is tagged by udev as: Keyboard
[     8.338] (II) event1  - Power Button: device is a keyboard
[     8.338] (II) event1  - Power Button: device removed
[     8.360] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     8.360] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     8.360] (**) Option "xkb_model" "pc105"
[     8.360] (**) Option "xkb_layout" "us"
[     8.360] (II) event1  - Power Button: is tagged by udev as: Keyboard
[     8.360] (II) event1  - Power Button: device is a keyboard
[     8.361] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[     8.361] (II) No input driver specified, ignoring this device.
[     8.361] (II) This device may have been added with another device file.
[     8.361] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[     8.361] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[     8.361] (II) Using input driver 'libinput' for 'Sleep Button'
[     8.361] (**) Sleep Button: always reports core events
[     8.361] (**) Option "Device" "/dev/input/event2"
[     8.361] (**) Option "_source" "server/udev"
[     8.362] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[     8.362] (II) event2  - Sleep Button: device is a keyboard
[     8.362] (II) event2  - Sleep Button: device removed
[     8.380] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[     8.380] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     8.380] (**) Option "xkb_model" "pc105"
[     8.380] (**) Option "xkb_layout" "us"
[     8.380] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[     8.380] (II) event2  - Sleep Button: device is a keyboard
[     8.381] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[     8.381] (II) No input driver specified, ignoring this device.
[     8.381] (II) This device may have been added with another device file.
[     8.381] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event10)
[     8.381] (II) No input driver specified, ignoring this device.
[     8.381] (II) This device may have been added with another device file.
[     8.381] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event11)
[     8.382] (II) No input driver specified, ignoring this device.
[     8.382] (II) This device may have been added with another device file.
[     8.382] (II) config/udev: Adding input device Lenovo EasyCamera: Lenovo EasyC (/dev/input/event12)
[     8.382] (**) Lenovo EasyCamera: Lenovo EasyC: Applying InputClass "libinput keyboard catchall"
[     8.382] (II) Using input driver 'libinput' for 'Lenovo EasyCamera: Lenovo EasyC'
[     8.382] (**) Lenovo EasyCamera: Lenovo EasyC: always reports core events
[     8.382] (**) Option "Device" "/dev/input/event12"
[     8.382] (**) Option "_source" "server/udev"
[     8.383] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: is tagged by udev as: Keyboard
[     8.383] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device is a keyboard
[     8.383] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device removed
[     8.420] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input19/event12"
[     8.420] (II) XINPUT: Adding extended input device "Lenovo EasyCamera: Lenovo EasyC" (type: KEYBOARD, id 10)
[     8.420] (**) Option "xkb_model" "pc105"
[     8.420] (**) Option "xkb_layout" "us"
[     8.420] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: is tagged by udev as: Keyboard
[     8.420] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device is a keyboard
[     8.421] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[     8.421] (**) Ideapad extra buttons: Applying InputClass "libinput keyboard catchall"
[     8.421] (II) Using input driver 'libinput' for 'Ideapad extra buttons'
[     8.421] (**) Ideapad extra buttons: always reports core events
[     8.421] (**) Option "Device" "/dev/input/event8"
[     8.421] (**) Option "_source" "server/udev"
[     8.421] (II) event8  - Ideapad extra buttons: is tagged by udev as: Keyboard
[     8.421] (II) event8  - Ideapad extra buttons: device is a keyboard
[     8.421] (II) event8  - Ideapad extra buttons: device removed
[     8.444] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input15/event8"
[     8.444] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 11)
[     8.444] (**) Option "xkb_model" "pc105"
[     8.444] (**) Option "xkb_layout" "us"
[     8.445] (II) event8  - Ideapad extra buttons: is tagged by udev as: Keyboard
[     8.445] (II) event8  - Ideapad extra buttons: device is a keyboard
[     8.445] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     8.445] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[     8.445] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[     8.445] (**) AT Translated Set 2 keyboard: always reports core events
[     8.445] (**) Option "Device" "/dev/input/event4"
[     8.445] (**) Option "_source" "server/udev"
[     8.446] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[     8.446] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[     8.446] (II) event4  - AT Translated Set 2 keyboard: device removed
[     8.464] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     8.464] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[     8.464] (**) Option "xkb_model" "pc105"
[     8.464] (**) Option "xkb_layout" "us"
[     8.464] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[     8.464] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[     8.465] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[     8.465] (**) PS/2 Generic Mouse: Applying InputClass "libinput pointer catchall"
[     8.465] (II) Using input driver 'libinput' for 'PS/2 Generic Mouse'
[     8.465] (**) PS/2 Generic Mouse: always reports core events
[     8.465] (**) Option "Device" "/dev/input/event7"
[     8.465] (**) Option "_source" "server/udev"
[     8.465] (II) event7  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[     8.465] (II) event7  - PS/2 Generic Mouse: device is a pointer
[     8.465] (II) event7  - PS/2 Generic Mouse: device removed
[     8.508] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio3/input/input14/event7"
[     8.508] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 13)
[     8.508] (**) Option "AccelerationScheme" "none"
[     8.508] (**) PS/2 Generic Mouse: (accel) selected scheme none/0
[     8.508] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[     8.508] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[     8.509] (II) event7  - PS/2 Generic Mouse: is tagged by udev as: Mouse
[     8.509] (II) event7  - PS/2 Generic Mouse: device is a pointer
[     8.509] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
[     8.509] (II) No input driver specified, ignoring this device.
[     8.509] (II) This device may have been added with another device file.
[     8.510] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[     8.510] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[     8.510] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     8.510] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     8.510] (II) LoadModule: "synaptics"
[     8.510] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     8.511] (II) Module synaptics: vendor="X.Org Foundation"
[     8.511]     compiled for 1.19.3, module version = 1.9.0
[     8.511]     Module class: X.Org XInput Driver
[     8.511]     ABI class: X.Org XInput driver, version 24.1
[     8.511] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     8.511] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     8.511] (**) Option "Device" "/dev/input/event6"
[     8.540] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5512 (res 42)
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4714 (res 66)
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     8.540] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     8.540] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     8.592] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event6"
[     8.592] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[     8.592] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     8.592] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     8.592] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[     8.592] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     8.592] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     8.592] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     8.592] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     8.592] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     8.593] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     8.593] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     8.630] (II) config/udev: removing device Lenovo EasyCamera: Lenovo EasyC
[     8.630] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device removed
[     8.676] (II) UnloadModule: "libinput"
[     8.676] (II) config/udev: Adding input device Lenovo EasyCamera: Lenovo EasyC (/dev/input/event12)
[     8.676] (**) Lenovo EasyCamera: Lenovo EasyC: Applying InputClass "libinput keyboard catchall"
[     8.676] (II) Using input driver 'libinput' for 'Lenovo EasyCamera: Lenovo EasyC'
[     8.676] (**) Lenovo EasyCamera: Lenovo EasyC: always reports core events
[     8.676] (**) Option "Device" "/dev/input/event12"
[     8.676] (**) Option "_source" "server/udev"
[     8.677] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: is tagged by udev as: Keyboard
[     8.677] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device is a keyboard
[     8.677] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device removed
[     8.720] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input19/event12"
[     8.720] (II) XINPUT: Adding extended input device "Lenovo EasyCamera: Lenovo EasyC" (type: KEYBOARD, id 10)
[     8.720] (**) Option "xkb_model" "pc105"
[     8.720] (**) Option "xkb_layout" "us"
[     8.720] (WW) Option "xkb_variant" requires a string value
[     8.720] (WW) Option "xkb_options" requires a string value
[     8.721] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: is tagged by udev as: Keyboard
[     8.721] (II) event12 - Lenovo EasyCamera: Lenovo EasyC: device is a keyboard

```

---

