---
title: "Huge lag with RX580 under 20.04 in Gnome"
date: 2020-05-02
forum: Hardware
---

### Post by chortya2 on 2020-05-02
Hi all,

I am gradually moving from Windows 10 to Ubuntu on most of my devices at home. I repurposed one of my old mining rigs to play around with Ubuntu and installed 20.04 on it.
My integrated Intel graphics card works very well but the new RX580 (Saphire) introduces huge lag and choppiness.

```
sudo lshw -c video  *-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 mode=2560x1440 visual=truecolor xres=2560 yres=1440
       resources: iomemory:200-1ff iomemory:210-20f irq:130 memory:2000000000-20ffffffff memory:2100000000-21001fffff ioport:e000(size=256) memory:dfe00000-dfe3ffff memory:dfe40000-dfe5ffff



```

```
lsmod | grep amdamdgpu               4575232  2
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
ttm                   106496  1 amdgpu
drm_kms_helper        184320  2 amdgpu,i915
i2c_algo_bit           16384  2 amdgpu,i915
drm                   491520  17 gpu_sched,drm_kms_helper,amdgpu,i915,ttm



```

```
dmesg | grep -i amdgpu[   12.949673] [drm] amdgpu kernel modesetting enabled.
[   12.950771] amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 0: 0x2fe0000000 -> 0x2fefffffff
[   12.950772] amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 2: 0x2ff0000000 -> 0x2ff01fffff
[   12.950773] amdgpu 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 5: 0xdfe00000 -> 0xdfe3ffff
[   12.950801] amdgpu 0000:01:00.0: enabling device (0000 -> 0003)
[   13.499145] amdgpu 0000:01:00.0: BAR 2: releasing [mem 0x2ff0000000-0x2ff01fffff 64bit pref]
[   13.499147] amdgpu 0000:01:00.0: BAR 0: releasing [mem 0x2fe0000000-0x2fefffffff 64bit pref]
[   13.499165] amdgpu 0000:01:00.0: BAR 0: assigned [mem 0x2000000000-0x20ffffffff 64bit pref]
[   13.499170] amdgpu 0000:01:00.0: BAR 2: assigned [mem 0x2100000000-0x21001fffff 64bit pref]
[   13.499192] amdgpu 0000:01:00.0: VRAM: 4096M 0x000000F400000000 - 0x000000F4FFFFFFFF (4096M used)
[   13.499193] amdgpu 0000:01:00.0: GART: 256M 0x000000FF00000000 - 0x000000FF0FFFFFFF
[   13.499264] [drm] amdgpu: 4096M of VRAM memory ready
[   13.499266] [drm] amdgpu: 4096M of GTT memory ready.
[   13.832130] amdgpu: [powerplay] hwmgr_sw_init smu backed is polaris10_smu
[   14.068232] [drm] Initialized amdgpu 3.35.0 20150101 for 0000:01:00.0 on minor 1
[   14.474218] snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])



```

Already installed [COLOR=#333333][FONT=monospace]ppa:oibaf/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]graphics-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]drivers but there was no change.
[/FONT][/COLOR]Also tried Proprietary AMDGPU-PRO drivers, but no luck too.
[COLOR=#333333][FONT=monospace]What else can I try?

[/FONT][/COLOR]

---

### Post by chortya2 on 2020-05-02
I was able to solve the issues by resetting the BIOS. It seems I had some strange settings from the miner config.

---

### Post by CelticWarrior on 2020-05-02
> **chortya2 said:**
> I was able to solve the issues by resetting the BIOS. It seems I had some strange settings from the miner config.

Yes, that must have been it.

---

