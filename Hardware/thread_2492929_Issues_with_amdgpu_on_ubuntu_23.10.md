---
title: "Issues with amdgpu on ubuntu 23.10"
date: 2023-11-28
forum: Hardware
---

### Post by seeg on 2023-11-28
Hello,

I have a laptop with an "AMD Ryzen 7 4700U with Radeon Graphics". I'm having serious issues with the amdgpu driver. 

I tried so many boot settings and many configs I could find on the internet, but I always end up with a blank screen. In the end, only vesa works. My grub settings are:

```
GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt radeon.modeset=1 nomodeset"

```
So basically nomodeset turns the GPU support off. Any attempt to remove `nomodeset` leaves me with dark screen. Apparently the computer works as I can Ctrl-Alt-Del to reboot it.

Here is lspci output:

```
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Renoir [Radeon RX Vega 6 (Ryzen 4000/5000 Mobile Series)] (rev c2) (prog-if 00 [VGA controller])
        Subsystem: CLEVO/KAPOK Computer Renoir
        Flags: bus master, fast devsel, latency 0, IRQ 255, IOMMU group 5
        Memory at fce0000000 (64-bit, prefetchable) [size=256M]
        Memory at fcf0000000 (64-bit, prefetchable) [size=2M]
        I/O ports at 1000 [disabled] [size=256]
        Memory at d0400000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>
        Kernel modules: amdgpu

```

Could someone help me?

---

### Post by seeg on 2023-11-28
Hm, it seems that `pci=noats` kernel parameter fixed the problem. I found the solution here [https://forum.endeavouros.com/t/wont-boot-with-clevo-amd-4700u-laptop/23818](https://forum.endeavouros.com/t/wont-boot-with-clevo-amd-4700u-laptop/23818)

The key was to find motherboard manufacturer and investigate from there.

---

