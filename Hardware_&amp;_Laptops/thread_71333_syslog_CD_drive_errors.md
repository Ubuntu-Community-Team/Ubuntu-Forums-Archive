---
title: "syslog CD drive errors"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by vayu on 2005-10-03
My syslog shows a page full of the below errors for every login.  The drive plays CDs and DVD videos fine.  I should test it writing and reading a computer format, but it does play fine.  I enabled dma through hdparm.conf.  Any ideas what these errors mean and how to get rid of them?  If nothing else it seems it must be slowing my boot times.  These are just a few lines but the log actually has a long list of them.


```
Oct  2 22:50:49 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct  2 22:50:49 localhost kernel: hdc: command error: error=0x54
Oct  2 22:50:49 localhost kernel: ide: failed opcode was 100
Oct  2 22:50:49 localhost kernel: end_request: I/O error, dev hdc, sector 64
Oct  2 22:50:49 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct  2 22:50:49 localhost kernel: hdc: command error: error=0x54
Oct  2 22:50:49 localhost kernel: ide: failed opcode was 100
Oct  2 22:50:49 localhost kernel: end_request: I/O error, dev hdc, sector 743836
Oct  2 22:50:49 localhost kernel: hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Oct  2 22:50:49 localhost kernel: hdc: command error: error=0x54
Oct  2 22:50:49 localhost kernel: ide: failed opcode was 100

```

---

