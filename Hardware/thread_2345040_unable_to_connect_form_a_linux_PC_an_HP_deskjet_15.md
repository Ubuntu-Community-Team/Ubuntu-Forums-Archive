---
title: "unable to connect form a linux PC an HP deskjet 1510 printer attached to a windows XP"
date: 2016-11-30
forum: Hardware
---

### Post by dkarior on 2016-11-30
In my home LAN there are two PCs, one with Windows XP 32 bit, with a  deskejet 1510 attached to it, and a Linux 16.04 LTS PC.  What I am trying to do, is installing the printer to the Linux PC (as a  network printer I guess). I tried the following: 1. Insert printer via printer system settings, choose the samba option,  locate the printer, and select the model from a list. It all seemed ok,  but when I tried to print, the jobs were stucked in the pool. 2. Installed hplip, but I could not find a way to install a samba  printer. It said that it could not find a network printer. 3. I again tried to insert printer via printer system settings, choose  the samba option, locate the printer, but used the ppd files from the  hplip. Now, when I tried to print, the job went to the pool, then the  pool was emptied, and all seemed fine. But nothing ever was printed? What else can I do? Thanks in advance

---

### Post by SeijiSensei on 2016-11-30
What permissions did you set on the printer share in Windows?  Is it available to all users?

You need to use Samba for this since the printer itself isn't directly visible to the Ubuntu machine.

I generally prefer to configure printers in Linux with the built-in utility that comes with CUPS.  On the Ubuntu machine, try opening a browser and pointing it to [http://localhost:631/](http://localhost:631/).  Choose "Administration" from the top, then "Manage Printers." If your printer already appears on the list, click on it and then select Administration > Modify Printer.  Use your own username and password when prompted. Continue onward until you see the list of drivers.  Choose the one that most closely matches your printer's model. You can print a test page by selecting your printer from the Manage Printers list, then clicking the Maintenance button followed by Print Test Page.

If the printer doesn't appear, use the Add Printer button on the Administration page to add it.  You'll be walked through a sequence of steps.

---

