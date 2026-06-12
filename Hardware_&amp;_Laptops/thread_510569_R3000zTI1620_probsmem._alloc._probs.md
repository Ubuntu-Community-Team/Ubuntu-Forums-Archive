---
title: "R3000z/TI1620 probs/mem. alloc. probs"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by Kejan33 on 2007-07-26
Hi.  I have an R3000z with TI1620 5-1 card reader (in PCMCIA slot??) but despite reading a lot of info re:loading modules (works in earlier versions of Ubuntu), I still cant get SD or MMC cards to be recognized.  Also, at boot, there is a flash of a mem. allocation error and in dmesg, there is indication of PCI hidden behind bridge.  Attached are some lines of the dmesg. report.  Is there ANY work around this to get the SD/MMC cards to be read?  

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)

[   10.925087] ACPI: bus type pci registered
[   10.925134] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[   10.925136] PCI: Using configuration type 1
[   10.925137] Setting up standard PCI resources
[   10.926816] ACPI: Interpreter enabled
[   10.926818] ACPI: Using IOAPIC for interrupt routing
[   10.927126] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.927129] PCI: Probing PCI hardware (bus 00)
[   10.927720] PCI: Bus #03 (-#06) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[   10.927722] Please report the result to linux-kernel to fix this permanently
[   10.927746] PCI: Bus #07 (-#0a) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[   10.927748] Please report the result to linux-kernel to fix this permanently

[   11.008160] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.0
[   11.008208] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.1

---

