---
title: "Bluetooth fail"
date: 2011-04-05
forum: Hardware
---

### Post by caryub on 2011-04-05
I update to ubuntu 11.04 natty 64 Bits my toshiba laptop. All right except bluetooth.
Bluetooth settings say me "bluetooth is disconnected. The turn on button is disabled.

Any idea?

**$hciconfig**
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:03:7A:FE:42:64  ACL MTU: 384:8  SCO MTU: 64:8
	UP RUNNING 
	RX bytes:356 acl:0 sco:0 events:13 errors:0
	TX bytes:53 acl:0 sco:0 commands:13 errors:0

**$ lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**$ dmesg | grep Bluetooth**
[   25.372066] Detected Toshiba ACPI Bluetooth device - installing RFKill handler
[   25.374600] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
[   26.553488] Bluetooth: Core ver 2.15
[   26.553743] Bluetooth: HCI device and connection manager initialized
[   26.553746] Bluetooth: HCI socket layer initialized
[   26.583156] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   30.591891] Bluetooth: L2CAP ver 2.15
[   30.591895] Bluetooth: L2CAP socket layer initialized
[   30.945206] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.945210] Bluetooth: BNEP filters: protocol multicast
[   31.223796] Bluetooth: SCO (Voice Link) ver 0.6
[   31.223800] Bluetooth: SCO socket layer initialized
[40081.082048] toshiba_bluetooth: Re-enabling Toshiba Bluetooth

---

### Post by caryub on 2011-04-05
WTF!!!!

After reading diferent blogs and making diferent thinks

sudo modprobe toshiba_acpi
sudo modprobe toshiba_bluetooth
toshset -bluetooth on
sudo apt-get install toshset (it was installed at latest version)
...

I do:

sudo apt-get update
sudo apt-get upgrade

and started to downloand a new version of bluez, and bluetooth icon turned on.... incredible

---

### Post by caryub on 2011-04-05
It look repaired and show me bluetooth detected devices, but when I sent a file to my mobile it crashed.

Another time bluetooth icon was turned off. when I go to preferences/settings (I don't know the english text) 

I see "Bluetooth is disabled" and a button "Turn on Bluetooth"
I press it but no change. Only the button turn disabled.

If I close the window and open again the button is available another time...

---

### Post by urizen555 on 2011-04-19
same problem with me, i have a custom laptop {turbo-x} and i have the exact same problem. no recognition for the blue tooth devices i have and worked fine with 10.10 .

---

### Post by isantop on 2011-04-21
This is also affecting most Bluetooth enabled System76 Laptops. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/762964)

---

### Post by gsaggior on 2011-05-05
Same issue with a Satellite P100:

xyz@Toshiba-P100:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
...

xyz@Toshiba-P100:~$ sudo hciconfig
hci0:   Type: BR/EDR  Bus: USB
        BD Address: 00:03:7A:FA:D8:58  ACL MTU: 384:8  SCO MTU: 64:8
        UP RUNNING
        RX bytes:380 acl:0 sco:0 events:18 errors:0
        TX bytes:79 acl:0 sco:0 commands:16 errors:0

:cry:

---

### Post by avlnewby on 2011-05-06
same with asus eeepc 1005ha. interesting

---

### Post by fishie on 2011-05-16
same with eeepc 1000he, no adapter found. usb adapter i have works fine though

---

