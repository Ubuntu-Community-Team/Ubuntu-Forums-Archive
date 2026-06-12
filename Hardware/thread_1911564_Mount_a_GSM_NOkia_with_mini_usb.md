---
title: "Mount a GSM NOkia with mini usb?"
date: 2012-01-19
forum: Hardware
---

### Post by honeybear on 2012-01-19
Hello, nothing appears in dmesg such as /dev/X :( 

usb 2-1.2: New USB device found, idVendor=0421, idProduct=0261
```

[54351.888673] usb 2-1.2: new full speed USB device using ehci_hcd and address 5
[54351.985137] usb 2-1.2: New USB device found, idVendor=0421, idProduct=0261
[54351.985142] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[54351.985147] usb 2-1.2: Product: Nokia 7230
[54351.985150] usb 2-1.2: Manufacturer: Nokia
[54351.985270] usb 2-1.2: configuration #1 chosen from 3 choices
[54352.560325] usbcore: registered new interface driver cdc_ether
[54352.685656] NET: Registered protocol family 35
[54352.687777] usb 2-1.2: bad CDC descriptors
[54352.687793] usbcore: registered new interface driver rndis_host
[54352.881377] usbcore: registered new interface driver cdc_phonet
[54352.902353] cdc_acm 2-1.2:1.4: ttyACM0: USB ACM device
[54352.902991] usbcore: registered new interface driver cdc_acm
[54352.902993] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[54352.972620] cfg80211: Using static regulatory domain info
[54352.972622] cfg80211: Regulatory domain: US
[54352.972624]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[54352.972626]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[54352.972627]  (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[54352.972629]  (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[54352.972630]  (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[54352.972632]  (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[54352.972634]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[54352.972637] cfg80211: Calling CRDA for country: US
[54352.996692] usb 2-1.2: bad CDC descriptors
[54352.997259] usbcore: registered new interface driver rndis_wlan
```

---

