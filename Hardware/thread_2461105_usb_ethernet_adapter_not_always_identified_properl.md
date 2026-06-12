---
title: "usb ethernet adapter not always identified properly on bootup"
date: 2021-04-24
forum: Hardware
---

### Post by robdavies on 2021-04-24
Hi

I'm using xubuntu 20.10 and running on a Dell D830 laptop, have had this problem for a couple of versions, just got around to sorting it out now.

I have a USB TP-LINK UE300 ethernet adapter providing network connection. Upto bootup, sometimes it works, sometimes it doesn't have a network connection until I unplug it and then plug it back in.

The output from dmesg (I ran sudo dmesg | grep 2-1) when it doesn't work is :

[    1.641278] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.798118] usb 2-1: New USB device found, idVendor=2357, idProduct=0600, bcdDevice=30.00
[    1.798121] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[    1.798123] usb 2-1: Product: USB 10/100/1000 LAN
[    1.798124] usb 2-1: Manufacturer: TP-LINK
[    1.798125] usb 2-1: SerialNumber: 000001000000
[    1.822561] usb-storage 2-1:1.0: USB Mass Storage device detected
[    1.822804] scsi host2: usb-storage 2-1:1.0

The output from dmesg after I unplugged it and plugged it back in :

[    1.641278] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.798118] usb 2-1: New USB device found, idVendor=2357, idProduct=0600, bcdDevice=30.00
[    1.798121] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[    1.798123] usb 2-1: Product: USB 10/100/1000 LAN
[    1.798124] usb 2-1: Manufacturer: TP-LINK
[    1.798125] usb 2-1: SerialNumber: 000001000000
[    1.822561] usb-storage 2-1:1.0: USB Mass Storage device detected
[    1.822804] scsi host2: usb-storage 2-1:1.0
[  206.729281] usb 2-1: USB disconnect, device number 2
[  207.673512] usb 2-1: new high-speed USB device number 4 using ehci-pci
[  207.834952] usb 2-1: New USB device found, idVendor=2357, idProduct=0601, bcdDevice=30.00
[  207.834960] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[  207.834965] usb 2-1: Product: USB 10/100/1000 LAN
[  207.834970] usb 2-1: Manufacturer: TP-LINK
[  207.834974] usb 2-1: SerialNumber: 000001000000
[  208.013540] usb 2-1: reset high-speed USB device number 4 using ehci-pci
[  208.243794] r8152 2-1:1.0 eth0: v2.14.0 (2020/09/24)
[  208.243800] r8152 2-1:1.0 eth0: This product is covered by one or more of the following patents:
[  208.309941] r8152 2-1:1.0 enx503eaa77b591: renamed from eth0
[  211.155306] r8152 2-1:1.0 enx503eaa77b591: carrier on

Does anyone know if there is anything I can do?

Thanks,
Rob

---

