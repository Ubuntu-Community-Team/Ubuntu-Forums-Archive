---
title: "Nividia problems after new videocard and monitor"
date: 2010-10-02
forum: Hardware
---

### Post by B3rt on 2010-10-02
I recently updated my video card and my monitor.
I updated to a video card with 3 output, 1x vga, 1x hdmi and 1x dvi
My old card was 1x vga + 1x dvi
Both cards are nvida cards

Since this update my ubuntu 10.10 (64bit) very often give an graphic error on both such as:

Failed to initialize the NVIDIA kernel module. Please see the system's kernel log for additional error messages and consult the NVIDIA README for details.

I use the original drivers suplied by ubuntu, ther eare no updates.

I can start in graphic safe mode and restart gdm, after restarting gdm the graphic works fine.


The message log gives:

```

[   18.249642] nvidia: module license 'NVIDIA' taints kernel.
[   18.249646] Disabling lock debugging due to kernel taint
[   18.404458] usb 2-3.4.2: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[   18.446541] usb 2-3.4.2: configuration #1 chosen from 1 choice
[   18.512098] input: HID 06b4:1c70 as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4.2/2-3.4.2:1.0/input/input5
[   18.512210] generic-usb 0003:06B4:1C70.0003: input,hidraw2: USB HID v1.10 Keyboard [HID 06b4:1c70] on usb-0000:00:1d.7-3.4.2/input0
[   18.649295]   alloc irq_desc for 22 on node -1
[   18.649298]   alloc kstat_irqs on node -1
[   18.649306] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.649389] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.770642] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   18.781588] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.781591] hda_intel: Disable MSI for Nvidia chipset
[   18.781629] HDA Intel 0000:01:00.1: setting latency timer to 64
[   18.804145] Console: switching to colour frame buffer device 80x30
[   18.878705]   alloc irq_desc for 29 on node -1
[   18.878709]   alloc kstat_irqs on node -1
[   18.878723] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X


```


after gdm restart:
```

[   20.660531] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.660541] nvidia 0000:01:00.0: setting latency timer to 64
[   20.660547] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.660732] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010

```

I cannot find out why this is happening, does anyone have an explanation?

---

