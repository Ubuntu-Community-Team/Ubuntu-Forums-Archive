---
title: "Cannot fet NFC reader/writer to be recognized"
date: 2020-09-22
forum: Hardware
---

### Post by suomalainen on 2020-09-22
Hello All!

I have the following piece of hardware:

Advanced Card Systems, LTD
ACR1281
P/N  ACR1281U-C1

I want to use this NFC reader/writer with a program called TagXplorer but I keep getting the message 'Device not supported'. But device is supported because it works out of the box with same app in Windows 10.

lsusb renders:
paavo@Paavo:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 072f:2224 Advanced Card Systems, Ltd ACR1281 1S Dual Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I also ran sudo -E hw-probe -all -upload
and for this device I got the following

[ATTACH=CONFIG]287009[/ATTACH]

How would I go about figuring what to do next. I'd really like to get this thing working under Ubuntu.

Thank you,

Suomalainen

---

