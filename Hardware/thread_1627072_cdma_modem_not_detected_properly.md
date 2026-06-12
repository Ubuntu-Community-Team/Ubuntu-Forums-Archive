---
title: "cdma modem not detected properly"
date: 2010-11-21
forum: Hardware
---

### Post by LKNT on 2010-11-21
Hi everyone,

I have a USB CDMA modem which I want to use on Ubuntu. The model of the modem is cm200 (brand haier), the service provider is Tata Indicom (indian service provider) and the modem is a simless model (meaning, there is no SIM card in the modem, but the device is somehow associated with the phone number) so I cannot use a different modem. This modem is supposed to work on Linux using the wvdial dialer, however when I plug the modem in it does not get detected properly whether usb-modeswitch is installed or not, in fact it doesn't even mount as a CD storage device (which is supposed to host the drivers). This is the output of dmesg:

```
[  117.176523] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  122.396504] usb 2-2: configuration #1 chosen from 1 choice
[  122.399571] scsi5 : SCSI emulation for USB Mass Storage devices
[  122.399811] usb-storage: device found at 3
[  122.399814] usb-storage: waiting for device to settle before scanning
[  127.397711] usb-storage: device scan complete
[  127.400696] scsi 5:0:0:0: CD-ROM            HAIER    MMC Storage      2.31 PQ: 0 ANSI: 2
[  127.520050] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  127.832029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  128.144030] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  128.460032] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  128.776035] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  129.092027] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  129.408034] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  129.604820] sr1: scsi3-mmc drive: 0x/0x caddy
[  129.605010] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  129.605117] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  129.728029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  130.040033] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  130.352034] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  130.664029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  130.976036] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  131.288026] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  131.600025] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  131.912023] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  132.228022] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  132.544161] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  132.860023] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  133.176024] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  133.496033] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  133.812024] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  134.180028] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  134.492034] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  134.804030] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  135.116026] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  135.428064] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  135.760039] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  136.072028] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  136.384031] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  136.696031] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  137.012031] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  137.324031] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  137.636030] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  137.948030] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  138.264021] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  138.576031] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  138.888022] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  139.200035] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  139.512026] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  139.824025] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  140.144028] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  140.456029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  140.768033] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  141.080024] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  141.392029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  141.704029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  142.016026] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  142.328026] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  142.640024] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  142.952025] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  143.264023] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  143.576029] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  143.888035] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  144.200022] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  144.512021] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  144.828019] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  145.144026] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[  145.460027] usb 2-2: reset full speed USB device using uhci_hcd and address 3

```Does anyone know what I should try next?
Thanks

---

### Post by LKNT on 2010-11-22
Anyone?

---

### Post by Fafler on 2010-11-22
Try getting the latest usb-modeswitch from [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) and add your USB vendor and device ID´s to the source.

---

