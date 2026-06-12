---
title: "Fiesty usb hub disconnect/reconnect"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by cakirke on 2007-05-10
Belkin 4-port usb hub disconnects/reconnects every 30 seconds but the devices connected to it (including the keyboard i'm typing on) remain available.  currently running Fiesty - this problem didn't occur prior to upgrading from Edgy.

hardware is a Dell D820

from lsusb:

Bus 003 Device 031: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 003 Device 029: ID 0b97:7761 O2 Micro, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:8115 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 013: ID 0bb4:0bce High Tech Computer Corp. 
Bus 001 Device 007: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 008: ID 045e:00db Microsoft Corp. 
Bus 001 Device 005: ID 03f0:4f11 Hewlett-Packard 
Bus 001 Device 006: ID 046d:c508 Logitech, Inc. 
Bus 001 Device 004: ID 413c:0058 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  

from /var/log/messages:

May 10 18:43:30 us-cak-mobile kernel: [31945.600000] usb 3-1: USB disconnect, address 5
May 10 18:43:30 us-cak-mobile kernel: [31945.600000] usb 3-1.1: USB disconnect, address 6
May 10 18:43:30 us-cak-mobile kernel: [31945.600000] usb 3-1.2: USB disconnect, address 7
May 10 18:43:30 us-cak-mobile kernel: [31945.712000] usb 3-1: new full speed USB device using uhci_hcd and address 8
May 10 18:43:30 us-cak-mobile kernel: [31945.864000] usb 3-1: configuration #1 chosen from 1 choice
May 10 18:43:30 us-cak-mobile kernel: [31945.864000] hub 3-1:1.0: USB hub found
May 10 18:43:30 us-cak-mobile kernel: [31945.868000] hub 3-1:1.0: 3 ports detected
May 10 18:43:30 us-cak-mobile kernel: [31946.180000] usb 3-1.1: new full speed USB device using uhci_hcd and address 9
May 10 18:43:30 us-cak-mobile kernel: [31946.316000] usb 3-1.1: configuration #1 chosen from 1 choice
May 10 18:43:31 us-cak-mobile kernel: [31946.520000] usb 3-1.2: new full speed USB device using uhci_hcd and address 10
May 10 18:43:31 us-cak-mobile kernel: [31946.640000] usb 3-1.2: configuration #1 chosen from 1 choice
May 10 18:44:00 us-cak-mobile kernel: [31975.604000] usb 3-1: USB disconnect, address 8
May 10 18:44:00 us-cak-mobile kernel: [31975.604000] usb 3-1.1: USB disconnect, address 9
May 10 18:44:00 us-cak-mobile kernel: [31975.604000] usb 3-1.2: USB disconnect, address 10
May 10 18:44:00 us-cak-mobile kernel: [31975.716000] usb 3-1: new full speed USB device using uhci_hcd and address 11
May 10 18:44:00 us-cak-mobile kernel: [31975.868000] usb 3-1: configuration #1 chosen from 1 choice
May 10 18:44:00 us-cak-mobile kernel: [31975.872000] hub 3-1:1.0: USB hub found
May 10 18:44:00 us-cak-mobile kernel: [31975.872000] hub 3-1:1.0: 3 ports detected
May 10 18:44:00 us-cak-mobile kernel: [31976.184000] usb 3-1.1: new full speed USB device using uhci_hcd and address 12
May 10 18:44:01 us-cak-mobile kernel: [31976.320000] usb 3-1.1: configuration #1 chosen from 1 choice
May 10 18:44:01 us-cak-mobile kernel: [31976.524000] usb 3-1.2: new full speed USB device using uhci_hcd and address 13
May 10 18:44:01 us-cak-mobile kernel: [31976.640000] usb 3-1.2: configuration #1 chosen from 1 choice

addresses will climb to 127, then roll over

has anyone else seen this ??

---

### Post by cakirke on 2007-05-31
i've updated to Dell A06 bios and the latest kernel with no change in symptom - after more testing, it appears that the usb hub in question is the one internal to the laptop ...

Chris

---

### Post by NoMojoMofo on 2007-11-13
> **cakirke said:**
>  
Bus 001 Device 013: ID 0bb4:0bce High Tech Computer Corp. 


HEY!  Are you able to connect to your HTC from Ubuntu?

---

### Post by cakirke on 2007-11-13
i've been able to connect, charge, and use the synce stuff but haven't had much luck with synchronizing with evolution, even using most current (0.34) version of OpenSync.  i used the info at:

[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2005_device_via_USB_%28usb-rndis-lite%29)

as my guide.  even on Gutsy, you either have to rebuild rndis_host or just replace with the build described for pre-2.6.21 kernel.  you also need to go to Programs -> Accessory -> USBSwitch on the device and set RNDIS mode (this seems to get reset to Serial with every reboot).  btw, my phone is a Cingular 8125 (not sure if USBSwitch is particular to it).

---

