---
title: "Cant' mount USB HDD anymore"
date: 2014-08-09
forum: Hardware
---

### Post by henri-periat on 2014-08-09
Since the upgrad from 12.04 LTS to 14.04 LTS, I can't mount my external, crypted backup harddisk anymore. In the log I can find:

tail -f /var/log/syslog 
Aug  9 15:10:42 gutemine kernel: [ 2799.080763] usb 4-4: New USB device found, idVendor=18a5, idProduct=022a
Aug  9 15:10:42 gutemine kernel: [ 2799.080768] usb 4-4: New USB device strings: Mfr=10, Product=11, SerialNumber=3
Aug  9 15:10:42 gutemine kernel: [ 2799.080771] usb 4-4: Product: Desktop USB3.0 Drive
Aug  9 15:10:42 gutemine kernel: [ 2799.080773] usb 4-4: Manufacturer: Verbatim
Aug  9 15:10:42 gutemine kernel: [ 2799.080775] usb 4-4: SerialNumber: 18A5022A0000A419
Aug  9 15:10:42 gutemine kernel: [ 2799.081592] usb-storage 4-4:1.0: USB Mass Storage device detected
Aug  9 15:10:42 gutemine kernel: [ 2799.081775] scsi8 : usb-storage 4-4:1.0
Aug  9 15:10:42 gutemine mtp-probe: checking bus 4, device 3: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-4"
Aug  9 15:10:42 gutemine mtp-probe: bus: 4, device: 3 was not an MTP device
Aug  9 15:10:43 gutemine kernel: [ 2799.207548] usb 4-4: USB disconnect, device number 3

I have changed the USB port and the cable with no sucess.
Thanks a lot for any help.

---

