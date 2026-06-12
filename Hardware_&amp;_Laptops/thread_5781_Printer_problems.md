---
title: "Printer problems"
date: 2004-11-22
forum: Hardware &amp; Laptops
---

### Post by bob k on 2004-11-22
I have a Samsung ML1750 Laser printer. when ever I try to print some thing the printer will wake up but nothing will print. The printer is on usb1 and is identified as a ML-1750. I checked the printer setup and it has it as paraport type device and I mapped it to the usb1 device that my printer is on.

Any ideas what to do next?

Bob

---

### Post by az on 2004-11-22
You can look here:

[http://linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1750](http://linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1750)

What driver are you using?

I am not clear on what you described about the parport?

---

### Post by WW on 2004-11-22
I have an ML-1750, and it works for me.  I am using the USB interface. I have attached screen shots of the Driver and Connection tabs in the Printer Properties.

---

### Post by bob k on 2004-11-22
Thats what mine looks like. I have removed and and redefined it and it still dosen't work. When I try to print a test page the printer starts up and nothing gets printed and nothing gets queued to the print queue waiting to print, so I would assume that the driver thought it printed.

I figured it out I bought 2 of these printers and they sent me a ml-1740 for one of them. Since there is no entry for this printer I guess I am going to have to download the driver or figure a way to tell the os that is is a ML-1740.

---

### Post by skipsjh on 2004-11-24
Have you tried just defining it as a Generic Postscript Printer?  This usually works.  You don't have all the printer-specific controls, but It'll print alright more than likely.

~Scott

---

### Post by bob k on 2004-11-24
[QUOTE=skipsjh]Have you tried just defining it as a Generic Postscript Printer?  This usually works.  You don't have all the printer-specific controls, but It'll print alright more than likely.

~Scott[/QUOTE]
 I got it working by going to the ML-1710 defined printer. The print quality is good the only problem is that the print job does not get removed from the print queue when finished and holds the printer open with a status of printing.

I tried to install the Samsung Lunix driver for this printer but it did not like the way Ubuntu handles the Root account, and since the GUI was not a script I couldn't figure out what it was chocking on.

I don't print to much right now, as this is not a production machine, I will live with it. If it becomes a show stopper later on I will just buy another 1570 and be done with it.

I rebooted today and that fixed the print queue problem. All is working normal. I figured out what a ML-1740 is, it is a ML-1710 that prints faster. The 1750 adds 600x1200 support at the same speed.

---

