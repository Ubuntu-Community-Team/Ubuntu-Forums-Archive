---
title: "USB read problem"
date: 2009-05-14
forum: Hardware
---

### Post by rado3105 on 2009-05-14
Hi I have usb printer HP. When I connect it, it is doesnt recognized.
In dmesg:

> [  493.056347] usb 1-1.4.3: new high speed USB device using ehci_hcd and address 9
[  508.140289] usb 1-1.4.3: device descriptor read/64, error -110
[  516.072838] hub 1-1.4:1.0: unable to enumerate USB device on port 3
[  521.168020] usb 1-2: new high speed USB device using ehci_hcd and address 10
[  527.776247] ppdev0: registered pardevice
[  527.824087] ppdev0: unregistered pardevice
[  536.280047] usb 1-2: device descriptor read/64, error -110
[  551.496028] usb 1-2: device descriptor read/64, error -110
[  551.656335] hub 1-0:1.0: unable to enumerate USB device on port 2
[  551.896024] usb 1-2: new high speed USB device using ehci_hcd and address 12
[  567.008023] usb 1-2: device descriptor read/64, error -110
[  582.224047] usb 1-2: device descriptor read/64, error -110
[  582.384257] hub 1-0:1.0: unable to enumerate USB device on port 2
[  582.384550] ppdev0: registered pardevice
[  582.432426] ppdev0: unregistered pardevice
[  582.624025] usb 1-2: new high speed USB device using ehci_hcd and address 14
[  597.748046] usb 1-2: device descriptor read/64, error -110
[  612.964022] usb 1-2: device descriptor read/64, error -110
[  613.124298] hub 1-0:1.0: unable to enumerate USB device on port 2
[  613.364026] usb 1-2: new high speed USB device using ehci_hcd and address 16
[  628.476026] usb 1-2: device descriptor read/64, error -110
[  643.692026] usb 1-2: device descriptor read/64, error -110
[  643.852342] hub 1-0:1.0: unable to enumerate USB device on port 2
[  643.852720] ppdev0: registered pardevice
[  643.900211] ppdev0: unregistered pardevice
[  644.127171] usb 1-2: new high speed USB device using ehci_hcd and address 18
[  659.236045] usb 1-2: device descriptor read/64, error -110
[  674.464025] usb 1-2: device descriptor read/64, error -110
[  674.624264] hub 1-0:1.0: unable to enumerate USB device on port 2
[  674.864028] usb 1-2: new high speed USB device using ehci_hcd and address 20
[  689.988021] usb 1-2: device descriptor read/64, error -110

---

### Post by mechdave on 2009-05-14
You need to run hp-setup from the command line (terminal) to get it all working. HP are very good at supporting Linux, mine was a hassle free setup :)

---

### Post by rado3105 on 2009-05-14
> r-c@r-c-desktop:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.9.2)
Printer/Fax Setup Utility ver. 8.0
Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: You must be root to run this utility.
r-c@r-c-desktop:~$ sudo hp-setup
[sudo] password for r-c: 

HP Linux Imaging and Printing System (ver. 3.9.2)
Printer/Fax Setup Utility ver. 8.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb

doesnt look like printer driver problem, it writes No USB device, and also the error in dmesg.

---

