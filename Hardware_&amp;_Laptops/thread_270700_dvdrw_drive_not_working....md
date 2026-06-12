---
title: "dvdrw drive not working..."
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by PixelCloud on 2006-10-03
trying to mount a cd results in

```
[17180513.812000] ide: failed opcode was: unknown
[17180513.812000] end_request: I/O error, dev hdb, sector 262148
[17180609.180000] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17180609.180000] hdb: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17180609.180000] ide: failed opcode was: unknown
[17180609.412000] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[17180609.412000] hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17180609.412000] ide: failed opcode was: unknown
[17180609.412000] end_request: I/O error, dev hdb, sector 64
[17180609.416000] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
```

the cdrom drive shows up in the bios and in kubuntu

---

