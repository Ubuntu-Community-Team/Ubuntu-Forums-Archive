---
title: "USB transfer very very slow"
date: 2010-11-08
forum: Hardware
---

### Post by tribaldata on 2010-11-08
Hi, 

I just installed a fresh version of the Server Edition 10.10.

I'm running into some very slow speed while transferring to and from my USB external drive. (1Tb LaCie):confused:

Here some information about my setup:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       92513   743110641    7  HPFS/NTFS
/dev/sdd2   *       92514      121601   233649360    1  FAT12

This is the input of hdparm -tT on /dev/sdd:
Timing cached reads: 2 MB in  3.77 seconds = 542.95 kB/sec
Timing buffered disk reads: 2 MB in  3.40 seconds = 602.91 kB/sec

Any help will be appreciated.

EDIT: Here is the info from dmesg
cat dmesg* | grep USB
[    0.452937] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.452997] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.453030] uhci_hcd: USB Universal Host Controller Interface driver
[    0.453322] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.453739] hub 1-0:1.0: USB hub found
[    0.454035] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    0.454391] hub 2-0:1.0: USB hub found
[    0.814604] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    2.187264] Initializing USB Mass Storage driver...
[    2.233875] USB Mass Storage support registered.
[    0.452846] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.452905] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.452939] uhci_hcd: USB Universal Host Controller Interface driver
[    0.453229] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    0.453645] hub 1-0:1.0: USB hub found
[    0.453939] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[    0.454297] hub 2-0:1.0: USB hub found
[    0.815110] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    2.197567] Initializing USB Mass Storage driver...
[    2.233022] USB Mass Storage support registered.

---

### Post by ajgreeny on 2010-11-08
It looks as if you are using a hub to do this and not direct into usb ports.

1.  If that's so, try a direct connection instead.

2.  Are you sure all the hardware is USB2 compliant?

---

### Post by tribaldata on 2010-11-09
Hi, 

Thanks for the response, after further reading and testing i established that the USB port were in fact USB1.1 Compliant only...

So in short i've been beating a dead horse... Sorry about that...

---

