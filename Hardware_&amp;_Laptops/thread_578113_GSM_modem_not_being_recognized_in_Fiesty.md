---
title: "GSM modem not being recognized in Fiesty"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by vnums on 2007-10-16
Hello,

I am relatively new to Ubuntu (and Linux in general).  Now that that's out of the way...

In our office we have a server that is currently hooked up to a GSM modem on a serial port and is sending/receiving SMS messages as part of our service.  We are now in the process of creating a test server to work in the same fashion as our production server for debugging/testing purposes.

We have come across the problem where the modem is not being recognized on the serial port for our test server.  We've tried installing/using a PCI serial card to no avail, used the built-in serial port to no avail.  We then installed windows on the machine and the modem is recognized/works fine (meaning it's not a hardware issue).  We've also tried the other modem currently on the production server and it is not recognized on our test server either.

To check connectivity we've been using "gnome-phone-manager".  It's not being recognized on ttyS0-3, and we're at a loss as to why.  We've been doing some research online and the few people who have posted solutions to their specific problem, those solutions aren't working.  

We were thinking that the serial port might be sharing an IRQ with another device but that doesnt seem to be the case either.  

We've tried creating links and configuring the ttyS0 with the 'setserial' command, which also doesnt seem to work.

I guess my question, then, is: Has anyone come across the problem where a serial device isnt recognized by Ubuntu and have they found a way to solve said problem? Or, are there any utilities available that may help us debug this issue?  I'm 100% positive that this modem/hardware configuration will work perfectly with Ubuntu as it already is on our other system.  Any help would be greatly appreciated.

Thanks!

---

### Post by eggcaker on 2007-10-16
same problem for me ...

---

