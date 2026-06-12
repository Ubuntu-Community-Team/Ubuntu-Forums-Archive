---
title: "SD card doesn't mount"
date: 2016-09-10
forum: Hardware
---

### Post by piu130 on 2016-09-10
I insert a SD card in the SD slot and nothing happens.

dmsg:
```
[  451.002871] mmc0: new high speed SDHC card at address aaaa
[  451.005663] mmcblk0: mmc0:aaaa SD04G 3.69 GiB 
[  451.008870]  mmcblk0: p1
```

fdisk -l:
```
Disk /dev/mmcblk0: 3.7 GiB, 3965190144 bytes, 7744512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000eeff6
```

lspci -v:
```
07:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader (rev 01)
        Subsystem: Hewlett-Packard Company RTL8411 PCI Express Card Reader
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at 61600000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [b0] MSI-X: Enable- Count=1 Masked-
        Capabilities: [d0] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: rtsx_pci
        Kernel modules: rtsx_pci
```

I tried to mount it with ```
mount /dev/mmcblk0 /mnt/
``` with -t vfat/auto but it always returns
```
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0,
       missing codepage or helper program, or other error
```

Do I need a driver for RTL8411 PCI Express Card Reader? Or whats the problem?

I tried the solution from an other post restarting the PC but that doesn't work. I found an other solution to unplug the SD card reader or deactivate it in the BIOS and plug it in/activate it again. But I don't have an option to deactivate/activate and I can't unplug the SD card reader.

I have Kubuntu 16.04 Kernel version 4.4.0-36-generic (new Kubuntu installation).

Sorry for the bad formatting. I'm new to this forum and don't know the syntaxes.

---

### Post by Bucky Ball on 2016-09-10
Welcome. Please install exfat-utils and exfat-fuse and try again. They are in the Ubuntu software repositories (Software Centre, but not sure what it's called now). :)

That should be all you need. You're not missing drivers for the card reader, just for the SDHC cards.

If this fixes, please mark thread as solved using Thread Tools at the top right (or see link in my signature).

PS: Your use of code tags is ideal. Nothing wrong with the formatting. :)

---

