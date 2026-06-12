---
title: "Asus U3100 Mini plus DVB-T - w_scan doesn't find anything"
date: 2011-07-05
forum: Hardware
---

### Post by jpage89 on 2011-07-05
Hi
I follow this guide
[http://linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T](http://linuxtv.org/wiki/index.php/Asus_U3100_Mini_plus_DVB-T)
The module find correctly the stick, such as dmesg tell me:
```
usb 2-1: new high speed USB device using ehci_hcd and address 6
usb 2-1: New USB device found, idVendor=0b05, idProduct=1779
usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 2-1: Product: AF9035A USB Device
usb 2-1: Manufacturer: Afa Technologies Inc.
usb 2-1: SerialNumber: CT7013035700470
AF903X: af903x_module_init
        DRIVER_RELEASE_VERSION : v9.08.14.1
        FW_RELEASE_VERSION     : v8_8_63_0
        API_RELEASE_VERSION    : 200.20090402.0
dvb-usb: found a 'Asus U3100MINI_PLUS/T/RC Receiver' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
DVB: registering adapter 0 frontend 0 (AF903X USB DVB-T)...
dvb-usb: Asus U3100MINI_PLUS/T/RC Receiver successfully initialized and connected.
        DRIVER_RELEASE_VERSION : v9.08.14.1
        FW_RELEASE_VERSION     : v8_8_63_0
        API_RELEASE_VERSION    : 200.20090402.0
dvb-usb: found a 'Asus U3100MINI_PLUS/T/RC Receiver' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
DVB: registering adapter 1 frontend 0 (AF903X USB DVB-T)...
dvb-usb: Asus U3100MINI_PLUS/T/RC Receiver successfully initialized and connected.
usbcore: registered new interface driver dvb_usb_af903x

```But w_scan doesn't find any channel!

Have you some ideas?

PS: the serial numbers are different from my pen to the pen of the guide
GUIDE: AF0102020700001
MINE:   CT7013035700470

---

