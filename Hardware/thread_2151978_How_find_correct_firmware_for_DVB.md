---
title: "How find correct firmware for DVB?"
date: 2013-06-06
forum: Hardware
---

### Post by DrAlbert on 2013-06-06
my operating system is kubuntu 13.01.
I have a usb (capture+tv tuner) card with name "pegasus hybrid pro stick plus"
Isearch many website for make this card to work with no luck.
after connecting device this is log in ksyslog:


06/06/13 07:07:29 PM        kernel    [ 6061.292894] usb 1-1.2: new high-speed USB device number 16 using ehci-pci
06/06/13 07:07:29 PM        kernel    [ 6061.386676] usb 1-1.2: New USB device found, idVendor=0438, idProduct=ac14
06/06/13 07:07:29 PM        kernel    [ 6061.386685] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
06/06/13 07:07:29 PM        kernel    [ 6061.386691] usb 1-1.2: Product: Cali TV Card
06/06/13 07:07:29 PM        kernel    [ 6061.386696] usb 1-1.2: Manufacturer: AMD
06/06/13 07:07:29 PM        kernel    [ 6061.386700] usb 1-1.2: SerialNumber: 1234-5678
06/06/13 07:07:29 PM        mtp-probe    checking bus 1, device 16: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2"
06/06/13 07:07:29 PM        mtp-probe    bus: 1, device: 16 was not an MTP device


and this is the result of lsusb:


Bus 001 Device 009: ID 0438:ac14 Advanced Micro Devices, Inc. 


I searched the ID number for firmware with no luck.


I installed many software for DVB but none of those show the device.


what should I do?

---

### Post by DrAlbert on 2013-06-08
no help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

