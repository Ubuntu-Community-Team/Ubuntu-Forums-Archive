---
title: "USB Bluetooth Issues"
date: 2019-08-24
forum: Hardware
---

### Post by petermc2 on 2019-08-24
Hi, I need some help with a bluetooth problem. I am unable to use a USB bluetooth device. The bluetooth UI just says there is no adapter.

I am running ubuntu 19.04 and everything is up to date.

I have this device as per lsusb,

Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

dmesg | grep Bluetooth

[    6.137963] Bluetooth: Core ver 2.22
[    6.137977] Bluetooth: HCI device and connection manager initialized
[    6.137980] Bluetooth: HCI socket layer initialized
[    6.137982] Bluetooth: L2CAP socket layer initialized
[    6.137984] Bluetooth: SCO socket layer initialized
[    8.208995] Bluetooth: hci0: command 0x2003 tx timeout
[   10.224994] Bluetooth: hci0: command 0x2007 tx timeout
[   15.063638] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.063639] Bluetooth: BNEP filters: protocol multicast
[   15.063642] Bluetooth: BNEP socket layer initialized
[ 1069.727317] Bluetooth: hci0: command 0x2003 tx timeout
[ 1071.743434] Bluetooth: hci0: command 0x2007 tx timeout
[ 1346.401282] Bluetooth: hci0: command 0x2003 tx timeout
[ 1348.417451] Bluetooth: hci0: command 0x2007 tx timeout
[ 1487.968981] Bluetooth: hci0: command 0x2003 tx timeout
[ 1489.984757] Bluetooth: hci0: command 0x2007 tx timeout
[ 2258.267934] Bluetooth: hci0: command 0x2003 tx timeout
[ 2260.287907] Bluetooth: hci0: command 0x2007 tx timeout

hciconfig -a hci0

hci0:   Type: Primary  Bus: USB
        BD Address: 33:03:30:09:E8:9D  ACL MTU: 360:4  SCO MTU: 0:0
        DOWN 
        RX bytes:3318 acl:0 sco:0 events:168 errors:0
        TX bytes:2208 acl:0 sco:0 commands:180 errors:0
        Features: 0xff 0xff 0xcd 0xfa 0xdb 0xbf 0x7b 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 

sudo hciconfig hci0 up

gives me this,

Can't init device hci0: Operation not supported (95)

I'm not sure what else to do here?

Interestingly enough I purchased this device because it said it would work with a raspberry pi, so I thought that would mean it would work with other linux distros too. And it is mentioned here,

[https://elinux.org/RPi_USB_Bluetooth_adapters](https://elinux.org/RPi_USB_Bluetooth_adapters)

---

