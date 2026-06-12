---
title: "Install Bluetooth adapter / Make a Connection"
date: 2009-10-29
forum: Hardware
---

### Post by frs89 on 2009-10-29
Hello everyone:

My laptop doesn't have bluetooth, so I want to use a bluetooth adapter to connect with my sixaxis gamepad. How do I setup the bluetooth device? And how can I make a connection, for example to my cellphone?

Regards

---

### Post by tlytle83 on 2011-07-22
I have the same issue. I have an HP slimline on which the Windows XP build finally took a massive dump so I took the leap to Linux. Now having a 42 inch tv as a monitor is a pain because I can't get my bluetooth adapter to work. I'm lost in the terminal but I get these responses from commands I've seen others suggest running:

tim@Ubuntu-Box:~$ lsusb
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 15a9:0004 Gemtek WUBR177G
Bus 002 Device 003: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 002 Device 002: ID 0461:4d42 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tim@Ubuntu-Box:~$ hcitool dev
Devices:
tim@Ubuntu-Box:~$ hcitool dev
Devices:
tim@Ubuntu-Box:~$ hcitool scan
Device is not available: No such device

---

