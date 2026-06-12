---
title: "Getting Slides2PC Scanner Working?"
date: 2021-04-28
forum: Hardware
---

### Post by rebeltaz on 2021-04-28
I'm running Ubuntu 18.04 LTS. I have an old Ion Slides2PC slide and film scanner that I would like to use. Technically, it was designed to be used with Photo Impressions software under windows. I tried sane/xsane and it reported that there was no device found so I took a quick look at dmesg. It looks like the "scanner" is being seen as a USB camera:

```
[24710.144125] usb 2-2: new high-speed USB device number 9 using xhci_hcd
[24710.293831] usb 2-2: New USB device found, idVendor=05a9, idProduct=1550
[24710.293834] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[24710.293836] usb 2-2: Product: USB Camera
[24710.293838] usb 2-2: Manufacturer: FW-07.07.25
[24710.331624] media: Linux media interface: v0.10
[24710.338543] Linux video capture interface: v2.00
[24710.342160] gspca_main: v2.14.0 registered
[24710.343485] gspca_main: ov534_9-2.14.0 probing 05a9:1550
[24713.496218] usbcore: registered new interface driver ov534_9
```


Cheese Webcam Booth doesn't see a device, either. Is there any way that I can utilize this thing under linux?

EDIT: Nevermind... After posting this, I did a search for ov534_9 and that led me to guvcview that seems to work with this scanner. Thanks for letting me think out loud. Leaving this here in case anyone else needs it.

---

