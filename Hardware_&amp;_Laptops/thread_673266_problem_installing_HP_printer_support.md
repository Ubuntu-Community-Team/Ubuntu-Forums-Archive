---
title: "problem installing HP printer support"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by billrosenblatt on 2008-01-20
Trying to install drivers for an HP OfficeJet G85xi on a Dell Latitude C510 laptop running Ubuntu 7.10.  The distro appears to have all the utilities installed already - hp-setup and so on.  But when I try running hp-setup it gives the following:

$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 2.7.7)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PyQt not installed. GUI not available. Exiting.
warning: PyQt init failed. Reverting to interactive mode.

HP Linux Imaging and Printing System (ver. 2.7.7)
Services and Status Daemon ver. 9.2

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.
error: Error occured during interactive mode. Exiting.

Any idea what to do??

THanks

- bill.

---

### Post by linuxwizard on 2008-01-20
You need to install through Synaptic > python-qt3 & python-sip4 > also check to make sure libqt3-mt is installed.

---

