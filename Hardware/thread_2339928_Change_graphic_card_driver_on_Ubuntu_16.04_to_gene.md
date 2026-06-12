---
title: "Change graphic card driver on Ubuntu 16.04 to generic modesetting driver"
date: 2016-10-14
forum: Hardware
---

### Post by ericjoh on 2016-10-14
Hi,

I have Ubuntu 16.04 installed on a machine (HP EliteOne 800 G2 AiO). However, the graphics does not work with the default installation and does not work with the latest version of Ubuntu 16.10 ([yakkety-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/yakkety-desktop-amd64.iso")  12-Oct-2016 10:39) either. I got a suggestion to try the generic modesetting driver which I would like to do.

Can anyone please tell me how to active the generic modesetting driver? From  what I can see Ubuntu 16.04 no longer uses the "xorg.conf" file, at  least I cannot find it in /etc/X11/ or /usr/share/X11/. When I tried to  install the package "xserver-xorg-video-modesetting" it said it is  already included in "xserver-xorg-core".

Thanks in advance :)

---

### Post by QIII on 2016-10-14
Hello!

Could you provide the hardware specifications of your machine - particularly the graphics hardware?

Cheers!

---

### Post by ericjoh on 2016-10-14
Sure, when I try to figure out what kind of integrated graphic card is used I type "lspci -v" and get the following:

[...]
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06) (prog-if 00 [VGA controller])
        DeviceName: Onboard IGD
        Subsystem: Hewlett-Packard Company Skylake Integrated Graphics
        Flags: bus master, fast devsel, latency 0, IRQ 127
        Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 3000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [40] Vendor Specific Information: Len=0c <?>
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [100] #1b
        Capabilities: [200] Address Translation Service (ATS)
        Capabilities: [300] #13
        Kernel driver in use: i915_bpo
        Kernel modules: i915_bpo
[...]

---

### Post by Yellow Pasque on 2016-10-15
You can still create your own /etc/X11/xorg.conf
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "modesetting"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by ericjoh on 2016-10-17
Thanks! However, the screen still looks the same after adding the above /etc/X11/xorg.conf and rebooting the computer :-(

(the screen is split in half in height so that the  whole screen is  squeezed in in the upper half of the screen and the  lower half of the  screen is black)

---

### Post by alexeyn on 2016-10-19
add 'blacklist i915_bpo"   /etc/modprobe.d/ihoku.conf

---

### Post by Yellow Pasque on 2016-10-19
^I think you mean blacklist i915_bpo
I'm curious what that does. Are newer intel GPU's also supported by older i915 module?

EDIT: I guess so, since modinfo i915 lists skylake firmware:
```
# modinfo i915
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.
firmware:       i915/bxt_dmc_ver1_07.bin
firmware:       i915/skl_dmc_ver1_26.bin
firmware:       i915/kbl_dmc_ver1_01.bin
firmware:       i915/kbl_guc_ver9_14.bin
firmware:       i915/bxt_guc_ver8_7.bin
firmware:       i915/skl_guc_ver6_1.bin
```

---

### Post by crimsonleech-gmail on 2016-10-19
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) for the Intel graphics update tool for 16.04 you will have to wait for the 16.10 version to come out for your problems as 4.8 kernel is too new.

---

### Post by ericjoh on 2016-10-20
Sorry, but do you mean that I should create the file /etc/modeprobe.d/ihoku.conf and add the line "blacklist i915_bpo" to this file? In my Ubuntu 16.04 system the folder /etc/modeprobe.d does not exist.

---

### Post by alexeyn on 2016-10-20
yea 
  /etc/modprobe.d/ihoku.conf i mean that


any .conf does it

---

### Post by ericjoh on 2016-10-21
Thanks for all suggestions so far. I think I have tried them all, but the screen is still split in half after the computer has started upp and lightdm is shown.

I have tested with this, but it still looks the same:

```
# cat /etc/modprobe.d/ihoku.conf
blacklist i915_bpo
```

I have tested both with and without the file /etc/X11/xorg.conf that looks like this:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "modesetting"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

I have also downloaded "intel-graphics-update-tool_2.0.2_amd64.deb", installed it and have runned "/usr/bin/intel-graphics-update-tool", but the problem is still there.

Not sure if this is of any help:

```
# /usr/bin/igut-config-test
No LSB modules are available.
Distribution:
{
    distributor: 'Ubuntu'
    release    : '16.04'
    codename   : 'xenial'
    config-id  : [Ubuntu xenial]
}
{
  errors: (nil)
  sources: [https://download.01.org/gfx/ubuntu/16.04/main xenial main]
  keys: []
  docs: []
  INSTALL: []
  install: [i915-4.6.3-4.4.0-dkms libgles1-mesa libgles2-mesa libosmesa6 libva-drm1 libva-egl1 libva-glx1 libva-tpi1 libva-wayland1 libva-x11-1 vainfo libcairo2]
  upgrade: [libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libwayland-egl1-mesa libxatracker2 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libva1 va-driver-all i965-va-driver intel-gpu-tools]
  lts: []
}
```

---

### Post by alexeyn on 2016-10-21
last fails coz of blacklist maybe.

---

### Post by ericjoh on 2016-10-26
I have now removed /etc/modprobe.d/ihoku.conf and rebooted the computer, but the screen problem is still the same.

igut-config-test now looks like this:

```
# /usr/bin/igut-config-test                                                                                                                              
No LSB modules are available.                                                                                                                                            
Distribution:                                                                                                                                                            
{                                                                                                                                                                        
    distributor: 'Ubuntu'                                                                                                                                                
    release    : '16.04'                                                                                                                                                 
    codename   : 'xenial'                                                                                                                                                
    config-id  : [Ubuntu xenial]                                                                                                                                         
}                                                                                                                                                                        
{                                                                                                                                                                        
  errors: (nil)                                                                                                                                                       
  sources: [https://download.01.org/gfx/ubuntu/16.04/main xenial main]                                                                                                
  keys: []                                                                                                                                                            
  docs: []                                                                                                                                                            
  INSTALL: []                                                                                                                                                         
  install: [i915-4.6.3-4.4.0-dkms libgles1-mesa libgles2-mesa libosmesa6 libva-drm1 libva-egl1 libva-glx1 libva-tpi1 libva-wayland1 libva-x11-1 vainfo libcairo2]     
  upgrade: [libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libwayland-egl1-mesa libxatracker2 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libva1 va-driver-all i965-va-driver intel-gpu-tools]                                                                                               
  lts: []                                                                                                                                                            
}
```

---

