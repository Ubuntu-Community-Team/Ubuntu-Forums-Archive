---
title: "need help for framebuffer console (intel 855gm)"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by Sav on 2005-06-03
Hi, I just recompiled the 2.6.11 sources, for my benq joybook 6000 notebook.
It's all ok, but I can't have a working frame buffer console.
If i boot the system with this lilo's line:

append="video=intelfb:mtrr,accel,1280x800-16@60"

the box starts at 640x800, with this error:

[drm] Initialized i915 1.1.0 20040405 on minor 1: Intel Corp. 82852/855GM Integrated Graphics Device (#2)
intelfb: intelfb_init
intelfb: Framebuffer driver for Intel(R) 830M/845G/852GM/855GM/865G chipsets
intelfb: Version 0.9.2
intelfb: intelfb_setup
intelfb: options: mtrr,accel,vtotal:32768,1280x800
intelfb: intelfb_pci_register
PCI: 0000:00:02.0 has unsupported PM cap regs version (1)
ACPI: PCI interrupt 0000:00:02.0[A] -> GSI 10 (level, low) -> IRQ 10
intelfb: fb aperture: 0xb0000000/0x8000000, MMIO region: 0xf0000000/0x80000
intelfb: 00:02.0: Intel(R) 855GME, aperture size 128MB, stolen memory 32636kB
intelfb: fb: 0xb0000000(+ 0x0)/0x1fdf000 (0xde980000)
intelfb: MMIO: 0xf0000000/0x80000 (0xe6a00000)
intelfb: ring buffer: 0xb1fe0000/0x10000 (0xe0960000)
intelfb: HW cursor: 0x1529000/0x1000 (0xe0970000) (offset 0x1ff0) (phys 0x1529000)
intelfb: options: vram = 4, accel = 1, hwcursor = 1, fixed = 0, noinit = 0
intelfb: options: mode = "1280x800"
intelfb: Non-CRT device is enabled ( LVDS port ).  Disabling mode switching.
intelfb: Video mode must be programmed at boot time.
intelfb: cleanup

If I use vga=791 (I don't know the command for 1280x800), the system boots in framebuffers, but with non cursor (intelfb: the cursor was killed - restore it !!)

If I do a "scan" after vga=ask, the system hangs, with monitor madness.
I also edite the fb.modes files, by adding:

mode "1280x800"
  geometry   1280 800   1280 38   8
  timings    11981   200 72   24 1   128 3
endmode

Any ideas?
Thanks in advance

Sav

---

### Post by Sav on 2005-06-03
video=intelfb:mtrr,accel,1280x800-24@60,hwcursor=0

Thanks to this line i solved the cursor problem. With the "hwcursor" option i can set the proper value.

Now, the only problem is the resolution, stocked at 1024x768.

---

