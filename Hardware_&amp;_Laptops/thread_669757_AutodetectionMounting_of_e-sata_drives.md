---
title: "Autodetection/Mounting of e-sata drives"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by NeneOnline on 2008-01-16
Hi All,

I am using Ubuntu 7.10 with default kernel 2.6.22-14 on i386 and I have an nvidia sata controller.

I have an external e-Sata drive and I wonder if there is a way to configure the system to get a similar experience to that of a USB stick which is automatically detected and mounted when it is plugged in.

I have been reading and it seems hotplug capability is supported sin kernel 2.6.19 for my chipset.

I can only mount the drive when it is already on when I boot the system. If it is turned on afterwards (this is, I boot the computer with the e-sata drive off) it is just not detected.

In fact it is not even listed when I execute "sudo mount -l" or "sudo lsscsi".

I have tried with "sudo scsiadd -s" command but no sucess. I am pasting the output just in case it might help:

```

could not add device 0 0 2 0 : Invalid argument
could not add device 0 0 3 0 : Invalid argument
could not add device 0 0 4 0 : Invalid argument
could not add device 0 0 5 0 : Invalid argument
could not add device 0 0 6 0 : Invalid argument
could not add device 0 0 7 0 : Invalid argument
could not add device 0 0 8 0 : Invalid argument
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD2500KS-00M Rev: 02.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ASUS     Model: Flash HS-CF      Rev: 3.95
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi2 Channel: 00 Id: 00 Lun: 01
  Vendor: ASUS     Model: Flash HS-COMBO   Rev: 3.95
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: Flash HS-CF      Rev: 4.44
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi3 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic  Model: Flash HS-COMBO   Rev: 4.44
  Type:   Direct-Access                    ANSI  SCSI revision: 00

```

And below the output in /var/log/messages

```

Jan 17 00:44:43 ubuntu-desktop kernel: [ 2284.644000] ata1: hard resetting port
Jan 17 00:44:43 ubuntu-desktop kernel: [ 2285.276000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 17 00:44:43 ubuntu-desktop kernel: [ 2285.292000] ata1.00: configured for UDMA/133
Jan 17 00:44:43 ubuntu-desktop kernel: [ 2285.292000] ata1: EH complete
Jan 17 00:44:43 ubuntu-desktop kernel: [ 2285.292000] ata1: hard resetting port
Jan 17 00:44:43 ubuntu-desktop kernel: [ 2285.292000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.924000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.940000] ata1.00: configured for UDMA/133
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.940000] ata1: EH complete
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.940000] sd 0:0:0:0: [sda] Write Protect is off
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.944000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.944000] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.944000] sd 0:0:0:0: [sda] Write Protect is off
Jan 17 00:44:44 ubuntu-desktop kernel: [ 2285.944000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

I would really appreciate if anyone could give me a hint. Am I trying something that is not supported?

Thanks to all,

Neneonline

---

