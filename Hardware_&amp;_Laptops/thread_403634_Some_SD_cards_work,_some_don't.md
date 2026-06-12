---
title: "Some SD cards work, some don't"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by Apreche on 2007-04-07
I own three flash memory cards. One is a 512MB Sandisk SD, one is a 1GB Corsair SD, and one is a 512MB Corsair Micro-SD with a normal SD adapter. I have a digital camera, a Wii and an external USB memory card reader. All of these cards work perfectly in all of these devices. 

However, my laptop, a Fujitsu P7230, has an internal memory card reader. Only the SANDisk card will work in this slot. If I try to put in the Corsair cards, I get errors. I'm currently running Fiesty, but that doesn't matter. The same problem happened when I tried to use Fiesty, Edgy and Dapper LiveCDs. I haven't tried windows, because this laptop is not dual-boot and I would have to reinstall. I also haven't tried any other distribution. A hardware problem has not been ruled out entirely, but is unlikely as this laptop is brand new and the slot DOES work with some cards. 

Here is the error I see in dmesg upon inserting a card that doesn't work.

```
[ 6190.760000] mmcblk0: mmc0:b368 SD    975360KiB 
[ 6190.764000]  mmcblk0:<3>mmcblk0: error 1 transferring data
[ 6190.768000] end_request: I/O error, dev mmcblk0, sector 0
[ 6190.768000] Buffer I/O error on device mmcblk0, logical block 0
[ 6190.768000] ldm_validate_partition_table(): Disk read failed.
[ 6190.768000] Dev mmcblk0: unable to read RDB block 0
[ 6190.768000]  unknown partition table
[ 6190.864000] mmcblk0: error 1 transferring data
[ 6190.864000] end_request: I/O error, dev mmcblk0, sector 1950592
[ 6190.864000] Buffer I/O error on device mmcblk0, logical block 243824
[ 6190.868000] mmcblk0: error 1 transferring data
[ 6190.868000] end_request: I/O error, dev mmcblk0, sector 1950592
[ 6190.868000] Buffer I/O error on device mmcblk0, logical block 243824
[ 6190.876000] mmcblk0: error 1 transferring data
[ 6190.876000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.876000] Buffer I/O error on device mmcblk0, logical block 243839
[ 6190.880000] mmcblk0: error 1 transferring data
[ 6190.880000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.880000] Buffer I/O error on device mmcblk0, logical block 243839
[ 6190.884000] mmcblk0: error 1 transferring data
[ 6190.884000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.884000] Buffer I/O error on device mmcblk0, logical block 243839
[ 6190.892000] mmcblk0: error 1 transferring data
[ 6190.892000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.892000] Buffer I/O error on device mmcblk0, logical block 243839
[ 6190.896000] mmcblk0: error 1 transferring data
[ 6190.896000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.896000] Buffer I/O error on device mmcblk0, logical block 243839
[ 6190.900000] mmcblk0: error 1 transferring data
[ 6190.900000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.900000] Buffer I/O error on device mmcblk0, logical block 243839
[ 6190.908000] mmcblk0: error 1 transferring data
[ 6190.908000] end_request: I/O error, dev mmcblk0, sector 1950656
[ 6190.908000] Buffer I/O error on device mmcblk0, logical block 243832
[ 6190.912000] mmcblk0: error 1 transferring data
[ 6190.912000] end_request: I/O error, dev mmcblk0, sector 1950704
[ 6190.916000] mmcblk0: error 1 transferring data
[ 6190.916000] end_request: I/O error, dev mmcblk0, sector 1950712
[ 6190.924000] mmcblk0: error 1 transferring data
[ 6190.924000] end_request: I/O error, dev mmcblk0, sector 1950712

```

Here is what lspci says about the card reader. 
```
08:03.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSP
08:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (re
08:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)
```

---

