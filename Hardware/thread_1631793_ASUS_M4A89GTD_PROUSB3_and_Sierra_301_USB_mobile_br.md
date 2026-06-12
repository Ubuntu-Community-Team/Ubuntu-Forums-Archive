---
title: "ASUS M4A89GTD PRO/USB3 and Sierra 301 USB mobile broadband"
date: 2010-11-27
forum: Hardware
---

### Post by rjg_munga on 2010-11-27
Need help getting my Sierra 301 USB mobile broadband stick to work on my new motherboard ASUS M4A89GTD PRO/USB3.

The Sierra 301 stick works fine on my Eee PC running Ubuntu 10.04 & 10.10 and it also works on the ASUS M4A89GTD PRO/USB3 motherboard when running winxp
I have no idea where to start looking, here is the output from dmesg when the stick is inserted and trys to connect.
```

$ dmesg

[ 4768.260132] usb 2-3: new high speed USB device using ehci_hcd and address 4
[ 4768.411959] usb 2-3: config 1 has an invalid interface number: 9 but max is 0
[ 4768.411968] usb 2-3: config 1 has no interface number 0
[ 4768.479752] Initializing USB Mass Storage driver...
[ 4768.481368] usb-storage: probe of 2-3:1.9 failed with error -5
[ 4768.481424] usbcore: registered new interface driver usb-storage
[ 4768.481429] USB Mass Storage support registered.
[ 4768.978929] usb 2-3: USB disconnect, address 4
[ 4769.370925] usb 2-3: new high speed USB device using ehci_hcd and address 5
[ 4769.527729] usb 2-3: config 1 has an invalid interface number: 7 but max is 4
[ 4769.527738] usb 2-3: config 1 has no interface number 2
[ 4769.581056] usb 2-3: Incompatible driver and firmware versions
[ 4769.581085] usbcore: registered new interface driver sierra_net
[ 4769.592342] usbcore: registered new interface driver usbserial
[ 4769.592377] USB Serial support registered for generic
[ 4769.620265] usbcore: registered new interface driver usbserial_generic
[ 4769.620271] usbserial: USB Serial Driver core
[ 4769.626275] USB Serial support registered for Sierra USB modem
[ 4769.626344] sierra 2-3:1.0: Sierra USB modem converter detected
[ 4769.627221] usb 2-3: Sierra USB modem converter now attached to ttyUSB0
[ 4769.627258] sierra 2-3:1.1: Sierra USB modem converter detected
[ 4769.627746] usb 2-3: Sierra USB modem converter now attached to ttyUSB1
[ 4769.627780] sierra 2-3:1.3: Sierra USB modem converter detected
[ 4769.628146] usb 2-3: Sierra USB modem converter now attached to ttyUSB2
[ 4769.628173] sierra 2-3:1.4: Sierra USB modem converter detected
[ 4769.628648] usb 2-3: Sierra USB modem converter now attached to ttyUSB3
[ 4769.628703] usbcore: registered new interface driver sierra
[ 4769.628707] sierra: v.1.7.16:USB Driver for Sierra Wireless USB modems
[ 4830.916619] ehci_hcd 0000:00:13.2: force halt; handshake ffffc9000067a424 00004000 00000000 -> -110
[ 4830.916632] sierra ttyUSB2: sierra_submit_rx_urbs: submit intr urb failed: -110
[ 4831.016828] sierra ttyUSB2: sierra_write - usb_submit_urb(write bulk) failed with status = -108

```

any ideas?
thanks
munga

---

### Post by rjg_munga on 2010-11-29
Bumping!!!
I could really do with some help guys.

---

