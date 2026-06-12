---
title: "HP Deskjet 1050 worked with Ubuntu 13.04 but not printing with 14.04"
date: 2014-05-27
forum: Hardware
---

### Post by RayArdia on 2014-05-27
Printer was working fine on Ubuntu 13.04, then shortly after upgrade to  Ubuntu 14.04, when I wanted to print for the first time, I found that the printer was not being found.

The system will not auto-detect the printer so I have had to enter the URI manually - and I'm not sure that I've entered the correct one. Those I've tried without success are -

ipp://cups-server/printers/printer-queue  and ipp://printer.ray(my domain)/ipp

I have changed the printer cable (somewhat in desperation for I've no reason to suspect it), and via questions and responses on Ask Ubuntu, (HP Deskjet 1050 worked with Ubuntu 13.04 but not printing with 14.04) I have endeavoured to check that all is well regarding hplip etc - all seems fine there but I'm open to any suggestions as to how to check again!

Sequence of events is - Laptop restarted with printer ON.   'Settings/Printers/Properties..... Printer Stutus - Connected to Local Host' then -
'Print Test Page....Processing Page 1........Unable to Locate Printer'

Seems, (TO ME !) that the printer is being recognised from the 'connected to local host' bit and the fact that it tries to printthe Test Page. Or am Is that just wishful thinking on my part?

---

### Post by RayArdia on 2014-05-28
Solution was to go to Home-CUPS 1.7.2 and simply follow through the well-written steps. Printer now prints!

Please mark as solved.

---

