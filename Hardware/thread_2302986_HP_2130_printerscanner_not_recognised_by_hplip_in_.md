---
title: "HP 2130 printer/scanner not recognised by hplip in Vivid 15.04"
date: 2015-11-15
forum: Hardware
---

### Post by pickarooney on 2015-11-15
I got a new printer/scanner/copier and was able to set up the printer in a couple of seconds in the XFCE printer manager and CUPS handles it just fine.
However, no scanner program works with it and hplip / hp-setup don't recognise that there is a device installed.

**lsusb**
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 03f0:e111 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**sudo hp-setup**
```
sudo hp-setup -i 03f0:e111

HP Linux Imaging and Printing System (ver. 3.15.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)

 
--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 

Using connection type: usb

error: No device selected/specified or that supports this functionality.

```

Has anyone a solution for this?

---

### Post by pickarooney on 2015-11-19
Sorry for bumping but I have absolutely no leads on this. Is it just a problem with this scanner and linux or with this version of Ubuntu... ?

---

### Post by pickarooney on 2015-11-20
This fixed itself with an update to 15.10!

---

