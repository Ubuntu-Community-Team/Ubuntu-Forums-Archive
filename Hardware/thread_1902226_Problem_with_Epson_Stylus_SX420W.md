---
title: "Problem with Epson Stylus SX420W"
date: 2011-12-30
forum: Hardware
---

### Post by SammyM on 2011-12-30
Hi,

I'm trying to get my Epson Stylus SX420W printer to work properly on Ubuntu 10.04, but I'm failing.

I've downloaded and installed the latest pacackage a few times now ([http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/) - epson-inkjet-printer-nx420_1.0.0-1lsb3.2_i386.deb). Installation went fine (while printer was unplugged).

As soon as I connect the printer, it starts "printing" infinite (or at least, a lot!) blank pages. I can't get the printer to stop using the buttons on the printer itself and the printer-queue is empty (system->administration->printers->view printer queue).

When I connect the printer to a Windows laptop, it works just fine.

Can somebody help me?

---

### Post by Mark Phelps on 2012-01-02
I have an older Epson printer and have it working using CUPS.

To try that, open a browser and enter "localhost:631".  That will start CUPS.

Then use the option to Add a printer and see if it finds your Epson.  IF it does, continue through the process, including choosing a driver -- and see if that works.

---

### Post by desconocido on 2012-03-14
I have the same model printer. I used the same package as you but I am using Karmic (Ubuntu 9.10 Karmic (kernel 2.6.31-22)). It works fine for me.

I did not use cables. I set up the access to the WiFi network using the control panel on the printer. I then used Ubuntu menu System->Administration->Printing and clicked on New and clicked on Network Printer.

Sorry I cannot be of more help.

---

