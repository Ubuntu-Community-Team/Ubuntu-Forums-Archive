---
title: "CD drive problem (again!!!!)"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by Declan on 2005-12-17
I've never had a really satisfying time with the CD drive on this laptop (Toshiba A60-302).  Sometimes it doesn't work at all, sometimes it spins madly though there is nothing in it, sometimes it thinks that DVDs are bland CD-Rs. At the moment it refuses to recognise an audio disk.

The output from dmesg is:

[HTML][4295689.717000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295689.717000] hdc: packet command error: error=0x34 { AbortedCommand LastFailedSense=0x03 }
[4295689.717000] ide: failed opcode was: unknown
[4295689.717000] ATAPI device hdc:
[4295689.717000]   Error: Medium error -- (Sense key=0x03)
[4295689.717000]   (reserved error code) -- (asc=0x57, ascq=0x00)
[4295689.717000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295689.717000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295689.719000] cdrom: This disc doesn't have any tracks I recognize!
[4295689.723000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295689.723000] hdc: packet command error: error=0x34 { AbortedCommand LastFailedSense=0x03 }
[4295689.724000] ide: failed opcode was: unknown
[4295689.724000] ATAPI device hdc:
[4295689.724000]   Error: Medium error -- (Sense key=0x03)
[4295689.724000]   (reserved error code) -- (asc=0x57, ascq=0x00)
[4295689.724000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295689.724000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295689.728000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295689.728000] hdc: packet command error: error=0x34 { AbortedCommand LastFailedSense=0x03 }
[4295689.728000] ide: failed opcode was: unknown
[4295689.729000] ATAPI device hdc:
[4295689.729000]   Error: Medium error -- (Sense key=0x03)
[4295689.729000]   (reserved error code) -- (asc=0x57, ascq=0x00)
[4295689.729000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295689.729000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[/HTML]

Any ideas what any of that means?

Declan

---

### Post by mlomker on 2005-12-18
Does it work properly in Windows?  It could just be dying.

---

