---
title: "Printing problem in 9.04"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by ted_001 on 2009-04-30
Dear All,
I have no idea if this is the right place to post this thread, but here goes.  I upgraded to 9.04 from 8.10 today.
Unfortunately I am having a printing problem.
Both in OpenOffice and in gedit some characters just print as a black square.  This seems to happen at random, and the same character is not affected twice.
I can't print out any of my documents without these black squares occuring about every 48 characters.
I am using a HP 1200 LaserJet printer that worked fine under 8.10.
Regards,
Ted

---

### Post by ted_001 on 2009-04-30
Dear All,
I have solved the printing problem - I think.  The upgrade from 8.10 to 9.04 changed the printer driver to:-

 Foomatic/pxlmono [en].

I have now changed it back to the HP provided driver:-

hpijs [en]

The printer is now working fine.
Regards,
Ted Mason

---

### Post by pietro2580 on 2009-05-13
I have exactly the same problem after upgrading to 9.04, also with .pdf-files by the way.
I checked the printer driver (Ricoh3250), but in contrary to what is the situation above, this is the correct one for me.

---

### Post by pietro2580 on 2009-05-13
A very similar problem is reported by someone else as a "bug":
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/372712](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/372712)

---

### Post by pietro2580 on 2009-05-13
Dear all,

I found the solution here:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/ghostscript/+bug/361772](https://bugs.launchpad.net/ubuntu/jaunty/+source/ghostscript/+bug/361772)

Depending on which printer you have, different solutions are provided. For HP it might indeed be related with the driver. 
However for other printers (Ricoh, Gestetner, Infotec, Lanier, NRG,...) it the solution might be to change the pdftops file in /usr/lib/cups/filter/ with the pdftops-file on this URL:
[http://launchpadlibrarian.net/26433224/pdftops](http://launchpadlibrarian.net/26433224/pdftops)

This worked in any case for me, but other options are provided in the link above.

Good luck

---

