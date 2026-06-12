---
title: "Toshiba and Bluetooth setup.."
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by nconceicao on 2007-08-12
Hi

I installed linux on my laptop. I've got everything working fine now, well except bluetooth...

I installed bluez-utils and followed the instructions on: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

but, no usb devices are detected. here's the output of lsusb and hcitool dev

Code:

~$ lsusb
Bus 005 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000

Code:

~$ hcitool dev
Devices:

Any help would be wonderfull.. bluetooth is bult on to my laptop..

---

### Post by linuxwizard on 2007-08-12
Is your Bluetooth devices supported under Linux

Here is a list if it has a HCI version number it should work under linux
[http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)

---

