---
title: "ACPI VGN-S460 Sony"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by larytet on 2007-03-16
From time to time kernel stacks after power up and waits for something 1-2 minutes
I am using 6.10  - the Edgy Eft
I did not compile the kernel 
I tried to run in the save mode and discovered, that  after lines 
```

Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]

```
kernel stacks for tens of seconds.
I run Ubuntu on VGN-S460 laptop. Probably every 2-3 boots I have one fast (no problems) boot. After power up the system apparently behaves correctly. The delay is extremely annoying, especially when battery is low. Any ideas/tips how this problem can be fixed ?

thank you
Here is the full log related to the ACPI
```

Mar 10 13:06:09 submarine kernel: [17179571.548000] NET: Registered protocol family 1
Mar 10 13:06:09 submarine kernel: [17179571.548000] NET: Registered protocol family 8
Mar 10 13:06:09 submarine kernel: [17179571.548000] NET: Registered protocol family 20
Mar 10 13:06:09 submarine kernel: [17179571.548000] Using IPI No-Shortcut mode
Mar 10 13:06:09 submarine kernel: [17179571.548000] ACPI: (supports S0 S3 S4 S5)
Mar 10 13:06:09 submarine kernel: [17179571.548000] Freeing unused kernel memory: 308k freed
Mar 10 13:06:09 submarine kernel: [17179571.580000] input: AT Translated Set 2 keyboard as /class/input/input0
Mar 10 13:06:09 submarine kernel: [17179572.724000] Capability LSM initialized
Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
Mar 10 13:06:09 submarine kernel: [17179572.780000] ACPI: Getting cpuindex for acpiid 0x1
Mar 10 13:06:09 submarine kernel: [17179572.784000] ACPI: Thermal Zone [ATF0] (30 C)
Mar 10 13:06:09 submarine kernel: [17179573.308000] ICH6: IDE controller at PCI slot 0000:00:1f.1
Mar 10 13:06:09 submarine kernel: [17179573.308000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 18 (level, low) -> IRQ 201
Mar 10 13:06:09 submarine kernel: [17179573.308000] ICH6: chipset revision 3
Mar 10 13:06:09 submarine kernel: [17179573.308000] ICH6: not 100%% native mode: will probe irqs later
Mar 10 13:06:09 submarine kernel: [17179573.308000]     ide0: BM-DMA at 0x1880-0x1887, BIOS settings: hda:DMA, hdb:pio
Mar 10 13:06:09 submarine kernel: [17179573.308000] Probing IDE interface ide0...
Mar 10 13:06:09 submarine kernel: [17179574.044000] hda: MATSHITAUJ-832D, ATAPI CD/DVD-ROM drive
Mar 10 13:06:09 submarine kernel: [17179574.380000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar 10 13:06:09 submarine kernel: [17179574.392000] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(

```

---

