---
title: "USB Modem treated as mass storage device"
date: 2011-07-28
forum: Hardware
---

### Post by raunhar on 2011-07-28
I have a 3G mobile phone, with Modem.
When I connect the phone to the USB port, the Computer treats it a mass storage device and shows the content of Memeory card.

I need to use the mobile to connect to internet.

Under Network connections (Mobile Broadband), it does not show the device.
lsusb result is:

 lsusb
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 010: ID d324:9003  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


When I unplug the device, result of lsusb is

$ lsusb
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

dmesg has the following result:
[ 3813.594099] usb 2-1: USB disconnect, address 10
[ 3832.000111] usb 2-1: new high speed USB device using ehci_hcd and address 11
[ 3832.134737] usb 2-1: config 1 has an invalid interface number: 4 but max is 3
[ 3832.134747] usb 2-1: config 1 has no interface number 0
[ 3832.140821] scsi6 : usb-storage 2-1:1.3
[ 3833.142684] scsi 6:0:0:0: CD-ROM            SPICE 3G Phone CDROM      2.31 PQ: 0 ANSI: 2
[ 3833.143543] scsi 6:0:0:1: Direct-Access     SPICE 3G Phone MicroSD/TF 2.31 PQ

On connecting the device, the following process are done:
Mass storage device
Charging of Mobile Phone.

What should I do it make it work.

---

