---
title: "HP OfficeJet G85, USB not working"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by sleightholme on 2005-10-07
I installed Ubuntu 5.04 a few days ago - no errors.

Trying to print, I have an HP OfficeJet G85 conected via a USB port.

Ubuntu recognised the printer fine during AddPrinter, and allows me to print to it, there is just no output on the printer. Print manager reports the prints going through without an issue.

The printer is connected fine ( works under Windows on same machine ) and did work under Mandrake 10.1 before I overwrote it with Ubuntu.

Anyone got any ideas ?

---

### Post by jasmuz on 2005-10-07
Remove the driver instalation you made and reinstall, as it works 'out of the box' with me.

---

### Post by sleightholme on 2005-10-07
I didn't install any drivers - just added the printer in System/Admin/Printing

I just tried to remove the printer from the above - atried again the options for printing are to PDF file or Generic Postscript - tried the latter, but not luck.

Also, the computer can see/recognise the printer is on the USB port :-

$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:0211 Hewlett-Packard
Bus 001 Device 002: ID 0707:0201 Standard Microsystems Corp.
Bus 001 Device 001: ID 0000:0000

---

### Post by jasmuz on 2005-10-08
Fairly odd, as i have done the same as you and it keeps on working.-

---

### Post by David Haas on 2005-10-09
sleightholme--I see that Ubuntu 5.04 has two drivers (PPD files) for the HP Office Jet G85, so your printer should work in Ubuntu. These are HP-OfficeJet_G85-cdj550.ppd.gz and HP-OfficeJet_G85-hpijs.ppd.gz. They are in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. Sometimes one works better than the other. 

I'd return to the Gnome Printer Manager at System>Administration>Printing and delete the chosen printer there at the icon, and then select "New Printer." Then reselect the HP OfficeJet G85 and then click on select driver. Here you can click through the directory listings to get to the HP directory as listed in the above series. Then select one of the two PPD files (I'd try the hpijs one first). After selected, Linux should place an unzipped copy in /etc/cups/ppd--you should then check this in your terminal.

Well, let me know how it goes or whether you have other questions about installing this printer.

David

---

### Post by schwermie on 2005-10-31
I'm having the same problem. Both drivers won't work. Any idea???

lsusb

Bus 005 Device 003: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 03f0:0211 Hewlett-Packard
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by jmfrey on 2005-11-07
I too am having difficulties with the HP Officejet G85.

I'm using Ubuntu Server 5.10.

I have my devices connected to the usb port via a hub.   All of my devices are recognized...

user@host:~$ lsusb
Bus 001 Device 005: ID 03f0:b602 Hewlett-Packard
Bus 001 Device 004: ID 0d49:7010 Maxtor
Bus 001 Device 003: ID 03f0:0211 Hewlett-Packard
Bus 001 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000

Device 003 is the Officejet.  Device 005 is a Photosmart, which works fine through CUPS by the way.

Both of the printers were setup via CUPS web interface.  Test pages work fine on Photosmart, but not on Officejet.

Additionally, I've tried to print to them over samba, no luck as of yet.

If anyone has solved the G85 issue, I would appreciate any assistance.

---

### Post by calvinpriest on 2005-11-07
Yep, me too.  Or rather, I have a friend I've been helping who has a G85 and we're seeing the exact same thing.

Unfortunately, in his case, this is a bit of a deal-breaker.  He has several people living in his house who need some convincing, and until the printer works they're going to keep using Windows XP.

---

