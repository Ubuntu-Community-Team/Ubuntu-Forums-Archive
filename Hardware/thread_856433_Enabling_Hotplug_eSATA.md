---
title: "Enabling Hotplug eSATA"
date: 2008-07-11
forum: Hardware
---

### Post by pseudonym on 2008-07-11
I have a 500GB Samsung HD501LJ SATA2 HDD in a CoolerMaster X-Craft drive enclosure. The USB connection works fine. eSATA works if the drive is plugged in at boot time, but can't be (safely) unplugged until shutdown.

My BIOS can set the SATA controllers to IDE or RAID mode. If I set it to RAID mode (while leaving each channel as IDE), hotplugging eSATA will work in Windows, but not in Linux. I have the latest BIOS for my motherboard (see sig below).

Here is some terminal output when set to RAID mode (it's essentially the same output when the SATA controllers are in IDE mode, except for the way they're named in lspci) - ```
dmesg | grep -i sda

[   34.337998] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   34.338055] sd 0:0:0:0: [sda] Write Protect is off
[   34.338102] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.338114] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.338201] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   34.338254] sd 0:0:0:0: [sda] Write Protect is off
[   34.338301] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.338311] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.338369]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.408349]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 sda10 >
[   34.479492] sd 0:0:0:0: [sda] Attached SCSI disk
[   43.788238] Adding 305192k swap on /dev/sda5.  Priority:-1 extents:1 across:305192k
[   44.210058] EXT3 FS on sda2, internal journal
[   44.603333] XFS mounting filesystem sda9
[   44.665154] Ending clean XFS mount for filesystem: sda9
[   44.724466] XFS mounting filesystem sda8
[   44.798687] Ending clean XFS mount for filesystem: sda8
[   45.098726] XFS mounting filesystem sda7
[   45.176809] Ending clean XFS mount for filesystem: sda7
```
```
dmesg | grep -i ata

[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[   28.312301] Memory: 2067064k/2097088k available (2177k kernel code, 28704k reserved, 1006k data, 368k init, 1179584k highmem)
[   28.312369]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   30.511856] libata version 3.00 loaded.
[   31.763433] sata_nv 0000:00:05.0: version 3.5
[   31.764520] scsi0 : sata_nv
[   31.765034] scsi1 : sata_nv
[   31.765192] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 16
[   31.765241] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 16
[   32.229384] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.237551] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-13, max UDMA7
[   32.237600] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   32.245533] ata1.00: configured for UDMA/133
[   32.557711] ata2: SATA link down (SStatus 0 SControl 300)
[   32.567987] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   32.568792] scsi2 : sata_nv
[   32.568935] scsi3 : sata_nv
[   32.569089] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 17
[   32.569139] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 17
[   32.876080] ata3: SATA link down (SStatus 0 SControl 300)
[   33.196434] ata4: SATA link down (SStatus 0 SControl 300)
[   33.207281] scsi4 : sata_nv
[   33.207433] scsi5 : sata_nv
[   33.207587] ata5: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb400 irq 18
[   33.207637] ata6: SATA max UDMA/133 cmd 0xbc00 ctl 0xb800 bmdma 0xb408 irq 18
[   33.670498] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.834255] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB04, max UDMA/100
[   34.006904] ata5.00: configured for UDMA/100
[   34.318181] ata6: SATA link down (SStatus 0 SControl 300)
[   34.332985] pata_amd 0000:00:04.0: version 0.3.10
[   34.333346] scsi6 : pata_amd
[   34.333429] scsi7 : pata_amd
[   34.333870] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   34.333919] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   34.333985] ata7: port disabled. ignoring.
[   34.334012] ata8: port disabled. ignoring.
[   34.800997] EXT3-fs: mounted filesystem with ordered data mode.
[  107.657311] ata4: hard resetting link
[  107.770440] ata4: SATA link down (SStatus 0 SControl 300)
[  107.774120] ata4: EH complete

```
```
lspci (trimmed)

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)

```
```
lsmod (trimmed)

Module                  Size  Used by
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  7 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_amd               14212  0 
ata_generic             8324  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
floppy                 59588  0 
sata_nv                27528  7 
pata_acpi               8320  0 
forcedeth              51980  0 
ehci_hcd               37900  0 
libata                159344  4 pata_amd,ata_generic,sata_nv,pata_acpi
ohci_hcd               25348  0 
scsi_mod              151436  4 sg,sd_mod,sr_mod,libata
usbcore               146028  4 usbhid,ehci_hcd,ohci_hcd

```
It's possible to coldplug the device using scsiadd (the external drive is on SATA channel 3 and I have the same type of drive as my internal one) - ```
sudo scsiadd -s 2 0

could not add device 2 0 1 0 : Invalid argument
could not add device 2 0 2 0 : Invalid argument
could not add device 2 0 3 0 : Invalid argument
could not add device 2 0 4 0 : Invalid argument
could not add device 2 0 5 0 : Invalid argument
could not add device 2 0 6 0 : Invalid argument
could not add device 2 0 7 0 : Invalid argument
could not add device 2 0 8 0 : Invalid argument
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG HD501LJ  Rev: CR10
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW SH-S203B  Rev: SB04
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG HD501LJ  Rev: CR10
  Type:   Direct-Access                    ANSI  SCSI revision: 05
```

I can then manually mount it. This works in both IDE and RAID mode. It's not a very elegant solution, however.

It was my understanding that later nVidia chipsets enable AHCI functions in both IDE and RAID mode. Clearly the sata_nv module is not picking this up.

Perhaps there's some special kernel parameter I need to set? Or something else?

Thanks.

---

### Post by pseudonym on 2008-07-12
bump

---

