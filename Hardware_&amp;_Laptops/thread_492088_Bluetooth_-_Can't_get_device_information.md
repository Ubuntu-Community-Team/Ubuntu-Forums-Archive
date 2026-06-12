---
title: "Bluetooth - Can't get device information"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by mhafren on 2007-07-04
Hello,

**Background**
Ubuntu Feisty 7.04 / LG T1 Express
dmesg | grep Bluetooth:
[   24.112000] Bluetooth: Core ver 2.11
[   24.112000] Bluetooth: HCI device and connection manager initialized
[   24.112000] Bluetooth: HCI socket layer initialized
[   24.208000] Bluetooth: HCI USB driver ver 2.9
[   25.432000] Bluetooth: L2CAP ver 2.8
[   25.432000] Bluetooth: L2CAP socket layer initialized
[   25.476000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   69.080000] Bluetooth: RFCOMM socket layer initialized
[   69.080000] Bluetooth: RFCOMM TTY layer initialized
[   69.080000] Bluetooth: RFCOMM ver 1.8

lsusb:
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

I have installed bluez-utils, bluez-pin and ppp.

**Problem**
When i "sudo /etc/init.d/bluetooth" I get the response
"Restarting  Bluetooth services
Can't get device information: Success    [ok]"
I am able to scan for devices but I am not able to pair them. For example trying to connect to my Nokia E61(using sudo hidd --connect mac-adress )gives the same respons "Can't get device information: Sucess" and it doesn't get connected. "hcitool cc mac-adress" doesn't give any response but doesn't get connected either". I'm guessing that it's alread at the first restart of bluetooth that something goes wrong. 

Does anybody have any idea what could be wrong?? Worth noting is that I already had bluetooth working on Ubuntu Dapper 6.06, did never try on edgy but feisty gives this problem..

Could somebody please help?

Regards,
Måns

---

