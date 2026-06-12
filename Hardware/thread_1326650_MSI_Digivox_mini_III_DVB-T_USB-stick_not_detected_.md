---
title: "MSI Digivox mini III DVB-T USB-stick not detected by Ubuntu 9.10"
date: 2009-11-14
forum: Hardware
---

### Post by beneedict on 2009-11-14
Hi there!
I had my DVB-T stick (MSI Digivox mini III) running flawlessly until the upgrade to karmic. Now it is not even detected any more. Sadly I upgraded to Win7 x64 at the same time, so the windows driver does not work either currently. Therefore please also take a possibly broken hardware in regard.
Anyway, this is my dmesg output after plugging in the USB DVB-T stick:
```
[18615.380073] usb 2-3: new full speed USB device using ohci_hcd and address 8
[18615.560094] usb 2-3: device descriptor read/64, error -62
[18615.850121] usb 2-3: device descriptor read/64, error -62
[18616.140082] usb 2-3: new full speed USB device using ohci_hcd and address 9
[18616.320114] usb 2-3: device descriptor read/64, error -62
[18616.610124] usb 2-3: device descriptor read/64, error -62
[18616.900097] usb 2-3: new full speed USB device using ohci_hcd and address 10
[18617.330065] usb 2-3: device not accepting address 10, error -62
[18617.510299] usb 2-3: new full speed USB device using ohci_hcd and address 11
[18617.930091] usb 2-3: device not accepting address 11, error -62
[18617.930173] hub 2-0:1.0: unable to enumerate USB device on port 3
```
and my lsusb output:
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Any ideas on the cause of this trouble?

---

