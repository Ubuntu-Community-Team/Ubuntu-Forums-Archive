---
title: "Laser Printer Only Prints Out Small Portion of Document"
date: 2010-06-05
forum: Hardware
---

### Post by jrd43 on 2010-06-05
The facts:
Running Ubuntu 10.04
Have old NEC SuperScript 860 with parallel cable connected to parallel>USB adapter, connected to computer
Printer easily detected and installed 
Per other threads I learned about Device URI: parallel:/dev/usb/lp0, which I am using
Using driver Foomatic/lp2 (tried all others - had the most success with this one)

Now, the computer and the printer ARE COMMUNICATING, and I know this because the printer usually prints the top 1/4" of the document before rolling out the rest of the page blank, and the job comes up as "Stopped" in the print queue (the rest of the time, nothing happens before it comes up as "Stopped").  What I find peculiar is that when I right-click on the "Stopped" job and click "View Attributes" the "printer URI" is listed as "ipp://localhost/printers/NEC_SuperScript_860" (why not parallel:/dev/usb/lp0 as is entered next to "Device URI" in "Printer Properties"???) - I wonder if this is the source of the problem.

Any new ideas would be greatly appreciated.

---

### Post by thodges999 on 2010-06-08
> **jrd43 said:**
> The facts:
Running Ubuntu 10.04
Have old NEC SuperScript 860 with parallel cable connected to parallel>USB adapter, connected to computer
Printer easily detected and installed 
Per other threads I learned about Device URI: parallel:/dev/usb/lp0, which I am using
Using driver Foomatic/lp2 (tried all others - had the most success with this one)

Now, the computer and the printer ARE COMMUNICATING, and I know this because the printer usually prints the top 1/4" of the document before rolling out the rest of the page blank, and the job comes up as "Stopped" in the print queue (the rest of the time, nothing happens before it comes up as "Stopped").  What I find peculiar is that when I right-click on the "Stopped" job and click "View Attributes" the "printer URI" is listed as "ipp://localhost/printers/NEC_SuperScript_860" (why not parallel:/dev/usb/lp0 as is entered next to "Device URI" in "Printer Properties"???) - I wonder if this is the source of the problem.

Any new ideas would be greatly appreciated.

I don't think its this as my device uri is also parallel:/dev/usb/lp0 and I get a similar printer-uri 'ipp://localhost/printers/HP-Laserjet-4' but no problem with printing.

---

### Post by ngrieb on 2010-06-24
I have the same problem, I'm printing on an HP 6300 series printer, but I can only manage about 1 and 1/4 pages before the printer stops printing. The queue says that the job is still pending, but nothing is going on. 

It seems almost like the print queue is too small to support the memory of more than a few pages at a time. Does anyone else have this problem? I'm using Ubuntu 9.10. Thanks.

---

