---
title: "More usb ports than letting on?"
date: 2008-12-20
forum: Hardware
---

### Post by Rard on 2008-12-20
I have an IBM X31 laptop. It has two visible external usb ports however lsusb gives me this. 

> 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

and lspci gives this
> 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)


Am I right in thinking this is reporting four USB controllers? There is a docking station that comes with the laptop which has a usb port. I had assumed it simply replaced the port on the back (as it is not accessible when docked) but perhaps not. The fourth one I have no idea about.  

Its a pretty old laptop so I would be interested in using these ports for internal hacks and upgrades. 

I will try to identify the controller chip/s and see if i can get more info that way.

Any thoughts?

---

### Post by cariboo on 2008-12-20
There are probably headers on the motherboard, that you could probably connect a couple more usb connectors to.

If you've got the service manual it will probably show you where they are.

Jim

---

### Post by Rard on 2008-12-20
Okay I think I solved it. I had forgotten my bluetooth card was not turned on. When I switch it on, and plug devices into the two usb ports i get this. 
```

Bus 004 Device 019: ID 0930:6533 Toshiba Corp. 512M USB Stick
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 1668:2441 Actiontec Electronics, Inc. [hex] BMDC-2 IBM Bluetooth III w.56k
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 007: ID 0979:0224 Jeilin Technology Corp., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

So it looks like there are the two usb ports, one internal for the bluetooth card and one that connects through the dock. I may look into installing a hub between the bluetooth card and mobo, in order to get some more internal connections.

---

