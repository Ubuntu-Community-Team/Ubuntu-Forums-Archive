---
title: "Laptop (Inspiron 5150) hangs on startup (sometimes)"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by markr on 2005-10-18
I have a problem (I think since I installed the NVidia drivers from the 5.10 CD) in that sometimes when starting up it appears to start everything okay, but when it would usually start Gnome,  I just get a blank screen and have to perform a hard power down of the laptop to restart it.

The only thing I can see in the logs is :

Oct 18 05:38:29 localhost kernel: [4294698.483000] intel8x0: clocking to 48000
Oct 18 05:38:29 localhost kernel: [4294699.813000] Linux Kernel Card Services
Oct 18 05:38:29 localhost kernel: [4294699.813000]   options:  [pci] [cardbus] [pm]
Oct 18 05:38:29 localhost kernel: [4294699.826000] PCI: Enabling device 0000:02:04.0 (0000 -> 0002)
Oct 18 05:38:29 localhost kernel: [4294699.826000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 18 05:38:29 localhost kernel: [4294699.826000] Yenta: CardBus bridge found at 0000:02:04.0 [1028:015f]
Oct 18 05:38:29 localhost kernel: [4294699.826000] Yenta: Using CSCINT to route CSC interrupts to PCI
Oct 18 05:38:29 localhost kernel: [4294699.826000] Yenta: Routing CardBus interrupts to PCI
Oct 18 05:38:29 localhost kernel: [4294699.826000] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64
Oct 18 05:38:29 localhost kernel: [4294700.047000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
Oct 18 05:38:29 localhost kernel: [4294700.047000] Socket status: 30000020
Oct 18 05:38:29 localhost kernel: [4294700.143000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
Oct 18 05:38:29 localhost kernel: [4294700.143000] ACPI: PCI Interrupt 0000:02:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Oct 18 05:38:29 localhost kernel: [4294700.198000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[faffd800-faffdfff]  Max Packet=[2048]
Oct 18 05:38:29 localhost kernel: [4294701.696000] Real Time Clock Driver v1.12
Oct 18 05:38:29 localhost kernel: [4294701.770000] input: PC Speaker
Oct 18 05:38:29 localhost kernel: [4294705.173000] ACPI: AC Adapter [AC] (on-line)
Oct 18 05:38:29 localhost kernel: [4294705.473000] ACPI: Battery Slot [BAT0] (battery present)
Oct 18 05:38:29 localhost kernel: [4294705.489000] ACPI: Lid Switch [LID]
Oct 18 05:38:29 localhost kernel: [4294705.489000] ACPI: Power Button (CM) [PBTN]
Oct 18 05:38:29 localhost kernel: [4294705.489000] ACPI: Sleep Button (CM) [SBTN]
Oct 18 05:38:29 localhost kernel: [4294705.682000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)


This appears to be the last thing that happens before the system hangs; mostly to do with ACPI.  Has anyone seen this before, or any thoughts on how the NVidia drivers could conflict with ACPI occasionally.

I have had the same problem shutting down on occasion as well.

Any thoughts appreciated.

Mark.

---

### Post by markr on 2005-10-19
Comparing the above log with the log when the system started okay reveals that the next line is (or should be):

"Found an AGP 2.0 Compliant device at 0000:00:000"

I have had to change my xorg.conf back to "nv" from "nvidia" for the moment as it seems to be hanging more and more.

I am currently using the "nvidia-glx" package which tells me it is using verion 1.0.7667.

Any help appreciated.

Mark.

---

