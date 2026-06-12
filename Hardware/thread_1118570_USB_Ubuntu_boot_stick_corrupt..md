---
title: "USB Ubuntu boot stick corrupt."
date: 2009-04-07
forum: Hardware
---

### Post by Morat on 2009-04-07
Apologies if this has already been asked and answered before.

My 8.10 USB Boot stick, which I had been using for several weeks, has become unreadable and I need to get some data off it. Also, I'd like to know how I can prevent this in the future.

The stick is a 4gb PNY Micro Attache. It worked perfectly until a couple of days ago, half worked for about a day (stupidly, I did not concentrate on getting data off it!) and now it won't boot at all or even appear as a drive under Windows or Ubuntu.

If I do tail -f /var/log/messages and then plug it in, I get the following:

[INDENT]Apr  7 08:40:53 ubuntu kernel: [ 1796.072084] usb 3-4: new high speed USB device using ehci_hcd and address 7
Apr  7 08:41:24 ubuntu kernel: [ 1826.616191] usb 3-4: new high speed USB device using ehci_hcd and address 8
Apr  7 08:42:00 ubuntu kernel: [ 1862.976182] usb 3-4: new high speed USB device using ehci_hcd and address 9
Apr  7 08:42:31 ubuntu kernel: [ 1893.520283] usb 3-4: new high speed USB device using ehci_hcd and address 10
Apr  7 08:43:01 ubuntu kernel: [ 1924.064182] usb 3-4: new high speed USB device using ehci_hcd and address 11
Apr  7 08:43:12 ubuntu kernel: [ 1934.584183] usb 3-4: new high speed USB device using ehci_hcd and address 12
Apr  7 08:43:22 ubuntu kernel: [ 1945.260263] usb 2-2: new full speed USB device using uhci_hcd and address 10
Apr  7 08:43:53 ubuntu kernel: [ 1975.812178] usb 2-2: new full speed USB device using uhci_hcd and address 11
Apr  7 08:44:23 ubuntu kernel: [ 2006.356204] usb 2-2: new full speed USB device using uhci_hcd and address 12
Apr  7 08:44:34 ubuntu kernel: [ 2016.876179] usb 2-2: new full speed USB device using uhci_hcd and address 13

[/INDENT]and then nothing after that. lsusb takes a long time and finally gives me this:

[INDENT]ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 001 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
[/INDENT]

I installed it using [System]->[Administration]->[Create USB Startup Disk] so is should be set up so it doesn't hammer the drive shouldn't it? Having said that, the drive only cost me about £15 so it may not be that robust.

Any suggestions how I can get the data back from this stick and how to avoid the same problem in the future (maybe I should keep another stick for the data!)

--- Morat.

---

