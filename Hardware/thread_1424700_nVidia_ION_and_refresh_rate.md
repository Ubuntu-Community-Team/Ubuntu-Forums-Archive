---
title: "nVidia ION and refresh rate"
date: 2010-03-08
forum: Hardware
---

### Post by MadeR on 2010-03-08
Greetings,
my case is with the nVidia ION chipset inside my Acer Revo R3600; my monitor is Philips Brilliance LCD 190S (Hudson 109S9).

My monitor tells me that the current resolution is 1280x1024@60
"nVidia xserver settings" tells me that the current resolution is 1280x1024@60,3
xrandr... well xrandr tells me    1280x1024      50.0*    51.0

The monitor is not showing images at its best: it's not blurry but it is not crystal clear as it should be.

```

[   12.539146] nvidia 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 22 (level, low) -> IRQ 22
[   12.539172] nvidia 0000:03:00.0: setting latency timer to 64
[   12.539635] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009

```
```

03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
        Subsystem: Acer Incorporated [ALI] Device 0222
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f8000000 (64-bit, prefetchable) [size=32M]
        I/O ports at ec00 [size=128]
        [virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb

```

---

