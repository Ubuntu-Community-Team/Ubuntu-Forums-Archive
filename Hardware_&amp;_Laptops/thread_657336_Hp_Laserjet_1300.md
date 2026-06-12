---
title: "Hp Laserjet 1300"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by André Lima on 2008-01-03
Everytime that I have to boot my UBUNTU 7.10, the status of my HP LASERJET 1300 is disable.
(I verify the status on system-config-printer.py 0.7.75), I tried to put a script to enable it on boot, but just works on the first job print after this is disable again....

Someone have any sugestion ?

Thanks / Lima

---

### Post by Paul Moir on 2008-01-03
I have been having the exact same problem with a Deskjet 5650 and a PhotoSmart A310 since upgrading to gutsy.  I've wondered if it's related to the bug where cups no longer powers up some HP printers automatically.

I have also been getting error messages in /var/log/cups/error_log like this:

E [03/Jan/2008:21:39:19 +0000] Pause-Printer: Unauthorized
E [03/Jan/2008:21:39:46 +0000] Resume-Printer: Unauthorized

Which might be related too.  Do you have similar error messages?

(And why on Earth does CUPS insist on UTC times rather than local in it's error logs??)

---

