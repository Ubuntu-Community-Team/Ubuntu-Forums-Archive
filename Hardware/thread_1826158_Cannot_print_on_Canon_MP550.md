---
title: "Cannot print on Canon MP550"
date: 2011-08-16
forum: Hardware
---

### Post by Åke Dovstam on 2011-08-16
I just installed Ubuntu (a late(st) version with the new desktop windowing) 
and most things seem to be OK at once. But not printing!? 
 
I have a Canon Pixma MP550 connected by USB. The system detects the printer, the system-config-printer utility gives the impression a suitable driver is found (device URL 
usb://Canon/MP550%20series appears).
 
But then, trying the test page option, it stalls: I am told a printing is sent to the device, but nothing is ever written.
 
I would be very glad to get some advice - in what directions to look, to find a solution.

---

### Post by graphius on 2011-08-16
I gave up on Canon printers a while ago when I read on their site they specifically do not support Linux.
However, back before I sold my printer I found a site (in Germany?) that sold a printer driver that worked for most Canon printers. My google foo is not working today, but I seem to remember that it started with an "a"..:(
As I remember, the new driver actually gave better results than the Canon driver under Windows.
Maybe someone else knows the program I am thinking of.


If all else fails, sell the printer and buy an Epson....:D

---

### Post by IcarusR on 2011-08-16
There is a canon linux driver for download here

[http://software.canon-europe.com/software/0037270.asp]("http://software.canon-europe.com/software/0037270.asp")

Failing that turboprint which is commercial software (ie cost money) supports your printer.

[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP550]("http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_MP550")

---

### Post by Åke Dovstam on 2011-08-17
Tried the advised driver MP550_debian_driver_pack downloaded from canon-europe, but the install script failed due to architecture mismatch (package ~ i386 vs. system's amd64). There does no seem to be an AMD variant? - does it really have to depend??

---

### Post by walt.smith1960 on 2011-08-17
> **Åke Dovstam said:**
> Tried the advised driver MP550_debian_driver_pack downloaded from canon-europe, but the install script failed due to architecture mismatch (package ~ i386 vs. system's amd64). There does no seem to be an AMD variant? - does it really have to depend??

Does the Canon site have installation instructions? I have a Brother printer with the same architecture mismatch.  Here's the install command for Brother.  This may or may not work with Canon.
```
dpkg  -i  --force-all  (drivername.deb)
```
There are "switches" other than --force-all but I haven't had to use them and know nothing about them.

---

### Post by Åke Dovstam on 2011-08-17
Using dpkg did not help - same diagnostic...

---

### Post by Åke Dovstam on 2011-08-18
Thanks folks! Guess I'l have to go commercial and pay for it.
On IcarusR's advice, tried Zedonet's driver with TurboPrint: works fine :)

---

