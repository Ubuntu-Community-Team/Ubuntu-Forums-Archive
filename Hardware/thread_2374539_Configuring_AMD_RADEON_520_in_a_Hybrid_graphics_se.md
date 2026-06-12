---
title: "Configuring AMD RADEON 520 in a Hybrid graphics setup with Wayland"
date: 2017-10-17
forum: Hardware
---

### Post by Kanfused on 2017-10-17
Hi,
The tl;dr about this question is - Is my radeon 520 dedicated  card working fine? Do I need to set  "xrandr --setprovideroffloadsink  radeon Intel" in Wayland to configure hybrid graphics? Xrandr is not  working well in weston/wayland.

Long version:
I installed Ubuntu 17.10 on my newly bought HP Laptop (Model: [HP 15-BS576TX]("https://support.hp.com/in-en/document/c05562627")) which has a dedicated AMD 520 2GB DDR3 graphics card and Intel HD 620 onboard graphics in a Kabylake Core i5 processor system. This is the first time I'm installing Linux on a hybrid graphics card setup on a laptop. 

Now, Ubuntu 17.10 defaults with Xwayland instead of Xorg/XFree86. I find it confusing to configure AMD Radeon 520 dedicated graphics. The confusing part is  xrander --listproviders only list the intel hd 620 integrated graphics.
```
xrandr --listproviders 
Providers: number : 0

```

But, lspci -knnn shows that AMD Radeon 520 card is detected:
```
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / R7 M520] [1002:6660] (rev 83)
    Subsystem: Hewlett-Packard Company Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430] [103c:832b]
    Kernel driver in use: radeon
    Kernel modules: radeon, amdgpu
```

and Integrated Intel HD 620 graphics:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02)
    Subsystem: Hewlett-Packard Company HD Graphics 620 [103c:832b]
    Kernel driver in use: i915
    Kernel modules: i915

```


```


# lshw -C video
  *-display                 
       description: VGA compatible controller
       product: HD Graphics 620
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:128 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:6000(size=64) memory:c0000-dffff
  *-display
       description: Display controller
       product: Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 / M430 / R7 M520]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 83
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:129 memory:90000000-9fffffff memory:b1200000-b123ffff ioport:5000(size=256) memory:b1240000-b125ffff


```
I'm booting with  "radeon.modeset=1" which is added to the grub bootloader entry. 

Now, if I run  any app with DRI_PRIME=1 it works and shows below info:

```
 :~$ DRI_PRIME=1 glxinfo |grep -i Opengl*
OpenGL vendor string: X.Org
OpenGL renderer string: AMD HAINAN (DRM 2.50.0 / 4.13.0-16-generic, LLVM 5.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.2.2
OpenGL core profile shading language version string: 4.50

 
```

[B]So, I assumed Radeon 520 is working fine. Then, noticed that there is no mention of gallium 3d? But, why Xrandr is not showing dedicated card as one of the providers?  

[/B]I see that there is amdgpu driver module also loaded. From the list, R520 card seems to be supported by the radeon driver. 
```
 
 lsmod |grep radeon
radeon               1470464  0
ttm                    94208  2 amdgpu,radeon
i2c_algo_bit           16384  3 amdgpu,radeon,i915
drm_kms_helper        167936  3 amdgpu,radeon,i915
drm                   356352  28 amdgpu,radeon,i915,ttm,drm_kms_helper

```

Wnat needs to be done now? I have no custom scripts or files placed in /etc/X11 directory .

---

### Post by tiagojc2 on 2017-11-14
Same problem..

---

