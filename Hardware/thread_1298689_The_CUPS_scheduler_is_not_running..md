---
title: "The CUPS scheduler is not running."
date: 2009-10-23
forum: Hardware
---

### Post by MadMax2 on 2009-10-23
I have lost the use of the printer.
If I go to preferences >printer I get this message:
"CUPS server error

The CUPS scheduler is not running."

/etc$ ls -l has this highlighted but I don't know what to do about it:


lrwxrwxrwx  1 root root        22 2009-07-03 09:02 printcap -> /var/run/cups/printcap

This seems to have happened after the receiving the latest support package.

Printer is HP PSC 1500   
 Thanks for your help

---

### Post by MadMax2 on 2009-10-24
I solved this by reinstalling cups 

sudo apt-get install cupsys cupsys-client

and via synaptic the driver Driver is hpijs, 3.9.2
(after checking on the linux printer driver website).

---

