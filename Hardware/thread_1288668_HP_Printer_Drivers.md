---
title: "HP Printer Drivers"
date: 2009-10-11
forum: Hardware
---

### Post by atliia on 2009-10-11
I have been looking around and have not been able to find a similar situation sorry if there is another post.

I am using an HP PSC 1410 All in one. For several years I have not had a problem. I believe there may have been something in a recent update that caused the printer to stop working. I have been been tinkering around with the HPLIP drivers to no avail. This is what I get(code tag) when I run HP set up. It tells me to restart cups. I go to System -> Admin. -> Printing and connect to localhost. Nothing happens. I would appreciate any help. 
```
$ hp-setup

HP Linux Imaging and Printing System (ver. 3.9.8)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/error: No PPD found for model psc_1400_series using new algorithm. Trying old algorithm...
error: No PPD found for model psc_1400 using old algorithm.
error: No appropriate print PPD file found for model psc_1400_series
error:  Printer queue setup failed.  Please restart CUPS and try again.

Done.

```

---

