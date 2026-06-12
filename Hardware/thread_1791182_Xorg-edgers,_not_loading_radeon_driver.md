---
title: "Xorg-edgers, not loading radeon driver?"
date: 2011-06-26
forum: Hardware
---

### Post by mikrogroove on 2011-06-26
I'm trying to get Xorg edge with the Radeon KMS (Gallium?) driver working under Karmic on a ThinkPad T43p with ATI Mobility FireGL V3200 (r300) graphics. I have added the Edgers PPA and installed the packages from there. X is working and (2D) performance seems quite good (full screen Flash video with no tearing for example), but I have a few question marks. I have tried to provide the relevant info below, please have a scan through and see if you can help me with any of the questions at the end. 

-------------------------------------------

In dmesg I see (abbreviated):

[   40.585334] [drm] Initialized drm 1.1.0 20060810
[   40.629476] [drm] radeon defaulting to kernel modesetting.
[   40.629477] [drm] radeon kernel modesetting enabled.
[   40.629496] radeon 0000:01:00.0: setting latency timer to 64
[   40.633408] [drm] radeon: Initializing kernel modesetting.
[   40.633437] [drm] register mmio base: 0xB0100000
[   40.633438] [drm] register mmio size: 65536
[   40.636198] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
...
[   40.637019] radeon 0000:01:00.0: irq 27 for MSI/MSI-X
[   40.637021] radeon 0000:01:00.0: radeon: using MSI.
[   40.637030] [drm] radeon: irq initialized.
...
[   40.640458] [drm] Loading R300 Microcode
[   40.640562] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
...
[   40.768124] fb1: radeondrmfb frame buffer device
[   40.768127] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0

-------------------------------------------

But GLX doesn't even try to use anything other than software rendering: 

$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so

Also:

$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

-------------------------------------------

And then I find in Xorg.1.log:

[  1119.658] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  1119.658] drmOpenDevice: node name is /dev/dri/card0
[  1119.658] drmOpenDevice: open result is 11, (OK)
[  1119.658] drmOpenByBusid: drmOpenMinor returns 11
[  1119.658] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[  1119.658] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  1119.659] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] This chipset requires a kernel module version of 1.17.0,
[dri] but the kernel reports a version of 2.0.0.[dri] If using legacy modesetting, upgrade your kernel.
[dri] If using kernel modesetting, make sure your module is
[dri] loaded prior to starting X, and that this driver was built
[dri] with support for KMS.
[dri] Disabling DRI.
[  1119.659] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[  1119.659] (II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
...
[  1120.695] (II) RADEON(0): Dynamic Power Management Disabled
[  1120.896] (WW) RADEON(0): Direct rendering disabled
...
[  1124.044] (II) AIGLX: Screen 0 is not DRI2 capable
[  1124.044] (II) AIGLX: Screen 0 is not DRI capable
[  1124.047] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[  1124.047] (II) GLX: Initialized DRISWRAST GL provider for screen 0

-------------------------------------------

Xorg & kernel version: 

$ Xorg -version
X.Org X Server 1.8.2
Release Date: 2010-07-01
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
Current Operating System: Linux iron 2.6.32-31-generic-phc #61~phc0-Ubuntu SMP Thu Apr 21 10:41:30 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-31-generic-phc root=/dev/mapper/iron-root ro quiet splash
Build Date: 08 July 2010  01:50:14AM
xorg-server 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2~lucid (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.21.4

-------------------------------------------

In /usr/lib/dri I have (amongst others): 

swrast_dri.so
radeon_dri.so
r300c_dri.so
r300_dri.so
nouveau_dri.so
fglrx_dri.so

Sidenote - see the fglrx driver which is there despite not having the official driver installed: 

$ sudo apt-get remove --purge fglrx
Package fglrx is not installed, so not removed

(I also have the ATI Catalyst Control Center which also cannot be removed through Synaptic)
 
-------------------------------------------

Questions: 

- Why is GLX not trying to load one of the Radeon drivers (radeon_dri.so, r300_dri.so, etc)?
- "Make sure your module is loaded prior to starting X" - yes, but how?
- It looks to me as if KMS is enabled and working, but how do I set dynpm/dynclks now that I no longer have an xorg.conf? 
- How do I clean my system of any remnants of the fglrx driver (I think it was preinstalled by Xubuntu)? 

I am primarily interested in achieving two things: LOW power consumption and decent 2D performance. It would seem I have the latter so I'm not too worried about the GLX issue (I don't play 3D games and only use 3D productivity software for very simple things), but enabling the power management features of my chip would be great. 


Any help much appreciated!

---

### Post by Yellow Pasque on 2011-06-26
First, make sure you uninstall fglrx:
```
sudo sh /etc/ati/fglrx-uninstall.sh
```
I think your other questions are answered here:
[http://www.x.org/wiki/radeonBuildHowTo#Checkifradeon-KMSisenabledbeforeXisstarted](http://www.x.org/wiki/radeonBuildHowTo#Checkifradeon-KMSisenabledbeforeXisstarted)
> but how do I set dynpm/dynclks now that I no longer have an xorg.conf? 
You can use the method suggested by the above link, but you can also create an xorg.conf.
```
gksu gedit /etc/X11/xorg.conf
```
Here's a skeleton example; add what you want:
```

Section "Monitor"
    Identifier     "Monitor0"
EndSection

Section "Device"
    Identifier     "Device0"
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

### Post by mikrogroove on 2011-06-26
Many thanks for a helpful reply! 

> **Temüjin said:**
> First, make sure you uninstall fglrx:
```
sudo sh /etc/ati/fglrx-uninstall.sh
```

Oddly, I do not have the uninstall script for fglrx:

/etc/ati/$ ls:
signature
logo_mask.xbm.example
logo.xbm.example
inst_path_override
inst_path_default
control
authatieventsd.sh
atiogl.xml
amdpcsdb.default
amdpcsdb

> **Temüjin said:**
> I think your other questions are answered here:
[http://www.x.org/wiki/radeonBuildHowTo#Checkifradeon-KMSisenabledbeforeXisstarted](http://www.x.org/wiki/radeonBuildHowTo#Checkifradeon-KMSisenabledbeforeXisstarted)

I added GRUB_CMDLINE_LINUX="radeon.modeset=1" to the end of my Grub default, rebuilt Grub and rebooted. Now I get in Xorg log: 

[    35.826] (II) Primary Device is: PCI 01@00:00:0
[    35.826] (II) [KMS] drm report modesetting isn't supported.
[    35.826] (WW) Falling back to old probe method for vesa
[    35.826] (WW) Falling back to old probe method for fbdev
[    35.826] (II) Loading sub module "fbdevhw"
[    35.826] (II) LoadModule: "fbdevhw"
[    35.826] (II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
[    36.042] (II) Module fbdevhw: vendor="X.Org Foundation"
[    36.042]    compiled for 1.8.2, module version = 0.0.2
[    36.042]    ABI class: X.Org Video Driver, version 7.0
...
[    36.281] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] This chipset requires a kernel module version of 1.17.0,
[dri] but the kernel reports a version of 2.0.0.[dri] If using legacy modesetting, upgrade your kernel.
[dri] If using kernel modesetting, make sure your module is
[dri] loaded prior to starting X, and that this driver was built
[dri] with support for KMS.
[    36.281] (WW) RADEON(0): Gallium DRI requires kernel-modesetting.  Ignoring ForceGallium option

So at least some progress but "drm report modesetting isn't supported" doesn't sound good. Also, it still complains about needing to load the driver prior to X. 

> **Temüjin said:**
> You can use the method suggested by the above link, but you can also create an xorg.conf.

Ah, good, I didn't know you could still configure the driver with xorg.conf when using KMS.

---

### Post by Yellow Pasque on 2011-06-26
I think you need to be using the 2.6.35 kernel from that PPA.

---

### Post by mikrogroove on 2011-06-26
> **Temüjin said:**
> I think you need to be using the 2.6.35 kernel from that PPA.

Thanks, I suspected it might come to this (kernel switch). The problem there is that I'm using the PHC kernel and the PHC Ubuntu PPA only has 2.6.32 as the latest available version. I suppose I would be able to build a more recent one myself?

---

### Post by mikrogroove on 2011-06-26
I found this bug which sounds like it's related: 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569332#10](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=569332#10)

Edit: I also have these issues with Ctrl+Alt+F1 etc

---

### Post by mikrogroove on 2011-06-26
Ok, so I found this thread (in German): 

[http://debianforum.de/forum/viewtopic.php?f=2&t=119689&start=30](http://debianforum.de/forum/viewtopic.php?f=2&t=119689&start=30)

which led on to: 

[http://phoronix.com/forums/showthread.php?19555-R600-r700-kms-no-go&p=100918](http://phoronix.com/forums/showthread.php?19555-R600-r700-kms-no-go&p=100918)

Following the suggestion to move the modline from Grub default to /etc/modules, I added this line to the end of modules:

```
radeon modeset=1
``` 

I also removed the old line from Grub along with the "splash" option, rebuilt Grub and rebooted. **Success!** Xorg log file now contains (abbreviated): 

X.Org X Server 1.8.2
Release Date: 2010-07-01
[    36.650] X Protocol Version 11, Revision 0
[    36.650] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    36.650] Current Operating System: Linux iron 2.6.32-31-generic-phc #61~phc0-Ubuntu SMP Thu Apr 21 10:41:30 UTC 2011 i686
[    36.650] Current version of pixman: 0.21.4
...
[    37.018] (--) PCI:*(0:1:0:0) 1002:3154:1014:0570 ATI Technologies Inc M24GL [Mobility FireGL V3200] rev 128, Mem @ 0xc0000000/134217728, 0xb0100000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
...
[    37.336] (II) Primary Device is: PCI 01@00:00:0
[    37.336] (II) [KMS] Kernel modesetting enabled.
[    37.336] (WW) Falling back to old probe method for vesa
[    37.337] (WW) Falling back to old probe method for fbdev
[    37.337] (II) Loading sub module "fbdevhw"
[    37.337] (II) LoadModule: "fbdevhw"
[    37.337] (II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
[    37.365] (II) Module fbdevhw: vendor="X.Org Foundation"
[    37.365]     compiled for 1.8.2, module version = 0.0.2
[    37.365]     ABI class: X.Org Video Driver, version 7.0
...
[    37.365] (**) RADEON(0): Option "ForceGallium" "True"
...
[    37.365] (--) RADEON(0): Chipset: "ATI FireGL M24 GL 3154 (PCIE)" (ChipID = 0x3154)
[    37.365] (II) RADEON(0): PCIE card detected
[    37.366] drmOpenDevice: node name is /dev/dri/card0
[    37.366] drmOpenDevice: open result is 9, (OK)
[    37.366] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    37.366] drmOpenDevice: node name is /dev/dri/card0
[    37.366] drmOpenDevice: open result is 9, (OK)
[    37.366] drmOpenByBusid: drmOpenMinor returns 9
[    37.366] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    37.366] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    37.366] (II) RADEON(0): Overriding default DRI driver selection.  Gallium selected.
...
[    37.621] (WW) RADEON(0): You need a newer kernel for sync extension
[    37.621] (II) RADEON(0): [DRI2] Setup complete
[    37.621] (II) RADEON(0): [DRI2]   DRI driver: r300
...
[    37.622] (II) RADEON(0): Direct rendering enabled
[    37.622] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.

---------------------------------------------
And dmesg: 

[   31.395600] [drm] radeon kernel modesetting enabled.
[   31.395808] radeon 0000:01:00.0: power state changed by ACPI to D0
...
[   31.409680] [drm] radeon: Initializing kernel modesetting.
...
[   31.417876] radeon 0000:01:00.0: radeon: using MSI.
...
[   31.425735] [drm] radeon: cp idle (0x10000C03)
[   31.425927] [drm] Loading R300 Microcode
...
[   31.426417] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
...
[   31.672655] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   38.407299] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

---------------------------------------------

Does this look like it's all good? 

Thanks!

---

### Post by mikrogroove on 2011-06-26
Errrm... So, after getting KMS working, thanks to Temüjin getting me on the right track, I now wanted to enable the power management features as per the guide linked to by Temüjin. But digging around in the /sys/class/drm/card0/device/ directory I found this seemingly endless directory nesting: 

/sys/class/drm/card0/device/drm/card0/device/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver/0000:01:00.0/driver

At which point i got fed up and stopped - only god knows how deep this rabbit hole goes. Surely this is not correct?

---

