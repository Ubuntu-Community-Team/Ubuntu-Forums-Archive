---
title: "Suspend and Texas Instruments 5in1 card reader."
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by am_pcguy on 2008-02-23
I have a Toshiba A130 and currently have everything working including suspend with one hitch.  After suspend the card reader does not work.

The card reader is listed in "lshw" as:
```
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7 module=tifm_7xx1

```
Dmesg shows the following related to the card
```
[48430.552000] mmcblk0: mmc0:b368 SDC   4020224KiB 
[48430.588000] usb 4-1: USB disconnect, address 2
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005040
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005040
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005054
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005054
[48430.620000] Buffer I/O error on device mmcblk0, logical block 0
[48430.620000] Buffer I/O error on device mmcblk0, logical block 0
[48430.620000] Buffer I/O error on device mmcblk0, logical block 0
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005055
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005055
[48430.620000] Buffer I/O error on device mmcblk0, logical block 1005055

```

I have to reboot before I can get the reader working again. 
I've attached the full dmesg, suspend occurs around line 525.

---

