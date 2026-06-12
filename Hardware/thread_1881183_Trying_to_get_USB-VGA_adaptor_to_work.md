---
title: "Trying to get USB-VGA adaptor to work"
date: 2011-11-15
forum: Hardware
---

### Post by keevill on 2011-11-15
I have a Magic Tech USB-VGA adapter which is not working in 10.04.
lsusb gives 
$ lsusb
Bus 005 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 028: ID 0711:5100 Magic Control Technology Corp. 
Bus 001 Device 027: ID 0461:0010 Primax Electronics, Ltd 
Bus 001 Device 026: ID 046d:c05b Logitech, Inc. 
Bus 001 Device 025: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 014: ID 1410:2120 Novatel Wireless 
Bus 001 Device 013: ID 044e:3012 Alps Electric Co., Ltd 
Bus 001 Device 012: ID 044e:3013 Alps Electric Co., Ltd 
Bus 001 Device 011: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 001 Device 010: ID 044e:3011 Alps Electric Co., Ltd 
Bus 001 Device 006: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 054c:02d5 Sony Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have found a post which seems to provide a way to get it to work.
Can someone explain to me in simple terms what I have to do ?
For example, how do I place the following lines in a kernel ?
The other suggestion at the bottom of the post refers to loader.conf which does not exist in my system.
Help pls...
Thx,

NAME
     umct — Magic Control Technology USB-RS232 converter driver

SYNOPSIS
     To compile this driver into the kernel, place the following lines in your
     kernel configuration file:

           device umct
           device ucom

     Alternatively, to load the driver as a module at boot time, place the
     following line in loader.conf(5):

           umct_load="YES"

---

