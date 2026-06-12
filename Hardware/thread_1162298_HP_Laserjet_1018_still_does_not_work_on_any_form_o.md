---
title: "HP Laserjet 1018 still does not work on any form of Ubuntu, 3 years now"
date: 2009-05-17
forum: Hardware
---

### Post by fuwkej on 2009-05-17
Still cannot get Ubuntu to print to HP Laserjet 1018, tried on three different computers with Ubuntu, only works on Windows. The issue is with Ubuntu. I'm about to dump Ubuntu.

---

### Post by IronArjen on 2009-06-04
This is actually a problem of the 1018 printer. It really sucks but for instance Mac has the same problems with this printer, and even on certain windooze machines it seems not to work. It is likely a buffer or cache problem: the printer does not effectively empty its memory.

What works for me is once it no longer works, logiin to my Windooze partition, switch the printer off for a few seconds switch it on again, print a test page. Switch off the computer, switch off the printer, switch on the computer, once login is complete, print via foomatic drivers. Normally then i have no problems for a month or so (print every day)

Hope it words for you too. 

Another possibility is to use the propietary HPLIP, I tried this in 9.04 with the gui and it yielde me a specified error that I should solve, haven't pursued that yet but I will and post the result back.

good luck

---

