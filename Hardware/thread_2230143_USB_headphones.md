---
title: "USB headphones"
date: 2014-06-17
forum: Hardware
---

### Post by rene11 on 2014-06-17
I guess you've all convinced me to give up on this quest.  Thanks for all your help that you refused to give.  This really sucks.

Okay, here goes:  I have this pair of Logitech Headphones (USB I think H390, but I'm not sure;  to my mind that shouldn't really make a differance to the subject at hand).  Well, when I bought them they worked fine, then one day they no longer installed.  Now when I try to get them working again I get this message from dmesg | grep usb:

[ 0.260613] usbcore: registered new interface driver usbfs
 [ 0.260644] usbcore: registered new interface driver hub
 [ 0.260707] usbcore: registered new device driver usb
 [ 2.052281] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
 [ 2.052290] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [ 2.052297] usb usb1: Product: EHCI Host Controller
 [ 2.052304] usb usb1: Manufacturer: Linux 3.13.0-29-generic ehci_hcd
 [ 2.052311] usb usb1: SerialNumber: 0000:00:1d.7
 [ 2.054339] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
 [ 2.054347] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [ 2.054355] usb usb2: Product: UHCI Host Controller
 [ 2.054362] usb usb2: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
 [ 2.054368] usb usb2: SerialNumber: 0000:00:1d.0
 [ 2.055607] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
 [ 2.055615] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [ 2.055622] usb usb3: Product: UHCI Host Controller
 [ 2.055629] usb usb3: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
 [ 2.055636] usb usb3: SerialNumber: 0000:00:1d.1
 [ 2.056871] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
 [ 2.056879] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [ 2.056886] usb usb4: Product: UHCI Host Controller
 [ 2.056893] usb usb4: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
 [ 2.056900] usb usb4: SerialNumber: 0000:00:1d.2
 [ 2.058097] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
 [ 2.058106] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 [ 2.058113] usb usb5: Product: UHCI Host Controller
 [ 2.058120] usb usb5: Manufacturer: Linux 3.13.0-29-generic uhci_hcd
 [ 2.058127] usb usb5: SerialNumber: 0000:00:1d.3

 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
 Aboue I understand:
 Below has baffled me for maybe four month or so:
 VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV

 [ 2.752099] usb 2-1: new full-speed USB device number 2 using uhci_hcd
 [ 2.872078] usb 2-1: device descriptor read/64, error -71
 [ 3.096059] usb 2-1: device descriptor read/64, error -71
 [ 3.312048] usb 2-1: new full-speed USB device number 3 using uhci_hcd
 [ 3.432051] usb 2-1: device descriptor read/64, error -71
 [ 3.656151] usb 2-1: device descriptor read/64, error -71
 [ 3.872083] usb 2-1: new full-speed USB device number 4 using uhci_hcd
 [ 4.280041] usb 2-1: device not accepting address 4, error -71
 [ 4.392188] usb 2-1: new full-speed USB device number 5 using uhci_hcd
 [ 4.800182] usb 2-1: device not accepting address 5, error -71

Hopefully someone out there knows what this means and how I can fix what I think is a BIOS issue.

---

### Post by rene11 on 2014-06-22
Is it possible that I've asked something so inconsequential that everyone considers it a waste of time?  I thought for sure someone would have replied to this with something by now.

---

