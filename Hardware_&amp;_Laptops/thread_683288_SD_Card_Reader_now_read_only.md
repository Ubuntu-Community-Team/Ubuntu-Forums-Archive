---
title: "SD Card Reader now read only"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Joe_CoT on 2008-01-30
Strangely, the SD card reader in this laptop now shows to be read only. This is on the hardware level, from the time the card is inserted. From the dmesg:
```
[102586.472000] mmcblk0: mmc0:1234 SD04G 4018176KiB (ro)
[102586.472000]  mmcblk0: p1
```

note the (ro) part.
Therefore, the SD card mounts, but I can't write to it. I can't edit its partition table in fdisk. The card is not hardware locked, and I just deleted files off of it from the camera.

Also, relevant info from lspci
```
05:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
05:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
05:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```

Any ideas?
**UPDATE**: for further clarification, I just plugged the card into a usb reader. I recreated the partition table and partition, and formatted it fat32. Works fine on the USB reader, it still isn't working on the built-in one.

---

