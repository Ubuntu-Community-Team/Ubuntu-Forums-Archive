---
title: "USB 3.0 disk get's disconnected just after connected"
date: 2016-07-30
forum: Hardware
---

### Post by henri-periat on 2016-07-30
Hi everybody

Whenever I connect one of my identical USB disks to a USB 3 port of my computer, it won't get connected. At the end of /var/log/kern.log I have found these statements:

Jul 30 22:05:24 gutemine kernel: [  122.524688] usb 4-4: new SuperSpeed USB device number 4 using xhci_hcd
Jul 30 22:05:24 gutemine kernel: [  122.541885] usb 4-4: New USB device found, idVendor=18a5, idProduct=022a
Jul 30 22:05:24 gutemine kernel: [  122.541890] usb 4-4: New USB device strings: Mfr=10, Product=11, SerialNumber=3
Jul 30 22:05:24 gutemine kernel: [  122.541893] usb 4-4: Product: Desktop USB3.0 Drive
Jul 30 22:05:24 gutemine kernel: [  122.541895] usb 4-4: Manufacturer: Verbatim
Jul 30 22:05:24 gutemine kernel: [  122.541897] usb 4-4: SerialNumber: 18A5022A00009821
Jul 30 22:05:24 gutemine kernel: [  122.545947] usb 4-4: Enable of device-initiated U2 failed.
Jul 30 22:05:24 gutemine kernel: [  122.546021] usb-storage 4-4:1.0: USB Mass Storage device detected
Jul 30 22:05:24 gutemine kernel: [  122.546405] scsi host9: usb-storage 4-4:1.0
Jul 30 22:05:24 gutemine kernel: [  122.712718] usb 4-4: USB disconnect, device number 4
Jul 30 22:05:24 gutemine kernel: [  122.952900] usb 4-4: new SuperSpeed USB device number 5 using xhci_hcd
Jul 30 22:05:24 gutemine kernel: [  122.969891] usb 4-4: New USB device found, idVendor=18a5, idProduct=022a
Jul 30 22:05:24 gutemine kernel: [  122.969909] usb 4-4: New USB device strings: Mfr=10, Product=11, SerialNumber=3
Jul 30 22:05:24 gutemine kernel: [  122.969912] usb 4-4: Product: Desktop USB3.0 Drive
Jul 30 22:05:24 gutemine kernel: [  122.969914] usb 4-4: Manufacturer: Verbatim
Jul 30 22:05:24 gutemine kernel: [  122.969916] usb 4-4: SerialNumber: 18A5022A00009821
Jul 30 22:05:24 gutemine kernel: [  122.970525] usb-storage 4-4:1.0: USB Mass Storage device detected
Jul 30 22:05:24 gutemine kernel: [  122.970754] scsi host10: usb-storage 4-4:1.0
Jul 30 22:05:24 gutemine kernel: [  123.079503] usb 4-4: USB disconnect, device number 5

These USB disk work perfectly on a USB 2 port. I tried out different USB 3 ports and different cables without success.
Has anybody an idea what I can do to solve this problem?

Thanks a lot
Henri

---

