---
title: "udisks-daemon and SATA errors"
date: 2010-05-18
forum: Hardware
---

### Post by EReckase on 2010-05-18
Having just installed Lucid I've been keeping an eye on my system log to make sure all is well, and I started getting frequent SATA disk errors on one of my archive drives shortly after the installation.  Watching the active processes on the machine, I'll see 'udisks-daemon' start up (on the hour or 30 minutes, mostly) and then I'll get the following messages in my system log:

```
May 18 13:29:20 flame64 kernel: [159327.828533] ata3: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
May 18 13:29:20 flame64 kernel: [159327.828538] ata3: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
May 18 13:29:20 flame64 kernel: [159327.828539]   dhfis 0x1 dmafis 0x0 sdbfis 0x0
May 18 13:29:20 flame64 kernel: [159327.828543] ata3: ATA_REG 0x41 ERR_REG 0x84
May 18 13:29:20 flame64 kernel: [159327.828545] ata3: tag : dhfis dmafis sdbfis sacitve
May 18 13:29:20 flame64 kernel: [159327.828547] ata3: tag 0x0: 1 0 0 1  
May 18 13:29:20 flame64 kernel: [159327.828558] ata3.00: exception Emask 0x1 SAct 0x1 SErr 0x0 action 0x6 frozen
May 18 13:29:20 flame64 kernel: [159327.828561] ata3.00: Ata error. fis:0x21
May 18 13:29:20 flame64 kernel: [159327.828564] ata3.00: failed command: READ FPDMA QUEUED
May 18 13:29:20 flame64 kernel: [159327.828570] ata3.00: cmd 60/00:00:3f:7a:96/02:00:5a:00:00/40 tag 0 ncq 262144 in
May 18 13:29:20 flame64 kernel: [159327.828571]          res 41/84:04:3f:7a:96/84:00:5a:00:00/40 Emask 0x10 (ATA bus error)
May 18 13:29:20 flame64 kernel: [159327.828574] ata3.00: status: { DRDY ERR }
May 18 13:29:20 flame64 kernel: [159327.828576] ata3.00: error: { ICRC ABRT }
May 18 13:29:20 flame64 kernel: [159327.828583] ata3: hard resetting link

```

I'm in the process of running fsck on the drive, but it's less than 6 months old, a 1.5 tb Samsung drive (I think - it's hard to match the ata# to the drive designator).  Can anyone explain what is causing this problem?

---

### Post by gordintoronto on 2010-05-18
It's not unusual for large drives to fail when they are still quite young. See:
[http://www.newegg.ca/Product/ProductReview.aspx?Item=22-152-175&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=](http://www.newegg.ca/Product/ProductReview.aspx?Item=22-152-175&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Page=1&Keywords=)

On newegg, 15% of the people who wrote reviews for that drive gave it one or two stars out of five. That's actually good, compared to other 1 TB+ drives.

When I built a new computer last summer, I went with a WD "Black" 640 GB drive, which has 9% one or two stars.

---

### Post by EReckase on 2010-05-18
Note that smartctl doesn't report anything wrong with the drive, so it seems more likely that it's a controller, or a cable, or something like that.  I'm currently running udisks --monitor-detail to wait for it to happen again...

---

