---
title: "Problem with AMD Radeon HD 7730M, identified but not working."
date: 2023-07-31
forum: Hardware
---

### Post by herciliocneto on 2023-07-31
Lately I've been having problems with my hybrid gpu laptop on Ubuntu, have an integrade Intel gpu and a dedicated AMD Radeon HD 7730M. The xrandr show both of the gpus:

```
Providers: number : 2Provider 0: id: 0x45 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 4 associated providers: 0 name:modesetting
Provider 1: id: 0xa1 cap: 0x0 crtcs: 6 outputs: 0 associated providers: 0 name:VERDE @ pci:0000:01:00.0

```

switcheroo:

```

Device: 0
  Name:        Intel® HD Graphics 4000
  Default:     yes
  Environment: DRI_PRIME=pci-0000_00_02_0


Device: 1
  Name:        Advanced Micro Devices, Inc. [AMD®/ATI] Chelsea LP [Radeon HD 7730M]
  Default:     no
  Environment: DRI_PRIME=pci-0000_01_00_0

```

BUT, when I try tu run anything using Discrete Graphics card it just doesn't open if I try at the terminal using DRI_PRIME=1, i generally get this:

```
DRI_PRIME=1 glxinfo
name of display: :0
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeon: Failed to allocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    alignment : 4096 bytes
radeon:    domains   : 4
radeon:    va        : 0x0000000100000000
radeon: Failed to deallocate virtual address for buffer:
radeon:    size      : 65536 bytes
radeon:    va        : 0x100000000
radeonsi: can't create border_color_buffer
radeonsi: Failed to create a context.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  152 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  38
  Current serial number in output stream:  39

```

My dmesg | grep radeon show this:

```
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.19.0-50-generic root=UUID=49f16fe6-aa75-4f14-969d-3dabae7b6de7 ro quiet splash radeon.dpm=0 radeon.aspm=0 radeon.bapm=0 radeon.runpm=0 radeon.cik_support=0 amdgpu.cik_support=1 vt.handoff=7
[    0.116746] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.19.0-50-generic root=UUID=49f16fe6-aa75-4f14-969d-3dabae7b6de7 ro quiet splash radeon.dpm=0 radeon.aspm=0 radeon.bapm=0 radeon.runpm=0 radeon.cik_support=0 amdgpu.cik_support=1 vt.handoff=7
[    4.619965] [drm] radeon kernel modesetting enabled.
[    4.620963] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    4.666719] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    4.666728] radeon 0000:01:00.0: GTT: 2048M 0x0000000080000000 - 0x00000000FFFFFFFF
[    4.666800] [drm] radeon: 2048M of VRAM memory ready
[    4.666803] [drm] radeon: 2048M of GTT memory ready.
[    4.667153] [drm] radeon: power management initialized
[    4.670410] [drm] enabling PCIE gen 3 link speeds, disable with radeon.pcie_gen2=0
[    6.020515] radeon 0000:01:00.0: WB enabled
[    6.020523] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00
[    6.020528] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04
[    6.020532] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08
[    6.020535] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c
[    6.020538] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10
[    6.020942] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18
[    6.031077] radeon 0000:01:00.0: failed VCE resume (-22).
[    6.032018] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    6.032108] radeon 0000:01:00.0: radeon: using MSI.
[    6.032149] [drm] radeon: irq initialized.
[    6.664039] [drm:r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x850C)=0xCAFEDEAD)
[    6.664215] radeon 0000:01:00.0: disabling GPU acceleration
[    6.838026] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0
[    9.375094] Modules linked in: input_leds snd_pcm(+) sparse_keymap wmi_bmof(+) at24(+) snd_seq libarc4 mc serio_raw snd_seq_device snd_timer iommu_v2 mei_me gpu_sched mei snd mac_hid soundcore sch_fq_codel msr parport_pc ppdev lp parport pstore_blk ramoops reed_solomon pstore_zone efi_pstore ip_tables x_tables autofs4 hid_generic usbhid hid radeon i2c_algo_bit drm_ttm_helper ttm drm_display_helper drm_kms_helper syscopyarea sysfillrect sysimgblt crc32_pclmul fb_sys_fops i2c_i801 ahci psmouse i2c_smbus drm libahci r8169 cec xhci_pci realtek xhci_pci_renesas wmi lpc_ich rc_core video
[   19.390474] radeon 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none



```

Would appreciate some help in solving this.

---

