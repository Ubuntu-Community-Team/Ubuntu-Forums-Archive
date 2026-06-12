---
title: "SATA controller for Intel ICH7 family"
date: 2009-07-07
forum: Hardware
---

### Post by chalkie1975 on 2009-07-07
I have a netbook with the ICH7 family chip inside

lspci gives me:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

and dmesg | grep ata gives me:

[    0.732259] libata version 3.00 loaded.
[    2.451295] ata1: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444500 irq 2299
[    2.451309] ata2: DUMMY
[    2.451317] ata3: SATA max UDMA/133 abar m1024@0xf0444400 port 0xf0444600 irq 2299
[    2.451328] ata4: DUMMY
[    2.768070] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.768871] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.822259] ata1.00: ATA-8: TOSHIBA MK1655GSX, FG011M, max UDMA/100
[    2.822279] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.823411] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.823589] ata1.00: configured for UDMA/100
[    3.156065] ata3: SATA link down (SStatus 0 SControl 300)
[    3.312135] ata_piix 0000:00:1f.1: version 2.12
[    3.312156] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.312218] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.312360] scsi4 : ata_piix
[    3.312506] scsi5 : ata_piix
[    3.313573] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.313587] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.468199] ata6: port disabled. ignoring.

I have already blacklisted ata_generic in order to get the kernel to use Libata instead of standard IDE compatibility mode, and my hard drive is a SATA II compliant 3Gbps speed disk - (google the model - MK1655GSX). I have select AHCI mode for the SATA in the bios (the other is 'compatibility' mode) yet i'm stuck with SATA speeds of 1.5Gbps only... and i've search all over for a solution to speed up the disk.

If i run hdparm -tT /dev/sda I get:

Timing cached reads:   1218 MB in  2.00 seconds = 609.26 MB/sec
Timing buffered disk reads:  176 MB in  3.01 seconds =  58.54 MB/sec

On a jumperless toshiba HDD, how can i speed up the disk to SATAII under Linux?:-({|=

---

### Post by damis648 on 2009-07-07
While the drive supports SATA II speeds, the actual disk may not actually be able to attain that speed perhaps.

---

### Post by chalkie1975 on 2009-07-28
Actually I found the answer : [http://www.macosxhints.com/article.php?story=20080215072351407](http://www.macosxhints.com/article.php?story=20080215072351407)

It seems that the ICH7-M AHCI controller does not support the SATAII standard and therefore only runs at 1.5GB/s

:O(

---

