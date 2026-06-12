---
title: "slow boot with ata revalidation errors"
date: 2008-04-27
forum: Hardware
---

### Post by teddmeister2 on 2008-04-27
Please help.  I need to know if my HDD is failing.  Basically I have a really slow boot with the following over and  over again in my dmesg:
```
[  525.860000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[  525.868000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[  525.868000] ata1.00: configured for UDMA/66
[  525.868000] ata1: EH complete
[  555.868000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  555.868000] ata1.00: cmd c8/00:08:2a:ad:4b/00:00:00:00:00/e8 tag 0 cdb 0x0 data 4096 in
[  555.868000]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  562.868000] ata1: port is slow to respond, please be patient (Status 0xd0)
[  585.884000] ata1: port failed to respond (30 secs, Status 0xd0)
[  585.884000] ata1: soft resetting port
[  586.048000] ATA: abnormal status 0xD0 on port 0x000101f7
[  586.048000] ATA: abnormal status 0xD0 on port 0x000101f7
[  586.048000] ATA: abnormal status 0xD0 on port 0x000101f7
[  586.048000] ATA: abnormal status 0xD0 on port 0x000101f7
[  586.048000] ATA: abnormal status 0xD0 on port 0x000101f7
[  586.348000] ata1.00: revalidation failed (errno=-2)
[  586.348000] ata1: failed to recover some devices, retrying in 5 secs
[  591.352000] ata1: soft resetting port
[  591.908000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[  591.916000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[  591.916000] ata1.00: configured for UDMA/66

```

Then I get the following in dmesg as  my computer decides to actually boot up:
```
[  591.916000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  591.916000] sda: Current [descriptor]: sense key: Aborted Command
[  591.916000]     Additional sense: No additional sense information
[  591.916000] Descriptor sense data with sense descriptors (in hex):
[  591.916000]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  591.916000]         00 00 00 00 
[  591.916000] end_request: I/O error, dev sda, sector 139177258
[  591.916000] ata1: EH complete
[  591.948000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[  591.948000] sda: Write Protect is off
[  591.948000] sda: Mode Sense: 00 3a 00 00
[  591.948000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  591.968000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[  591.968000] sda: Write Protect is off
[  591.968000] sda: Mode Sense: 00 3a 00 00
[  591.968000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  598.080000] NET: Registered protocol family 10
[  598.080000] lo: Disabled Privacy Extensions

```

Is this a hardware error?  What is it?  Do I have a hard drive or motherboard on the way out?  If it's not a hardware error, what kind of error is it, and how can I fix it?  Please help!

---

### Post by mccartyj on 2008-05-24
Same problem here...

[[COLOR="Red"]This thread has been talking a lot about it, but no definite solutions yet.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=770284&highlight=slow+boot+ata")

Very frustrating:mad:

---

