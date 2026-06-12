---
title: "Sharp AR 5320 cannot be detected"
date: 2008-07-12
forum: Hardware
---

### Post by sleepya on 2008-07-12
I tried to connect Sharp AR 5320 to Ubuntu Desktop 8.04.1. Ubuntu does not show anything on desktop. At least (I hope), it should display some message like "found new printer".

I get the following output from 'dmesg'

[10374.170296] usb 1-1: new full speed USB device using uhci_hcd and address 32
[10374.379614] usb 1-1: configuration #1 chosen from 1 choice
[10374.428468] usblp0: USB Bidirectional printer dev 32 if 0 alt 0 proto 2 vid 0x04DD pid 0x9051
[10374.810917] usblp0: nonzero read bulk status received: -84
[10375.065019] usb 1-1: USB disconnect, address 32
[10375.065339] usblp0: removed
...

The same message blocks are displayed without stopping with different address.

Does anyone have a idea about these error message?

---

### Post by hansdown on 2008-07-12
Hi sleepya,I just googled your copier, and sorry to say, the supported operating systems are, windows nt,2000,xp,95/98/me. Most hp printers are able to run on ubuntu because hp is one of the few companies that is willing to supply the drivers for ubuntu. You will need python qt3 and hplip to run them.sorry about the sharp printer. hope this will help You,as having a printer was the last thing I needed to be free of microsoft.

---

