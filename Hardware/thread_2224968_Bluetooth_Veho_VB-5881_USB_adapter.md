---
title: "Bluetooth Veho VB-5881 USB adapter"
date: 2014-05-19
forum: Hardware
---

### Post by lucast on 2014-05-19
Hi,

I am trying to get my bluetooth adapter to work with my laptop running Lubuntu, but for some reason it is not recognised.  Would anybody be able to help?

OS: Lubuntu 14.04
Bluetooth:  Veho VB-5881 USB Bluetooth adapter
Laptop: Asus eeePC 1005HA (2GB RAM, 240GB SSD)

When I run Preferences > Bluetooth Manager,  and select adapters, the list is empty.

With the Bluetooth USB adapter plugged in, I typed 'lsusb' into a terminal.  The result is as follows:

```
tlucas@tlucas-1005HA:~$ lsusb
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 003: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tlucas@tlucas-1005HA:~$ 
```

I then checked 'hcitool dev' but this does not identify the adapter.

```
tlucas@tlucas-1005HA:~$ hcitool dev
Devices:
tlucas@tlucas-1005HA:~$ 
```

---

### Post by lucast on 2014-05-30
Would anyone know how to get this Bluetooth adapter to work?

Tim

---

