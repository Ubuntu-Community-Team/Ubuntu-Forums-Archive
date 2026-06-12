---
title: "Problems with SATA-controller: &quot;abnormal status ...&quot;"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by Marco Mans on 2005-12-20
Hi again!

I'm still trying to install ubuntu on my Toshiba Tecra S3.
But he's still having problems with the SATA drive.

I tried several things I saw in forums, but without any results :(
One solution I read was to set the SATA-controller to legacy ATA,
but unfortunately my BIOS doesn't have this option.

This is my lspci output:
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
**0000:00:1f.2 0106: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)**
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 15)
0000:05:05.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:05:0b.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:05:0b.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:05:0b.4 0805: Texas Instruments: Unknown device 8034


And this is what dmesg says:
<snip>
[4294673.537000] ata_piix version 1.03
[4294673.537000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[4294673.537000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294673.537000] ata1: SATA max UDMA/133 cmd 0xAF08 ctl 0xAF06 bmdma 0xAEE0 irq 19
[4294673.537000] ata2: SATA max UDMA/133 cmd 0xAEF8 ctl 0xAEF6 bmdma 0xAEE8 irq 19
[4294673.615000] usb 1-1: USB disconnect, address 2
[B][4294673.699000] ATA: abnormal status 0xFF on port 0xAF0F
[4294673.699000] ata1: disabling port[/B]
[4294673.699000] scsi0 : ata_piix
[4294673.787000] usb 1-1: new full speed USB device using uhci_hcd and address 3
**[4294673.862000] ATA: abnormal status 0xFF on port 0xAEFF**
**[4294673.862000] ata2: disabling port**
[4294673.862000] scsi1 : ata_piix
<snip>

Does anybody knows what I can do???

Thanks!

Marco Mans.

---

### Post by bastis0 on 2006-05-12
Hi,

Ich had the same Problem as you.
But now, with Dapper Drake Flight 7 it can be installed on Tecra S3 because now Dapper have the drivers for the new Intel 9xx Chips.
I write this with Dapper on my S3 ;o)

have fun and greetz,
Bastian

---

