---
title: "New system with AMD 6700XT can't use GPU"
date: 2023-08-20
forum: Hardware
---

### Post by agmartin42 on 2023-08-20
Hi, I've been struggling with this for the past week. No matter what I try I haven't been able to get Ubuntu to actually use my graphics card for rendering. I'm running a fresh install of 22.04, I'm on the 6.2.0-26-generic kernel, I've installed Mesa from the kisak ppa, I tried installing the amd proprietary drivers at one point (not the pro drivers though), but I haven't been able to actually make use of my gpu.

The gpu is seen when I do [FONT=courier new]lshw[/FONT], but no driver is listed.
```

sudo lshw -c video  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Navi 22 [Radeon RX 6700/6700 XT / 6800M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c5
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:e000(size=256) memory:fc900000-fc9fffff memory:c0000-dffff
  *-graphics
       product: EFI VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=2560,1080

```

Running [FONT=courier new]inxi[/FONT] confirms that the system is using [FONT=courier new]llvmpipe[/FONT] for software rendering.
```

inxi -G
Graphics:
  Device-1: AMD Navi 22 [Radeon RX 6700/6700 XT / 6800M] driver: N/A
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: ati,vesa
    unloaded: fbdev,modesetting,radeon gpu: N/A resolution: 2560x1080~92Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.1.6 - kisak-mesa PPA

```

The only thing I think could be the problem is that I need to use [FONT=courier new]nomodeset[/FONT] in grub to be able to boot. The proprietary drivers complained about that when I installed them, but without it the system hard reboots almost immediately after selecting the Ubuntu option. All the posts I could find of people needing to use the [FONT=courier new]nomodeset[/FONT] option were because when they would boot they would only have a black screen, but when I try it the system fully power cycles itself. I've tried to remove it after installing the drivers, but no luck there. I'm just at a loss for what troubleshooting steps to try next.

Thank you for any help!

---

### Post by QIII on 2023-08-21
Would you please post the results of 

```
lsmod | grep amdgpu
```

and

```
lsmod | grep radeon
```

---

### Post by agmartin42 on 2023-08-21
Neither of those had any output.

I've checked to make sure that they aren't blacklisted too, and it looks like neither of them are. Just [FONT=courier new]radeonfb[/FONT], which seems to be deprecated anyway.

```

grep -r -e radeon -e amdgpu /etc/modprobe.d
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb

```

---

