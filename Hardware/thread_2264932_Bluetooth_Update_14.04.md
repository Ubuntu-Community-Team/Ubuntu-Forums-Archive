---
title: "Bluetooth Update 14.04"
date: 2015-02-11
forum: Hardware
---

### Post by JoeFriday49 on 2015-02-11
Did the latest update that included the bluetooth files make anyone's 14.04 work?...  Didn't change anything here...

---

### Post by jeremy31 on 2015-02-11
What devices do you have ```
lspci -nnk | grep -iA2 net
``````
lsusb
```
I know there were some kernel changes in 3.13.0-45 for loading firmware for some broadcom devices

---

### Post by JoeFriday49 on 2015-02-12
Here you go...  

joe@jf-pavilion:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1629]
    Kernel driver in use: rtl8192ce
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3562]
    Kernel driver in use: r8169
joe@jf-pavilion:~$ 
joe@jf-pavilion:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:a001 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0603:0002 Novatek Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
joe@jf-pavilion:~$

---

### Post by Pilot6 on 2015-02-12
This bluetooth probably will never work.
Broadcom  [COLOR=#000000]0a5c:2101

It is 'supported' by the kernel. But seems not to work. All broadcom chips is very hard to get to work under linux.[/COLOR]

---

### Post by jeremy31 on 2015-02-12
> **Pilot6 said:**
> This bluetooth probably will never work.
Broadcom  [COLOR=#000000]0a5c:2101

It is 'supported' by the kernel. But seems not to work. All broadcom chips is very hard to get to work under linux.[/COLOR]

It seems that the 3.13.0-45 kernel lumped a bunch of devices into a group with this ```
/*Broadcom devices with vendor specific id */	{ USB_VENDOR_AND_INTERFACE_INFO(0x0a5c, 0xff, 0x01, 0x01), .driver_info = BTUSB_BCM_PATCHRAM },

```
Which means you have to look throught windows drivers to find a hex file that can be converted to hcd

An older version had the device as ```
/* Broadcom BCM2045 */	{ USB_DEVICE(0x0a5c, 0x2039), .driver_info = BTUSB_WRONG_SCO_MTU },
	{ USB_DEVICE(0x0a5c, 0x2101), .driver_info = BTUSB_WRONG_SCO_MTU },
```

---

