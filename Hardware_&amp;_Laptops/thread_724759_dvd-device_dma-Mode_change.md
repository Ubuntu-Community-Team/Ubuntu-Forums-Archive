---
title: "dvd-device: dma-Mode change"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by KlausW on 2008-03-14
Helo!
I have a problem with the dvd-device under ubuntu, feisty fawn. U-dma 33 is activated, but it seems too fast, many io-errors.
So I want to reduce the dma-Mode. hdparm is not able to do this with -X-Option. In /etc/modules there is only fuse and lp. In /etc/modules.conf there is nothing in it.
In /etc/rcS.d hdparm is on position 21. At first not, I installed it there.
The dvd-device (IDE,ATA, not SATA) is ok, it works well under Knoppix and Win98. With ubuntu-installation-disk, it works, too.

kernel.log after dvd inserted:
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.713553] sr 1:0:0:0: SCSI error: return code = 0x08000002
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.713567] sr0: Current: sense key: Hardware Error
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.713573]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.713586] end_request: I/O error, dev sr0, sector 72
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.793186] sr 1:0:0:0: SCSI error: return code = 0x08000002
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.793200] sr0: Current: sense key: Hardware Error
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.793207]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
Mar 15 03:38:10 klaus-desktop kernel: [ 9506.793221] end_request: I/O error, dev sr0, sector 136

Hope for help!

:guitar:

---

