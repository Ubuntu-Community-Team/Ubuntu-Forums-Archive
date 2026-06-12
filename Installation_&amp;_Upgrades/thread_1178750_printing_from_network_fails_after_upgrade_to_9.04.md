---
title: "printing from network fails after upgrade to 9.04"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by spotspot on 2009-06-04
I use a Linux box to share a Samsung ML-2510 printer among a couple of Mac OSX machines on our LAN.  After I upgraded (via fresh install) to 9.04 (from 8.something) I was no longer able to print from the network.  Local printing is fine.  When I print the properties of the printer say "SpliX error while rendering the request" and in /var/log/cups/error_log it says:

E [04/Jun/2009:20:17:24 -0400] [Job 50] SpliX Cannot get input slot information.
E [04/Jun/2009:20:17:25 -0400] [Job 50] SpliX Cannot open job
E [04/Jun/2009:20:17:25 -0400] [Job 50] SpliX Error while rendering the request. Check the previous message
E [04/Jun/2009:20:17:25 -0400] PID 4719 (/usr/lib/cups/filter/rastertoqpdl) stopped with status 4!
E [04/Jun/2009:20:17:25 -0400] [Job 50] Job stopped due to filter errors.

when I print from another 9.04 machine it works fine.  One Mac has 10.4 and the other is 10.5 and both are up to date.  Anyone know what's wrong?  I note that SpliX is at 2.0.0....

---

### Post by spotspot on 2009-06-05
the answer is to "allow printing from the internet" in addition to just "publish shared printers connected to this system" which is what i had already turned on.

this is badly labeled since my LAN is certainly not the "internet", and the error message is completely inadequate as well.

---

### Post by sven 22 on 2009-06-06
Hi,

I have the same problem in upgrading from 8.04.

A page prints from the networked (IP 192.168.1.67) HP printer that says "Unable to open the initial device, quitting."

Where do you find "Allow printing from the internet" choice?


Thanks in advance!

---

### Post by sven 22 on 2009-06-06
Hi again,

The HP printer is now working.

I deleted the printer and then went through System-Administration-Printing and had it search for the printer through its IP address, and it found the printer, asked for and found the driver, then offered and printed a test page.

That was easy!

Now to do the same method, I suppose, with the fax function.

---

### Post by chackoge on 2010-01-10
I noticed the same problem with a minor variant. I have a shared ML-2510 hooked up to one Ubuntu 9.04 box and I print from another System 76 configured Ubuntu 9.04 laptop. In order to print from the laptop I have to stop Firestarter on the laptop. If I print from Google Chrome I get the SPlix error. If I print to a pdf file and then open that file with Document Viewer then the print job goes through fine. Infrequently and inconsistently, a print job will cause the modem to choke requiring a reboot.

---

### Post by RingoFyre on 2011-04-09
I went into "Printing" (Applications > System) in xfce. On properties I changed the make/model "driver" from SpliX to foomatic.

---

