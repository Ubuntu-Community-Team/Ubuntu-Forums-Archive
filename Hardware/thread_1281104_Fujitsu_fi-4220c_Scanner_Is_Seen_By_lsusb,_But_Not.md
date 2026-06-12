---
title: "Fujitsu fi-4220c Scanner Is Seen By lsusb, But Not By xSANE"
date: 2009-10-02
forum: Hardware
---

### Post by DrewT on 2009-10-02
Okay, I guess I've read enough marginally related threads, with no joy, to start my own on this problem.

When I plug my fi-4220c directly into the USB jack on the front panel of my computer, xSANE has no trouble seeing it. But when I plug it into a USB hub -- which works for every other USB peripheral I've ever plugged into it -- xSANE reports No Devices Found. But if I immediately run lsusb, there it is: 

> druid@Jove:~$ lsusb
Bus 001 Device 010: ID 04c5:1042 Fujitsu, Ltd fi-4220c Scanner
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

Granted, I can work around this by running a USB cable across my lap, but I'd prefer a more elegant solution, if there is one.

I'm running 9.04-amd64.

---

### Post by DrewT on 2009-10-04
This will teach me not to post on the eve of a new release. Anybody?

---

