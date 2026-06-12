---
title: "HP Laserjet won't print on network connection"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by m_vrik on 2006-11-16
I can't get my printer, HP Laserjet 6P, to print correctly.  The proerties for this printer show Laserjet 6P/6MP and the Network printer connection CUPS (IPP) indicate a URI of "usb://HP/Laserjet 6P.  When I try to print a test page all I get is (on five different lines) the following:
"%!PS-Adobe-3.0,%%Title:PPR Test Page,%%DocumentNeededResources: font Helvetica,%%For:lem,%RBINumCopies".  After this first page prints then the printer continues to print blank pages until I cancel the print job and turn off the printer.  Can you help?

---

### Post by likwidoxigen on 2006-11-16
Hey I had a similar problem with my HP1100. Try switching to another driver. I changed from the post script driver to a generic HP driver, there shoudl be 4 (i think, don't quote me) available drivers for your printer, try each i'm sure one will work. Good luck. Hope this helps.


Cheers.
Bryce

---

### Post by bluebirday on 2006-11-17
I did face the same problem with HP LaserJet 1100 but I discovered one important thing ... Since everything was Ok and the printer shown Ready
as per CUPS but it does not print out ... I discovered one new thing:
1- If you are connected through network .. do not use the CUPS
2- Use Network Printer - Windows Printer (SMB)
3- Put the host name and you will find the software complete itself

How I did help 
Regards

---

### Post by m_vrik on 2006-11-18
I tried using different drivers and switching to SMB but to not avail.  Since, I just switching my printer cable from one computer to another, even thought both laptops connect to the internet via a common router, I'm assuming that I should use the local printer connection. Even with that the printer now doesn't seem to be getting any print data.

---

