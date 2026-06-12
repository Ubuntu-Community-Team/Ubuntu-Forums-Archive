---
title: "Ralink RT5372 with Ubuntu 20.04"
date: 2020-11-25
forum: Hardware
---

### Post by shersk on 2020-11-25
Does anyone know how to get this to work? 

The driver rt2800usb is loaded. 

Here is part of dmesg showing the problem:

```
[45648.946427] usb 2-1: new high-speed USB device number 69 using xhci_hcd
[45649.110357] usb 2-1: New USB device found, idVendor=148f, idProduct=5372, bcdDevice= 1.01
[45649.110360] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[45649.110362] usb 2-1: Product: 802.11 n WLAN
[45649.110363] usb 2-1: Manufacturer: Ralink
[45649.110364] usb 2-1: SerialNumber: 1.0
[45649.238706] usb 2-1: reset high-speed USB device number 69 using xhci_hcd
[45649.404188] ieee80211 phy5176: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[45649.415399] ieee80211 phy5176: rt2x00_set_rf: Info - RF chipset 5372 detected
[45649.415559] ieee80211 phy5176: Selected rate control algorithm 'minstrel_ht'
[45649.440533] rt2800usb 2-1:1.0 wlx00116b4ee661: renamed from wlan0
[45649.480620] ieee80211 phy5176: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[45649.480660] ieee80211 phy5176: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.36
[45649.770641] usb 2-1: USB disconnect, device number 69
[45650.386357] ieee80211 phy5176: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush



```

This repeats itself, over and over.

---

