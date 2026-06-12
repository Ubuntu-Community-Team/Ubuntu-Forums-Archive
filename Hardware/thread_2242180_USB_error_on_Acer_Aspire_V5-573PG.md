---
title: "USB error on Acer Aspire V5-573PG"
date: 2014-08-31
forum: Hardware
---

### Post by nrvs on 2014-08-31
Hello,
I have an usb error on my laptop Acer Aspire V5-573PG.(with ACPI warnings)
I am trying kubuntu liveUSB and got this on dmesg log:
```
usb 2-6: new full-speed USB device number 8 using xhci_hcd
[   13.550057] usb 2-6: New USB device found, idVendor=04f3, idProduct=0125
[   13.550062] usb 2-6: New USB device strings: Mfr=4, Product=14, SerialNumber=0
[   13.550065] usb 2-6: Product: Touchscreen
[   13.550068] usb 2-6: Manufacturer: ELAN
[   13.550160] usb 2-6: ep 0x2 - rounding interval to 64 microframes, ep desc says 80 microframes
[   15.598045] usb 2-6: USB disconnect, device number 8
[   15.870511] usb 2-6: new full-speed USB device number 9 using xhci_hcd
[   16.871318] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   16.871474] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   17.936152] usb 2-6: unable to read config index 0 descriptor/start: -71
[   17.936154] usb 2-6: can't read configurations, error -71
[   18.048219] usb 2-6: new full-speed USB device number 10 using xhci_hcd
[   20.114517] usb 2-6: unable to read config index 0 descriptor/start: -71
[   20.114521] usb 2-6: can't read configurations, error -71
[   20.226082] usb 2-6: new full-speed USB device number 11 using xhci_hcd
[   27.295763] usb 2-6: unable to read config index 0 descriptor/start: -110
[   27.295767] usb 2-6: can't read configurations, error -110
[   27.592005] usb 2-6: new full-speed USB device number 13 using xhci_hcd
[   27.609658] usb 2-6: New USB device found, idVendor=04f3, idProduct=0125
[   27.609662] usb 2-6: New USB device strings: Mfr=4, Product=14, SerialNumber=0
```
This is a sample. Here is the complete  dmesg log:
[http://pastebin.com/3C7RyvEV](http://pastebin.com/3C7RyvEV)
At the end of the log shows the connection of another USB stick.

---

