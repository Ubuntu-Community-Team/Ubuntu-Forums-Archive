---
title: "Problem with DW5821e Snapdragon X20 LTE on Ubuntu 20"
date: 2021-04-15
forum: Hardware
---

### Post by jerichoroot on 2021-04-15
Hello!

I have automatic cyclical reinstall LTE modem when I upgrade Ubuntu 18.04 on ubuntu 20 lts.

dmesg:
```

Apr 15 16:13:27 kvv-7400 kernel: [154711.535064] usb 2-4: new SuperSpeed Gen 1 USB device number 89 using xhci_hcd
Apr 15 16:13:27 kvv-7400 kernel: [154711.562088] usb 2-4: New USB device found, idVendor=413c, idProduct=81d7, bcdDevice= 3.18
Apr 15 16:13:27 kvv-7400 kernel: [154711.562094] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 15 16:13:27 kvv-7400 kernel: [154711.562098] usb 2-4: Product: DW5821e Snapdragon X20 LTE
Apr 15 16:13:27 kvv-7400 kernel: [154711.562101] usb 2-4: Manufacturer: Dell Inc.
Apr 15 16:13:27 kvv-7400 kernel: [154711.562104] usb 2-4: SerialNumber: 0123456789ABCDEF
Apr 15 16:13:27 kvv-7400 kernel: [154711.619282] cdc_mbim 2-4:2.0: cdc-wdm0: USB WDM device
Apr 15 16:13:27 kvv-7400 kernel: [154711.619914] cdc_mbim 2-4:2.0 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-4, CDC MBIM, ee:01:c4:5d:12:19
Apr 15 16:13:27 kvv-7400 kernel: [154711.621016] option 2-4:2.2: GSM modem (1-port) converter detected
Apr 15 16:13:27 kvv-7400 kernel: [154711.621299] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB0
Apr 15 16:13:27 kvv-7400 kernel: [154711.621629] option 2-4:2.3: GSM modem (1-port) converter detected
Apr 15 16:13:27 kvv-7400 kernel: [154711.621963] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB1
Apr 15 16:13:27 kvv-7400 kernel: [154711.622266] option 2-4:2.4: GSM modem (1-port) converter detected
Apr 15 16:13:27 kvv-7400 kernel: [154711.622630] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB2
Apr 15 16:13:27 kvv-7400 kernel: [154711.623372] option 2-4:2.5: GSM modem (1-port) converter detected
Apr 15 16:13:27 kvv-7400 kernel: [154711.623858] usb 2-4: GSM modem (1-port) converter now attached to ttyUSB3
Apr 15 16:13:43 kvv-7400 kernel: [154727.558868] usb 2-4: USB disconnect, device number 89
Apr 15 16:13:43 kvv-7400 kernel: [154727.558980] cdc_mbim 2-4:2.0 wwan0: unregister 'cdc_mbim' usb-0000:00:14.0-4, CDC MBIM
Apr 15 16:13:43 kvv-7400 kernel: [154727.599769] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Apr 15 16:13:43 kvv-7400 kernel: [154727.599844] option 2-4:2.2: device disconnected
Apr 15 16:13:43 kvv-7400 kernel: [154727.600452] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Apr 15 16:13:43 kvv-7400 kernel: [154727.600524] option 2-4:2.3: device disconnected
Apr 15 16:13:43 kvv-7400 kernel: [154727.601367] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Apr 15 16:13:43 kvv-7400 kernel: [154727.601424] option 2-4:2.4: device disconnected
Apr 15 16:13:43 kvv-7400 kernel: [154727.602009] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Apr 15 16:13:43 kvv-7400 kernel: [154727.602068] option 2-4:2.5: device disconnected
Apr 15 16:13:45 kvv-7400 kernel: [154729.514967] usb 2-4: new SuperSpeed Gen 1 USB device number 90 using xhci_hcd
Apr 15 16:13:45 kvv-7400 kernel: [154729.540830] usb 2-4: New USB device found, idVendor=413c, idProduct=81d7, bcdDevice= 0.00
Apr 15 16:13:45 kvv-7400 kernel: [154729.540835] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 15 16:13:45 kvv-7400 kernel: [154729.540839] usb 2-4: Product: QUSB_Fast_Enum_SN:452C9695
Apr 15 16:13:45 kvv-7400 kernel: [154729.540842] usb 2-4: Manufacturer: Qualcomm CDMA Technologies MSM
Apr 15 16:13:50 kvv-7400 kernel: [154734.678915] usb 2-4: Set SEL for device-initiated U1 failed.
Apr 15 16:13:50 kvv-7400 kernel: [154734.678929] usb 2-4: Set SEL for device-initiated U2 failed.
Apr 15 16:13:50 kvv-7400 kernel: [154734.679236] usb 2-4: Set SEL for device-initiated U1 failed.
Apr 15 16:13:50 kvv-7400 kernel: [154734.679241] usb 2-4: Set SEL for device-initiated U2 failed.
Apr 15 16:13:50 kvv-7400 kernel: [154734.680346] usb 2-4: USB disconnect, device number 90

```

On ubuntu 18.04 this modem work good.

Thank U!

---

