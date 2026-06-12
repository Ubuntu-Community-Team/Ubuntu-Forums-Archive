---
title: "MicroSD card is no longer automounted in 10.04"
date: 2010-08-13
forum: Hardware
---

### Post by kfhughes on 2010-08-13
I hadn't noticed this until this week, so not sure when it started but it definitely worked under 9.10.  I have a laptop with the TI PCIxx12 Cardbus Controller and the 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD):

# lspci -s 04:09
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
# 

When I insert a microSD card using an adapter into the SD card slot, all I get is the following log message:

tifm_core: MMC/SD card detected in socket 0:1

/dev/mmcblk0 and /dev/mmcblk0p? are not created by udev. In order to get the card to work, I need to do the following (after the card is inserted):

sudo setpci -s 04:09.2 4c.b=0x02
sudo setpci -s 04:09.2 4c.b=0x00

Anyone have an idea what changed?  I'm running the 2.6.32-24-generic x86_64 kernel, if that helps.

---

