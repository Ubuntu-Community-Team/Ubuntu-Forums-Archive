---
title: "feisty freezes for short time"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by toh on 2007-07-02
Good morning!

I need help for the following Problem:

Sometimes Feisty suddenly freezes while working (doesn't matter which application is
running). After a minute or so Feisty "wakes up" and I can continue working at the
very point it had frozen.
(No data loss - no restarts necessary)

Here's an example of what what the System Log delivers:

> Jun 28 16:31:07 ubuFawn kernel: [  891.680000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

Jun 28 16:31:07 ubuFawn kernel: [  891.680000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in

Jun 28 16:31:07 ubuFawn kernel: [  891.680000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)

Jun 28 16:31:14 ubuFawn kernel: [  898.680000] ata1: port is slow to respond, please be patient (Status 0xd0)

Jun 28 16:31:37 ubuFawn kernel: [  921.696000] ata1: port failed to respond (30 secs, Status 0xd0)

Jun 28 16:31:37 ubuFawn kernel: [  921.696000] ata1: soft resetting port

Jun 28 16:31:38 ubuFawn kernel: [  922.024000] ata1.00: ata_hpa_resize 1: sectors = 141398112, hpa_sectors = 156301488

Jun 28 16:31:38 ubuFawn kernel: [  922.024000] ata1.00: Host Protected Area detected.

Jun 28 16:31:38 ubuFawn kernel: [  922.024000]      current size : 141398112 sectors (72395 MB)

Jun 28 16:31:38 ubuFawn kernel: [  922.024000]      native  size : 156301488 sectors (80026 MB)

Jun 28 16:31:38 ubuFawn kernel: [  922.024000] ata1.00: SET of native returned 0, expected 156301488

Jun 28 16:31:38 ubuFawn kernel: [  922.032000] ata1.00: ata_hpa_resize 1: sectors = 141398112, hpa_sectors = 156301488

Jun 28 16:31:38 ubuFawn kernel: [  922.032000] ata1.00: Host Protected Area detected.

Jun 28 16:31:38 ubuFawn kernel: [  922.032000]      current size : 141398112 sectors (72395 MB)

Jun 28 16:31:38 ubuFawn kernel: [  922.032000]      native  size : 156301488 sectors (80026 MB)

Jun 28 16:31:38 ubuFawn kernel: [  922.032000] ata1.00: SET of native returned 0, expected 156301488

Jun 28 16:31:38 ubuFawn kernel: [  922.032000] ata1.00: configured for UDMA/100

Jun 28 16:31:38 ubuFawn kernel: [  922.196000] ata1.01: configured for UDMA/33

Jun 28 16:31:38 ubuFawn kernel: [  922.196000] ata1: EH complete

Jun 28 16:31:38 ubuFawn kernel: [  922.212000] SCSI device sda: 141398112 512-byte hdwr sectors (72396 MB)

Jun 28 16:31:38 ubuFawn kernel: [  922.228000] sda: Write Protect is off

Jun 28 16:31:38 ubuFawn kernel: [  922.228000] sda: Mode Sense: 00 3a 00 00

Jun 28 16:31:38 ubuFawn kernel: [  922.252000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Jun 28 16:31:38 ubuFawn kernel: [  922.676000] SCSI device sda: 141398112 512-byte hdwr sectors (72396 MB)

Jun 28 16:31:38 ubuFawn kernel: [  922.680000] sda: Write Protect is off

Jun 28 16:31:38 ubuFawn kernel: [  922.680000] sda: Mode Sense: 00 3a 00 00

Jun 28 16:31:38 ubuFawn kernel: [  922.700000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA



Thanx for help!

Thomas

---

### Post by ndefontenay on 2007-07-02
```
Jun 28 16:31:14 ubuFawn kernel: [ 898.680000] ata1: port is slow to respond, please be patient (Status 0xd0)

Jun 28 16:31:37 ubuFawn kernel: [ 921.696000] ata1: port failed to respond (30 secs, Status 0xd0)
```

That could be a potential reason for your problem. I wonder if it's waiting some answer for a while and freezes the whole thing during that time...

---

### Post by toh on 2007-07-03
.....how can I solve the problem????

Thomas

---

