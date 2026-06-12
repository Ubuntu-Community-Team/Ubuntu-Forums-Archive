---
title: "DVD spindown jams DVD-drive"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by samwyse on 2007-06-06
When leaving a movie on pause or in the DVD-menus until the drive spins down and trying to continue the movie, the drive starts "raping" the DVD. Nothing can be done except hitting the eject button. Workaround: don't leave a movie on pause for too long. The drive is a Samsung DVD Writer SH-S162L.

Here's the log errors:

```
07.06.2007 03:05:10	localhost	kernel	[52203.341602] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }

07.06.2007 03:05:10	localhost	kernel	[52203.341610] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }

07.06.2007 03:05:10	localhost	kernel	[52203.341614] ide: failed opcode was: unknown
```

Any idea what's going on?

---

