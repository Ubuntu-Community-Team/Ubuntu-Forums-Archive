---
title: "USB edge modem not detected in Ubuntu 10.10"
date: 2010-10-26
forum: Hardware
---

### Post by rafi.mahmud on 2010-10-26
It works perfectly with Windows xp, vista & 7 but not in ubuntu. When I plug in the modem to usb port, nothing happens :(

Its a chinese modem and looks like this-
[IMG]http://images-en.busytrade.com/14327390018000180/Usb-Edge-Modem-erg-82-.jpg[/IMG]

I am new in ubuntu. Please help :confused::confused:

---

### Post by vim_lover on 2010-10-26
When the device is not plugged in type the following code in the terminal
```
lsusb
```That will list the devices attached to usb ports.
Then plugin the device.  Again type
```
lsusb
```Note the output.  Compare with the previous output.  Does it show any extra lines?  That will give you the details of the device.  Post the details.

---

### Post by rafi.mahmud on 2010-10-26
When the device is not plugged in the output is-


rafi@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Then, when I plugged in the device it gave me this output-

rafi@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 009: ID 0471:1237 Philips (or NXP) TalkTalk SNU5630NS/05 802.11bg
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


What should I do? please help :confused::confused:

---

