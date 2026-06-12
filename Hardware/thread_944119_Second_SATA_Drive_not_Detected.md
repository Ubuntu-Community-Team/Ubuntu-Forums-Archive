---
title: "Second SATA Drive not Detected"
date: 2008-10-11
forum: Hardware
---

### Post by ceiling on 2008-10-11
Hello,

I have a working installation of Hardy 8.04 on a SATA drive, which is dual botting with Windows XP.  I installed a second SATA drive, and it works fine with Windows.  It does not show up at all in Linux.  Here is the relevant excerpt from dmesg:

> [ 33.464422] scsi0 : pata_via
[   33.471444] scsi1 : pata_via
[   33.473025] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   33.473029] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   33.473076] ata1: port disabled. ignoring.
[   33.479422] USB Universal Host Controller Interface driver v3.0
[   33.806773] ata2.00: ATAPI: LITE-ON DVDRW SHW-160P6S, PS0B, max UDMA/66
[   33.806791] ata2.00: limited to UDMA/33 due to 40-wire cable
[   33.986013] ata2.00: configured for UDMA/33
[   33.987012] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-160P6S PS0B PQ: 0 ANSI: 5
[   33.989877] sata_via 0000:00:0f.0: version 2.3
[   33.989912] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 17
[   33.989959] sata_via 0000:00:0f.0: routed to hard irq line 10
[   33.992303] scsi2 : sata_via
[   33.993541] scsi3 : sata_via
[   33.994996] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[   33.995000] ata4: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[   34.197109] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.360941] ata3.00: ATA-7: HDT722516DLA380, V43OA9BA, max UDMA/133
[   34.360947] ata3.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   34.376880] ata3.00: configured for UDMA/133
[   34.579858] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   34.735377] ata: SEMB device ignored
[   34.735561] scsi 2:0:0:0: Direct-Access     ATA      HDT722516DLA380  V43O PQ: 0 ANSI: 5
[   34.736328] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18

and lspci:
> 
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0a.0 Multimedia video controller: Conexant CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600/X1650 PRO]
01:00.1 Display controller: ATI Technologies Inc RV530LE [Radeon X1650 PRO] (Secondary)

I've read other threads on non-working SATA drives, and they seem to mostly be issues where no SATA drives show up for installation.  In many cases it seems that the BIOS AHCI setting needs to be on for ubuntu to recognize the drive.  My BIOS doesn't seem to have this setting.  There is a SATA-IDE parameter that can either be 'IDE' 'RAID' or 'DISABLED'.  SATA or RAID seem to give the same results, and 'DISABLED' disables both hard drives.  

Any advice would be appreciated, let me know if you need any more information to help solve the problem.

---

### Post by fj1200 on 2008-10-11
"lsmod" will give you a hint on what drivers are loaded...

---

### Post by ceiling on 2008-10-11
Here are some of the relavant lines from lsmod:

> 
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  3 
ata_generic             8324  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
sata_via               12420  2 
pata_via               13316  1 
usbcore               146028  6 usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
libata                159344  4 pata_acpi,ata_generic,sata_via,pata_via
scsi_mod              151436  4 sr_mod,sg,sd_mod,libata


---

