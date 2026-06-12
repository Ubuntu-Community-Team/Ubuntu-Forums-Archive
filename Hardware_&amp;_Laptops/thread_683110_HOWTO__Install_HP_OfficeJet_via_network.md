---
title: "HOWTO:  Install HP OfficeJet via network"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Mega_Mike on 2008-01-30
This is how to install an HP OfficeJet multifunction printer so that you can get more than just printing.  By default Ubuntu detects and suggests the high quality driver that only allow printing (not scanning).  These instructions will allow you to add scanner support at the expense of the DPI quality for printing (not an issue if you are not printing pictures).  I tested this on Ubuntu 7.10 with an HP OfficeJet 7400 but since the driver is generic is should work with all HP OfficeJets.

[LIST]
add a new printer
[*]Select network and then in the address section put hp:/net/Officejet_7400_series?ip=192.168.0.1  Replace 192.168.0.1 with the IP address of your HP OfficeJet
[*]In the driver selection choose HP -> OfficeJet and for driver choose pcl3
[*]Leave the rest of the information as default and finish the wizard
[*]Got to /etc/cups and edit the printer.conf file.  Sudo gedit printer.conf
[*]Look for the line DeviceURI ipp://hp:/net/Officejet_7400_series%3Fip%3D192.168.0.1 and change it to DeviceURI hp:/net/Officejet_7400_series?ip=192.168.0.1  Of course replace 192.168.0.1 with the IP of your OfficeJet
[*]Now restart CUPS.  Goto /etc/init.d and type sudo ./cupsys restart
[/LIST]

Now open up XSane in Applications->Graphics and you can now scan images!

---

### Post by K.Mandla on 2008-01-31
Moved to Hardware and Laptops.

---

