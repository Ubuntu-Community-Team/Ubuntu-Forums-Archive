---
title: "Belkin n600 db wi-fi usb driver"
date: 2014-09-22
forum: Hardware
---

### Post by minos.masterchief on 2014-09-22
Hello everyone,

I'm a linux noob having trouble making it identify the belkin n600 db wi-fi usb adapter. As many have suggested I have installed ndiswrapper and tried installing the broadcom_bcm43xx drivers by using "sudo ndiswrapper -i bcmn43xx64.inf" in the relative folder. I however always get this error: "couldn't find SourceDisksFiles section - continuing anyway..." and thus everytime i try "ndiswrapper -l" i get the driver listed but no device recognized beneath it. Pls help, been on it for hours and still no luck.

Output of lsusb:
> Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 050d:110a Belkin Components 
Bus 001 Device 012: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



The realtek wlan adapter is the old wifi usb adater I'm currently using but doesn't work well anymore.

Thanks

---

