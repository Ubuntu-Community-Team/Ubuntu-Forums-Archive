---
title: "T45 was working but after installing hpijs was no longer found."
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by kmt on 2006-11-11
Hi everyone!

I have an HP T45 all-in-one parallel port printer.  Ubuntu has it in its HP printer list and so I had it working.  However, since it was not perfect, I searched and found:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_T45](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_T45)

where hpijs is the recommended driver.

After installing it the device is not even found:

```
$ sudo hp-setup
Password:

HP Linux Imaging and Printing System (ver. 1.6.10)
Printer/Fax Setup Utility ver. 3.1

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

0
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: <b>No devices found.</b><p>Please make sure your printer is properly connected and powered-on.
```

I am not sure which was the previously installed driver because I see both pcl3 and cdj550 in the driver list (even multiple times!  side question: why do they appear multiple times; how do I remove a driver?).

Switching back to pcl3 driver and LPT #1 makes it work again.

Any idea why hpij did not work for me?

---

