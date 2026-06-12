---
title: "Use OpenGL with intel"
date: 2014-10-27
forum: Hardware
---

### Post by jurgen32 on 2014-10-27
Hi all,

I have a hybrid video card (nvidia quadro k1100m). While running under Nvidia my system will use OpenGL 3.0. However, when I switch to the power saving mode (Intel) everything falls back to xrender.

I thought that my Intel was running OpenGL *before* my update to Kubuntu 14.10. While updating I ended up with a non-bootable system which I managed to get it back and running but I am quite sure that some packages are gone missing. 
Anyway, if someone can help me with this one I would be very happy. Please tell me which information I need to give (and how).

Thanks,
Jurgen

---

### Post by jurgen32 on 2014-10-27
Some info:

lxinfo | grep OpenGL
```
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 256 bits)
OpenGL version string: 3.0 Mesa 10.4.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
```

lspci
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107GLM [Quadro K1100M] (rev a1)
02:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)
```

Further I noticed that there is no xorg.conf file in etc/X11/. I made one but after reboot the name was changed in 'xorg.conf.10282014':
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
EndSection

```

---

### Post by mc4man on 2014-10-27
Just to clear up - 
"OpenGL version string: 3.0 Mesa 10.4.0-devel" seems to indicate you have mesa packages from here - 
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)
Did you add that ppa after upgrading to 14.10 or before while on 14.04? (or get upgraded mesa elsewhere?

---

### Post by grahammechanical on 2014-10-27
May I add something?

> OpenGL render string: Gallium 0.4 on llvmpipe (LLVM 3.5, 256 bits)

The system is running on llvmpipe, which is an open source video driver that is now used by Ubuntu (a) if the graphic adapter cannot do hardware accelerated 3D rendering. (b) when we use Recovery mode and select Resume. (c) if there is some kind of problem running a video driver.

You could try Additional Drivers to change video driver. I don't think that Ubuntu uses an xorg.conf file any more. There is not one on my system. Linux/Xserver reads the screen resolution from something called Extended Display Identification Data (EDID) in the monitor every time Linux loads.

Regards.

---

### Post by jurgen32 on 2014-10-28
Thank you for your reply.

#Mc4man
I already used that ppa. I forgot to change the ppa to utopic. The upgrade did not do that for me so I had to change do it afterwards. 
Innitially I just wanted to test this ppa under 14.04. However, it worked just great so I continued using my system and totally forgot about :(

#Grahammechanical
I think you are right about the xorg.conf. However, it seems strange to me that there are several files with that name and a date as extension (e.g. xorg.conf**.08262014**).
What additional drivers do you suggest?

---

### Post by jurgen32 on 2014-11-02
I have done a clean install of 14.10 and my intel video card is back on juice!
I have no idea what caused the problem... It could be that I missed (for some reason) the Nouveau packages. 
Oh well, some things will stay unsolved but are solved in the same time by just starting with a clean slate.

---

