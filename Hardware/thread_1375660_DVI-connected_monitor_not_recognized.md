---
title: "DVI-connected monitor not recognized"
date: 2010-01-08
forum: Hardware
---

### Post by int32 on 2010-01-08
Hi,

My ubuntu refuses to recognize a DVI-connected monitor on a W500 lenovo laptop. But not always, - if I boot to windows, then reboot (without turning the laptop off) back into ubuntu, then it works, once. After the next reboot the monitor is not recognized again.  Also, I found that if I change video boot device in BIOS and boot into ubuntu, then it works, but just once - next reboots again ignore DVI. Windows behaves also in an interesting way - when I boot it after ubuntu, when DVI is not recognized, it doesn't recognize it as well. However after next reboot, and all subsequent reboots, it works.

I collected a load of information in sessions where the connection is and isn't recognized.  I also made diffs between files, where especially interesting is dmesg diff (see excerpt below).  It seems that when boot video device is "pci 0000:01:00.0", the DVI connection is recognized.  I don't see why a different boot video device makes the connection unusable though. I wonder if I can tell ubuntu to use that particular device as boot?

I also tried latest intel video drivers for X, didn't help, but I think that the problem appears before X is loaded. What else I can try?

Thank you!

PS - all logs and diffs are here: [http://karasik.eu.org/misc/dvi/](http://karasik.eu.org/misc/dvi/) ; the excerpt dmesg is from diff/dmesg.

[FONT=Courier New]--- dmesg.dvi
+++ dmesg.nodvi

- pci 0000:01:00.0: Boot video device
+ pci 0000:00:02.0: Boot video device
+ pci 0000:01:00.0: enabling device (0106 -> 0107)
  pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  pci 0000:01:00.0: setting latency timer to 64
  [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
+ ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
+ pci 0000:00:02.0: power state changed by ACPI to D0
+ pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
+ pci 0000:00:02.0: setting latency timer to 64
+ mtrr: no more MTRRs available
+ [drm] MTRR allocation failed.  Graphics performance may suffer.
+   alloc irq_desc for 31 on node -1
+   alloc kstat_irqs on node -1
+ pci 0000:00:02.0: irq 31 for MSI/MSI-X
+ input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09/input/input6
+ ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
+ [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
+ pci 0000:01:00.0: Invalid ROM contents
+ pci 0000:01:00.0: Invalid ROM contents
+ pci 0000:01:00.0: Invalid ROM contents
- [drm] Setting GART location based on new memory map
- [drm] Loading RV635 CP Microcode
- [drm] Loading RV635 PFP Microcode
- [drm] Resetting GPU
- [drm] writeback test succeeded in 1 usecs[/FONT]

---

