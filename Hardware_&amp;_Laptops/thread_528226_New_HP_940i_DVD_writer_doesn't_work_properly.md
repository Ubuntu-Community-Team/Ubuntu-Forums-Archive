---
title: "New HP 940i DVD writer doesn't work properly"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by kdbaas on 2007-08-17
Hi, I bought a new HP 940i dvd writer today, to replace my faulty cd writer. The writer works in Windows XP, but doesn't in Ubuntu Feisty:

The writer does not mount all media I insert, and the ones it does -  I can browse them, but not open files (except for simple text files). (It seems to think all files are text files)
(Update) Browsing an old Feisty LiveCD displays the same problems, i.e. I can't open the files on the disk. However, I can boot off the disk without problems. Unfortunately I only have one optical drive in my system, so I couldn't test burning capabilities in the liveCD environment.

Burning does not work completely either, but haven't tested beyond the few coasters I created.
(Update) Burning seems to work mostly, but disks are unreadable in Ubuntu. Readable in Windows XP though. DVD Videos not playable on standalone dvdplayers though.

dmesg says, after inserting media:

```

[ 2358.769952] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 2358.769957] sr0: Current: sense key: Hardware Error
[ 2358.769959]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2358.769966] end_request: I/O error, dev sr0, sector 64
[ 2358.769969] Buffer I/O error on device sr0, logical block 8
[ 2358.875990] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 2358.875997] sr0: Current: sense key: Hardware Error
[ 2358.876000]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2358.876007] end_request: I/O error, dev sr0, sector 80
[ 2358.876011] Buffer I/O error on device sr0, logical block 10
[ 2358.876017] Buffer I/O error on device sr0, logical block 11
[ 2358.876021] Buffer I/O error on device sr0, logical block 12
[ 2358.876024] Buffer I/O error on device sr0, logical block 13
[ 2358.876028] Buffer I/O error on device sr0, logical block 14
[ 2358.876031] Buffer I/O error on device sr0, logical block 15
[ 2358.876035] Buffer I/O error on device sr0, logical block 16
[ 2358.876038] Buffer I/O error on device sr0, logical block 17
[ 2358.916758] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 2358.916765] sr0: Current: sense key: Hardware Error
[ 2358.916769]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2358.916776] end_request: I/O error, dev sr0, sector 64
[ 2358.919514] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 2358.919520] sr0: Current: sense key: Hardware Error
[ 2358.919523]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2358.919529] end_request: I/O error, dev sr0, sector 64
[ 2358.922076] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 2358.922083] sr0: Current: sense key: Hardware Error
[ 2358.922086]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2358.922093] end_request: I/O error, dev sr0, sector 64
[ 2358.924710] sr 1:0:0:0: SCSI error: return code = 0x08000002
[ 2358.924715] sr0: Current: sense key: Hardware Error
[ 2358.924718]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 2358.924724] end_request: I/O error, dev sr0, sector 64

```

How can I resolve this?

Thanks

Klaas

---

