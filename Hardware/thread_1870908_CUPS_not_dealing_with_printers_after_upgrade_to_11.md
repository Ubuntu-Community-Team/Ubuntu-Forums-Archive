---
title: "CUPS not dealing with printers after upgrade to 11.10"
date: 2011-10-28
forum: Hardware
---

### Post by pacut on 2011-10-28
After upgrading to 11.10, printer stops working.

Lsusb shows that printer is connected, as well as the flash-card reader in it:

Code:

Bus 001 Device 003: ID 04b8:0803 Seiko Epson Corp. Printer (Composite Device)
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

Other users on other forums said it is a matter of CUPS upgrading to latest version (1.5). Doing a downgrade to ver 1.4.6 is the trick that solves this issue.

Question is: how this downgrade can be done ? Which packets ?

Thanks

---

### Post by pacut on 2011-10-29
In this post there is the solution

[http://ubuntuforums.org/showthread.php?p=11405217#post11405217](http://ubuntuforums.org/showthread.php?p=11405217#post11405217)

---

