---
title: "How do I tell what hub my usb drives are attached to?"
date: 2016-08-20
forum: Hardware
---

### Post by Evil Wayz on 2016-08-20
I recently installed a front facing usb 2.0 hub.  I was forced to split the 9 pin jack because there was another device already using it.  Well I'm noticing that while it does work for power and data, it's really slow.  The fastest I can transfer data is 900kb/s or so, and right now it's crawling at about 300.  Also, now the original two usb ports on the front of hte bix don't work, and if you plug anything into them, it cuts off all usb hubs except for the ones on the board.  I haven't ever run into anything like that before.  Anyways I was wondering if that is as much speed as I can expect from usb 2.0 or not, and if myabe my usb drives are just plugged into the wrong ports. 


Here is the output of lsusb:

```
wolf@shaitan:~$ lsusb
Bus 002 Device 002: ID 1871:01f0 Aveo Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 018: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 006 Device 019: ID 1058:1110 Western Digital Technologies, Inc. My Book Essential (WDBAAF), My Book for Mac (WDBAAG)
Bus 006 Device 017: ID 0781:5575 SanDisk Corp. 
Bus 006 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 006 Device 008: ID 0489:e076 Foxconn / Hon Hai 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0c45:8603 Microdia 
Bus 003 Device 002: ID 0000:3821  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Yellow Pasque on 2016-08-21
> Bus 006 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

It's being initialized as USB 1.1 (possibly because of other devices connected to it).

>  I was forced to split the 9 pin jack because there was another device already using it. .. Also, now the original two usb ports on the front of hte bix don't work, and if you plug anything into them, it cuts off all usb hubs except for the ones on the board.

I would worry that too much power is being demanded.

---

### Post by Evil Wayz on 2016-08-21
Well, I have a hub that plugs into a pci slot that runs off the bus, and it appears to be running at the proper speed.  A little disappointed that my spiffy new front storage bay hub is only going to be useful for charging, but thems the breaks...

---

### Post by Evil Wayz on 2016-08-21
The hub consists of power outlet usb slot, two usb 3.0 slots which are not in use, and four usb 2.0 slots.  THose are connected to the split.  I wonder if there is some sort of molex to 9 pin adapter I can use.  That would feed enough power it seems to me.

---

### Post by Evil Wayz on 2016-08-27
OK, now my usb ports are just randomly assigning themselves.  This is my lsusb output after a reboot. nothing was unplugged, internally or externally.:

```
wolf@shaitan:~$ lsusb
Bus 006 Device 004: ID 1871:01f0 Aveo Technology Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1058:1110 Western Digital Technologies, Inc. My Book Essential (WDBAAF), My Book for Mac (WDBAAG)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 0781:5575 SanDisk Corp. 
Bus 005 Device 007: ID 05e3:0751 Genesys Logic, Inc. 
Bus 005 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 005 Device 009: ID 0489:e076 Foxconn / Hon Hai 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c45:8603 Microdia 
Bus 002 Device 002: ID 0000:3821  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

