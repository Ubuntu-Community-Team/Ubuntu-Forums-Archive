---
title: "Will boot ONLY with GRUB's &quot;recovery mode&quot; or nomodeset"
date: 2017-03-15
forum: Hardware
---

### Post by seedsca2 on 2017-03-15
I can't even boot to a Windows installation CD (only for tests ;))
When I try a normal boot I get a black screen and nothing else. No logging under kern.log, syslog or Xorg.0.log

Video driver is xserver-xorg-video-radeon version 7.7.1-1
Kubuntu 16.10
Lenovo y560 Laptop

```
sudo lspci -v -s 01:00.0
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5730 / 6570M] (prog-if 00 [VGA controller])
        Subsystem: Lenovo Mobility Radeon HD 5730
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e8400000 (64-bit, non-prefetchable) [size=128K]
        I/O ports at 2000 [size=256]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Kernel modules: radeon
```

This is from when I boot in "recovery mode" as NOTHING gets logged otherwise
```
dmesg | egrep 'drm|radeon'
[   47.900816] [drm] Initialized drm 1.1.0 20060810
[   48.349718] [drm] VGACON disable radeon kernel modesetting.
[   48.349756] [drm:radeon_init [radeon]] *ERROR* No UMS support in radeon module!
```

Again "recovery mode"
```
sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5730 / 6570M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:e8400000-e841ffff ioport:2000(size=256) memory:c0000-dffff


```

---

