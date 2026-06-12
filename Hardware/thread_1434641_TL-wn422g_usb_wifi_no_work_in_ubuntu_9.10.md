---
title: "TL-wn422g usb wifi no work in ubuntu 9.10"
date: 2010-03-20
forum: Hardware
---

### Post by K0smiC on 2010-03-20
Hi guys I have a problem with the wifi card in the tp-link tl-wn422g Atheros chipset on Ubuntu 9.10 with kernel 2.6.31-20-generic I can not get it working on my laptop I have installed an Intel wifi 5100 seen as a wlan1 Broadcom seen as wlan0
I put what I said lsusb

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a117 Suyin Corp. 
Bus 002 Device 002: ID 0cf3:1006 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 138a:0001 DigitalPersona, Inc Fingeprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

i put what i said lshw -c network
```
*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:63:8c:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

look through your news

---

