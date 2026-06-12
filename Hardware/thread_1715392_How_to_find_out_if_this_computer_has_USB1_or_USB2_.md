---
title: "How to find out if this computer has USB1 or USB2 ports?"
date: 2011-03-26
forum: Hardware
---

### Post by ntu on 2011-03-26
How to find out if this computer has USB1 or USB2 ports please?

---

### Post by wojox on 2011-03-26
Try 

```
lsusb
```

---

### Post by ntu on 2011-03-26
Thank you for your reply Wojox. I get:

> gb@gb-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gb@gb-desktop:~$ 

I presume this means only one is USB2 and so now I am wondering how to find out which one it is?

---

### Post by Dark_Stang on 2011-03-26
Plug in a flash drive, and copy files back and forth. The USB 2.0 port(s) will be significantly faster.

Also, just because 1 USB 2.0 device is listed, that doesn't mean there is only one port. One device could have several physical ports running off it.

---

### Post by ntu on 2011-03-27
Thanks DS. At least I know I have at least one USB2 port:). I am thinking of buying a device like the one shown here :
[http://www.trademe.co.nz/Computers/External-storage/Other/auction-363500515.htm](http://www.trademe.co.nz/Computers/External-storage/Other/auction-363500515.htm)
and it needs usb2. I also need to investigate whether it or something similar will work with Linux.

---

### Post by Yellow Pasque on 2011-03-27
Just plug your USB peripheral into the different ports and see which bus it uses with lsusb: In this example, my mouse and gamepad are hooked to USB 1.1 hubs, while my wireless adapter is running on a USB 2.0 hub.
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 005 Device 002: ID 046d:c216 Logitech, Inc. Dual Action Gamepad
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
```

---

### Post by ntu on 2011-03-27
Thank you for your reply Temujin. Here is what I get when I plug 3 flash drives in (the only usb gear I have):

```
gb@gb-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1043:8012 iCreate Technologies Corp. 
Bus 001 Device 005: ID 0718:0245 Imation Corp. 
Bus 001 Device 004: ID 1043:8012 iCreate Technologies Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
gb@gb-desktop:~$ 
```

So it looks like at lease those 3 ports are all usb2.

---

