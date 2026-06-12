---
title: "LPT to USB converter cable problem"
date: 2009-03-14
forum: Hardware
---

### Post by tornadof3 on 2009-03-14
So I have a HP LaserJet 4000 (tn) printer which has only a parallel cable connection. I got a cable from ebay that has parallel one end and USB the other. With HP LIP installed, the printer seems correctly configured in UBuntu (8.10), which is fully updated etc.

However, for a disturbing majority of the time now, I cannot print because the system insists the printer is not connected. Sometimes, restarting cups, or unplugging and replugging helps. Sometimes it can be printing a document fine, then you send the next one to print and it won't come out. The other day when I desperately needed to get something printed, no amount of restarting (laptop or cups/hal), swapping or toggling could  get this darn thing printed.

Has anyone heard anything like this before or know of any solutions, it's driving me mad!

---

### Post by sgosnell on 2009-03-14
Have you installed the driver for the converter?  It takes software to correctly convert a USB connection to an LPT connection.  I would be surprised if there are even Linux drivers available, but I've been surprised before.  The Windows drivers might work, if you have them.  The cable should have shipped with drivers.

---

### Post by tornadof3 on 2009-03-14
Yes this was auto-detected. It lists a CH34x printer adapter cable, and a USB printer-interface icon. As I say, this cable sometimes works. Print outs when they do work are flawless.

---

### Post by sgosnell on 2009-03-15
Well, it seems you either have a problem with the cable having an intermittent connection, or a software problem.  Intermittents can be very hard to troubleshoot.  I know nothing about your setup, so about all I can suggest is wiggling the cable a little when it doesn't work, and looking at the driver configuration, however that is done.  I've seen many USB ports that didn't provide a solid connection, especially when something heavy had been attached for awhile.

---

