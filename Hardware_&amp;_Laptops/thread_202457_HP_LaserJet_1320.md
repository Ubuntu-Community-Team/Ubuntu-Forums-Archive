---
title: "HP LaserJet 1320"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by jmb365 on 2006-06-23
Hi All,

I have successfully configured an HP LaserJet 1320 to work in "Breezy".  It was straight forward, from the "System Administration" -> "Printing" GUI.  The HP LaserJet 1320 is attached via USB.  Test page printed ok.  No issues here.

Now I would like to use this printer for other networked linux PCs as well - RedHat FC3.  In FC3 it expects the following:

Name: HP1320
Short Description: HP LaserJet 1320
Select Queue Type: Networked CUPS (IPP)
Server: unbuntu3
Path: (What do I specify here?)

When configuring CUPS in FC3 to connect to this printer what "Path" should I be specifying?  I do not have a good understanding of how CUPS works so please go easy on my ignorance.

The relevant portion of /etc/cups/printers.conf is:

<Printer LaserJet-1320>
Info LaserJet-1320
Location
DeviceURI usb://HP/LaserJet%201320%20series
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>


Thanks
JMB

---

