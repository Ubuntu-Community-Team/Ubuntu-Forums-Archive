---
title: "Ryzen 5 with Radeon RX 560X- Unable to use dedicated graphics card"
date: 2019-02-22
forum: Hardware
---

### Post by chandansathvik on 2019-02-22
I have purchased a new laptop Acer Nitro ryzen 5 with AMD Radeon Graphics card RX 560X. Had lot of trouble booting into ubuntu 18.04.2  but finally got it to work with the following boot parameters

[B]GRUB_CMDLINE_LINUX_DEFAULT="nosplash pci=noacpi rcu_nocbs=0-7 processor.max_cstate=1"

[/B]I want to use opencl so first tried installing amdgpu-pro drivers. The drivers installed successfully but clinfo gives[B] ERROR: clGetPlatformIDs(-1001)

Here is some info 

[/B]

```

~$ dmesg | grep amdgpu

[    3.722898] [drm] amdgpu kernel modesetting enabled.
[    3.724573] [drm] amdgpu version: 19.10.7.418
[    3.737757] amdgpu 0000:01:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    3.766021] [drm:amdgpu_get_bios [amdgpu]] *ERROR* ACPI VFCT table present but broken (too short #2)
[    3.768133] amdgpu 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
[    3.769905] amdgpu 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0x0000
[    3.771581] [drm:amdgpu_get_bios [amdgpu]] *ERROR* Unable to locate a BIOS ROM
[    3.773153] amdgpu 0000:01:00.0: Fatal error during GPU init
[    3.774713] [drm] amdgpu: finishing device.
[    3.776528] amdgpu: probe of 0000:01:00.0 failed with error -22
[    3.778091] fb: switching to amdgpudrmfb from EFI VGA
[    3.779885] amdgpu 0000:04:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    3.781212] amdgpu 0000:04:00.0: VRAM: 1024M 0x000000F400000000 - 0x000000F43FFFFFFF (1024M used)
[    3.781218] amdgpu 0000:04:00.0: GART: 1024M 0x0000000000000000 - 0x000000003FFFFFFF
[    3.781224] amdgpu 0000:04:00.0: AGP: 267419648M 0x000000F800000000 - 0x0000FFFFFFFFFFFF
[    3.781518] [drm] amdgpu: 1024M of VRAM memory ready
[    3.781523] [drm] amdgpu: 6930M of GTT memory ready.
[    4.086184] [drm:construct [amdgpu]] *ERROR* construct: Invalid Connector ObjectID from Adapter Service for connector index:2! type 0 expected 3
[    4.086288] [drm:construct [amdgpu]] *ERROR* construct: Invalid Connector ObjectID from Adapter Service for connector index:3! type 0 expected 3
[    4.160922] amdgpu 0000:04:00.0: fb0: amdgpudrmfb frame buffer device
[    4.176245] amdgpu 0000:04:00.0: ring gfx uses VM inv eng 0 on hub 0
[    4.176291] amdgpu 0000:04:00.0: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[    4.176331] amdgpu 0000:04:00.0: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[    4.176372] amdgpu 0000:04:00.0: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[    4.176412] amdgpu 0000:04:00.0: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[    4.176451] amdgpu 0000:04:00.0: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[    4.176491] amdgpu 0000:04:00.0: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[    4.176530] amdgpu 0000:04:00.0: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[    4.176570] amdgpu 0000:04:00.0: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[    4.176610] amdgpu 0000:04:00.0: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[    4.176649] amdgpu 0000:04:00.0: ring sdma0 uses VM inv eng 0 on hub 1
[    4.176687] amdgpu 0000:04:00.0: ring vcn_dec uses VM inv eng 1 on hub 1
[    4.176725] amdgpu 0000:04:00.0: ring vcn_enc0 uses VM inv eng 4 on hub 1
[    4.176764] amdgpu 0000:04:00.0: ring vcn_enc1 uses VM inv eng 5 on hub 1
[    4.176803] amdgpu 0000:04:00.0: ring vcn_jpeg uses VM inv eng 6 on hub 1
[    4.180321] [drm] Initialized amdgpu 3.27.0 20150101 for 0000:04:00.0 on minor 0

```

I ve been juggling with different kernel versions. My current version is [B]Linux 4.18.0-041800-generic x86_64

Here is some more info 

[/B]```

$ sudo lspci -nn | grep -E 'VGA|Display'

01:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Radeon RX 460/560D / Pro 450/455/460/555/560] [1002:67ef] (rev c0)
04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] [1002:15dd] (rev c4)

```

---

### Post by peter248 on 2019-02-26
run app from terminal using 
DRI_PRIME=0 glxgears  for cpu vega
DRI_PRIME=1 glxgears  for RX560
but expect lower fps on RX560 than on vega due the some driver performance issue (better on 5.0 RC7 kernel)

---

### Post by batmalin on 2019-11-18
> **peter248 said:**
> run app from terminal using 
DRI_PRIME=0 glxgears  for cpu vega
DRI_PRIME=1 glxgears  for RX560
but expect lower fps on RX560 than on vega due the some driver performance issue (better on 5.0 RC7 kernel)

Actually, this is not true. Despite the fact that obsolete bench tools are showing lower performance on RX560X the current one are showing something different. I am attaching 2 Win and 2 Linux benchmarks for the Vega and the RX560X. Well Win performs a little bit better, but that might be fixed with the next update of the amdgpu open source driver. My system is Acer Nitro 5 AN515-43 (Ryzen 5 3550H, 16GB DDR4 2666Mhz, 512GB Intel 660p NVMe, 1TB HDD 5400rpm, Vega 8, RX560X, BIOS 1.06).

---

