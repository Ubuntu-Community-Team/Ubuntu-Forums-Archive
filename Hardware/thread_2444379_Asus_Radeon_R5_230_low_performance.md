---
title: "Asus Radeon R5 230 low performance"
date: 2020-05-29
forum: Hardware
---

### Post by bolaocho-86 on 2020-05-29
Hi,

I just made a new fresh install of Ubuntu 20.04 LTS.

When I connect my screen directly as a main source with my graphic card R5 230, the system performances decrease so much, but when I used as a secondary screen I works fine.
Before I had Ubuntu 18.04 LTS and it works fine.

Can any one help me?

Thank's in advance

Here I put some outputs:

lshw -c video

  *-display                 
       descripción: VGA compatible controller
       producto: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
       configuración: driver=radeon latency=0
       recursos: irq:39 memoria:d0000000-dfffffff memoria:fe620000-fe63ffff ioport:e000(size=256) memoria:fe600000-fe61ffff
  *-display
       descripción: VGA compatible controller
       producto: 2nd Generation Core Processor Family Integrated Graphics Controller
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 09
       anchura: 64 bits
       reloj: 33MHz
       capacidades: msi pm vga_controller bus_master cap_list rom
       configuración: driver=i915 latency=0
       recursos: irq:37 memoria:fe000000-fe3fffff memoria:c0000000-cfffffff ioport:f000(size=64) memoria:c0000-dffff


lsmod | grep radeon

radeon               1474560  3
ttm                   106496  1 radeon
drm_kms_helper        184320  2 radeon,i915
i2c_algo_bit           16384  2 radeon,i915
drm                   491520  10 drm_kms_helper,radeon,i915,ttm

dmesg | grep -i radeon

[    3.853992] [drm] radeon kernel modesetting enabled.
[    3.854046] radeon 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 0: 0xd0000000 -> 0xdfffffff
[    3.854047] radeon 0000:01:00.0: remove_conflicting_pci_framebuffers: bar 2: 0xfe620000 -> 0xfe63ffff
[    3.854081] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    4.096400] radeon 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
[    4.102865] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    4.102868] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[    4.102934] [drm] radeon: 2048M of VRAM memory ready
[    4.102934] [drm] radeon: 1024M of GTT memory ready.
[    4.110482] [drm] radeon: dpm initialized
[    4.112230] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    4.116814] radeon 0000:01:00.0: WB enabled
[    4.116817] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0x(____ptrval____)
[    4.116818] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0x(____ptrval____)
[    4.117563] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x(____ptrval____)
[    4.117592] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    4.117630] radeon 0000:01:00.0: radeon: using MSI.
[    4.117668] [drm] radeon: irq initialized.
[    4.987552] [drm] Radeon Display Connectors
[    5.340318] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    5.391136] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0

---

