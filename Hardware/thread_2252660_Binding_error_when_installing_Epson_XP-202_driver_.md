---
title: "Binding error when installing Epson XP-202 driver on 14.01 LST"
date: 2014-11-13
forum: Hardware
---

### Post by tamminen on 2014-11-13
I have an updated Ubuntu 14.04 and I am trying to install from Epson support site a package epson-inkjet-printer-escpr but the installation ends in a failure . The erro message is Failed to satisfy all dependecies. Any experience / comments?

Here is the result of the try:

Selecting previously unselected package epson-inkjet-printer-escpr.
(Reading database ... 199266 files and directories currently installed.)
Preparing to unpack .../epson-inkjet-printer-escpr_1.4.4-1lsb3.2_i386.deb ...
Unpacking epson-inkjet-printer-escpr (1.4.4-1lsb3.2) ...
dpkg: dependency problems prevent configuration of epson-inkjet-printer-escpr:
 epson-inkjet-printer-escpr depends on lsb (>= 3.2).

dpkg: error processing package epson-inkjet-printer-escpr (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 epson-inkjet-printer-escpr

Failled to satify all dependecies (broken cache)

---

