---
title: "CD drive not available after suspend/resume"
date: 2014-01-05
forum: Hardware
---

### Post by elliecleo on 2014-01-05
Running Mint 15 Olivia/Ubuntu 13.4 Raring on an HP laptop, x86_64, AMD quad core.

After suspend/resume, I cannot access the CD drive.  Found the following in kernel.log:

On boot (Drive is recognized and installed):
```
Dec 20 14:34:09 drifter kernel: [    4.652474] ahci 0000:00:11.0: version 3.0
Dec 20 14:34:09 drifter kernel: [    4.652564] ahci 0000:00:11.0: irq 50 for MSI/MSI-X
Dec 20 14:34:09 drifter kernel: [    4.652635] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
Dec 20 14:34:09 drifter kernel: [    4.652641] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
Dec 20 14:34:09 drifter kernel: [    4.656556] scsi0 : ahci
Dec 20 14:34:09 drifter kernel: [    4.659857] scsi1 : ahci
Dec 20 14:34:09 drifter kernel: [    4.660074] ata1: SATA max UDMA/133 abar m2048@0xf0350000 port 0xf0350100 irq 50
Dec 20 14:34:09 drifter kernel: [    4.660080] ata2: SATA max UDMA/133 abar m2048@0xf0350000 port 0xf0350180 irq 50
Dec 20 14:34:09 drifter kernel: [    5.149029] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 20 14:34:09 drifter kernel: [    5.149060] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 20 14:34:09 drifter kernel: [    5.150810] ata1.00: ATA-8: Hitachi HTS547564A9E384, JEDOA50A, max UDMA/100
Dec 20 14:34:09 drifter kernel: [    5.150816] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec 20 14:34:09 drifter kernel: [    5.152676] ata1.00: configured for UDMA/100
Dec 20 14:34:09 drifter kernel: [    5.152920] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54756 JEDO PQ: 0 ANSI: 5
Dec 20 14:34:09 drifter kernel: [    5.153156] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Dec 20 14:34:09 drifter kernel: [    5.153161] sd 0:0:0:0: [sda] 4096-byte physical blocks
Dec 20 14:34:09 drifter kernel: [    5.153192] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 20 14:34:09 drifter kernel: [    5.153250] sd 0:0:0:0: [sda] Write Protect is off
Dec 20 14:34:09 drifter kernel: [    5.153255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 20 14:34:09 drifter kernel: [    5.153288] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 20 14:34:09 drifter kernel: [    5.159488] ata2.00: ATAPI: hp      DVD A  DS8A8SH, KH63, max UDMA/100
Dec 20 14:34:09 drifter kernel: [    5.166081] ata2.00: configured for UDMA/100
Dec 20 14:34:09 drifter kernel: [    5.179637] scsi 1:0:0:0: CD-ROM            hp       DVD A  DS8A8SH   KH63 PQ: 0 ANSI: 5
Dec 20 14:34:09 drifter kernel: [    5.194015] sr0: scsi3-mmc drive: 16x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 20 14:34:09 drifter kernel: [    5.194020] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 20 14:34:09 drifter kernel: [    5.194349] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 20 14:34:09 drifter kernel: [    5.194490] sr 1:0:0:0: Attached scsi generic sg1 type 5
```

On Resume (ata1 SATA link up; ata2 SATA link down):
```
Dec 21 15:35:07 drifter kernel: [72830.579703] ata2: SATA link down (SStatus 0 SControl 310)
Dec 21 15:35:07 drifter kernel: [72831.645762] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 21 15:35:07 drifter kernel: [72831.649299] ata1.00: configured for UDMA/100
Dec 21 15:35:07 drifter kernel: [72831.661766] sd 0:0:0:0: [sda] Starting disk
```


This behavior occurs since updating from Mint 14/Ubuntu 12.10, where resume worked great.

I've asked the Google, but can't seem to find quite the same issue.  I'd appreciate any pointers as to where I might look to track this down.

Thanks,
Wongo

---

### Post by Yellow Pasque on 2014-01-05
What model HP is it? Make sure your BIOS is up to date and that there are no CD firmware updates available.

---

### Post by elliecleo on 2014-01-06
Thanks for taking the time to reply, Temüjin.

The laptop is HP g7-2275dx.  I took some time tonight to boot to Windows, and update BIOS and optical FW.

Returned to Linux, (ripped the CD that finally prompted me to post the question,) suspended, resumed, and have the same behavior.

Any other ideas?

Thanks,
Wongo

---

### Post by tgalati4 on 2014-01-07
Install *acpitool* and see if you can leave power to the bus during suspend.  Open a terminal:

```
sudo apt-get install acpitool
acpitool -w
```

Another work-around would be to add the correct module (like sata) to /etc/default/acpi-support so that it gets reloaded after resume.

I would go through the kernel upgrade release notes to see if you can identify the change that may have happened that would effect SATA suspend/resume behavior.  It might be worth filing a bug since this is a regression--something that was working but now longer works with a newer distro.

---

### Post by elliecleo on 2014-01-08
Thanks, tgalati4, for your reply.

Installed acpitool, and get the following results:

```
$ acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SPB1      S5    *disabled  pci:0000:00:15.1
  2. XPDV      S5    *enabled   pci:0000:05:00.0
  3. OHC1      S3    *enabled   pci:0000:00:12.0
  4. OHC2      S3    *enabled   pci:0000:00:13.0
  5. OHC3      S3    *disabled
  6. OHC4      S3    *disabled
  7. EHC1      S3    *enabled   pci:0000:00:12.2
  8. EHC2      S3    *enabled   pci:0000:00:13.2
  9. EHC3      S3    *disabled
  10. XHC0      S3    *enabled   pci:0000:00:10.0
  11. XHC1      S3    *enabled   pci:0000:00:10.1
  12. KBC0      S3    *enabled   pnp:00:06
  13. PS2M      S3    *disabled  pnp:00:07
```

SATA controller is PCI 00:11.0:
```
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [AHCI mode]
```
... and does not appear to be listed w/ acpitool -w.  I assume that indicates your first suggestion will not work.

Best I can tell, the SATA driver is ahci, along with libahci.  There is no "sata" module.  I added "ahci libahci" to the MODULES directive in /etc/default/acpi-support.  No change.

I'll try to work through the kernel/module history and see if I see anything relevant.

Thanks for the suggestions,
Wongo

---

### Post by bobmao78 on 2015-01-03
I am on Ubuntu 14.04LTS, and currently stuck at the same problem.  Would very much appreciate knowing how to get the /dev/sr0 back without rebooting.  Thanks in advance.

---

