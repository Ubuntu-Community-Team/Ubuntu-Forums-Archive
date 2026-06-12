---
title: "Problem with (SD) card reader"
date: 2008-05-11
forum: Hardware
---

### Post by bogoliubov on 2008-05-11
Hello. My card reader doesn't seem to work. I don't think it's the SD card itself.

When I insert the SD card, Ubuntu will mount it and it looks OK. But when I want to copy files (photos really) from the card to my HD, the card is unmounted and then remounted again. I can't copy more or less anything. 

If I let the SD card be in my digital camera, and plug it in through an USB cable, it works without any problems. 

lspci gives me:
05:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:07.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


and I checked kern.log for stuff about the crashing.  This is what I think may be relevant:
May 11 08:42:12 ubuntu-m540n kernel: [   87.494267] tifm_sd0:1 : card failed to respond for a long period of time (
12, 1)
May 11 08:42:12 ubuntu-m540n kernel: [   87.494613] tifm0 : demand removing card from socket 0:1
May 11 08:42:12 ubuntu-m540n kernel: [   87.494661] mmc1: card f715 removed
May 11 08:42:12 ubuntu-m540n kernel: [   87.494831] mmcblk0: error -123 sending read/write command
May 11 08:42:12 ubuntu-m540n kernel: [   87.494837] end_request: I/O error, dev mmcblk0, sector 52448

This last message is repeated many times.

May 11 08:42:12 ubuntu-m540n kernel: [   87.494986] mmcblk0: error -123 sending read/write command
May 11 08:42:12 ubuntu-m540n kernel: [   87.494991] end_request: I/O error, dev mmcblk0, sector 832
May 11 08:42:12 ubuntu-m540n kernel: [   87.494997] Buffer I/O error on device mmcblk0p1, logical block 589
May 11 08:42:12 ubuntu-m540n kernel: [   87.495001] lost page write due to I/O error on mmcblk0p1
May 11 08:42:12 ubuntu-m540n kernel: [   87.503760] mmcblk0: error -123 sending read/write command
May 11 08:42:12 ubuntu-m540n kernel: [   87.503766] end_request: I/O error, dev mmcblk0, sector 52448
May 11 08:42:12 ubuntu-m540n kernel: [   87.540424] FAT: Directory bread(block 493) failed

And this last message is repeated a zillion times!

---

### Post by catnap on 2008-05-12
The other option is a problem with the card reader. Perhaps you could try substituting another reader.

Cheers

---

### Post by bogoliubov on 2008-05-12
Well, the card reader is built into my laptop, so exchanging it means changing laptop, which I do not want, nor can afford.

Thanks anyway!

---

