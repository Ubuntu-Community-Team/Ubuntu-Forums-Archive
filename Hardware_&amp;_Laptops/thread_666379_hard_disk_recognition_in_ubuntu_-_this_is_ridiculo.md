---
title: "hard disk recognition in ubuntu - this is ridiculous!"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Kenobi on 2008-01-13
Hi,

generally I love ubuntu but there is a really ridiculous issue: my new computer comes with two hard drives; the first is an old IDE, the second is an IDE too but had (for some issues) to be installed on SATA with an adapter.

Well, Windows XP (you know how old that is?) recognices both drives on installation and everything is fine. Ubuntu 7.04 Setup doesn't even know that my second drive exists or, if I try to persuade it, it sais something with "failed to set xfer mode" (dont ask - I tried all the quick-fixes).

OK, you might say: "**Yeah, Microsoft has all the fancy drivers that help it - if we just had the drivers we could do it, too...**" - RUBBISH!

[COLOR="DarkRed"]Just for fun I tried the oldest Linux I have, it is called **"Red Linux V.8"** and it is from **[COLOR="Red"]1999[/COLOR]** and you know what it does? During installation it recognised both hard drives and even recognised (just to tease me) all partitions on both drives, plus drive names, and right sizes![/COLOR]

**[COLOR="Red"]Can anybody tell me WHAT ON EARTH took Ubuntu 9 years and it doesn't even work NOW???[/COLOR]** 

(If I only knew whom to blame...)

---

### Post by Kenobi on 2008-01-29
I found out that the hard disk is working fine under Suse Linux 10.3. The hard disk concerned is the ST3160021A



<5>scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL11 PQ: 0 ANSI: 5
<5>scsi 0:0:1:0: Direct-Access     ATA      ST320423A        3.02 PQ: 0 ANSI: 5
<7>ahci 0000:00:0a.0: version 3.0
<4>ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
<6>ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 16
<6>ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
<6>ahci 0000:00:0a.0: flags: 64bit ncq sntf pm led clo pmp pio 
<7>PCI: Setting latency timer of device 0000:00:0a.0 to 64
<6>scsi2 : ahci
<6>scsi3 : ahci
<6>scsi4 : ahci
<6>scsi5 : ahci
<6>ata3: SATA max UDMA/133 cmd 0xf8820100 ctl 0x00000000 bmdma 0x00000000 irq 222
<6>ata4: SATA max UDMA/133 cmd 0xf8820180 ctl 0x00000000 bmdma 0x00000000 irq 222
<6>ata5: SATA max UDMA/133 cmd 0xf8820200 ctl 0x00000000 bmdma 0x00000000 irq 222
<6>ata6: SATA max UDMA/133 cmd 0xf8820280 ctl 0x00000000 bmdma 0x00000000 irq 222
<6>ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
<6>ata3.00: HPA unlocked: 312579695 -> 312581808, native 312581808
<6>ata3.00: ATA-6: ST3160021A, 8.01, max UDMA/100
<6>ata3.00: 312581808 sectors, multi 16: LBA48 
<6>ata3.00: applying bridge limits
<6>ata3.00: configured for UDMA/100
<6>ata4: SATA link down (SStatus 0 SControl 300)
<6>ata5: SATA link down (SStatus 0 SControl 300)
<6>ata6: SATA link down (SStatus 0 SControl 300)
<5>scsi 2:0:0:0: Direct-Access     ATA      ST3160021A       8.01 PQ: 0 ANSI: 5
<6>BIOS EDD facility v0.16 2004-Jun-25, 2 devices found

[B]Ubuntu 7.10 only sais:
b2c2-flexcop: i2c master_xfer failed[/B]

but I don't want Suse I want Ubuntu so what can I do?

---

