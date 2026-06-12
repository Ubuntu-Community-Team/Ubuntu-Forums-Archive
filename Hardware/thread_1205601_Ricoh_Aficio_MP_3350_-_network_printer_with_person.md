---
title: "Ricoh Aficio MP 3350 - network printer with personal user code"
date: 2009-07-06
forum: Hardware
---

### Post by chichilalescu on 2009-07-06
Hello,

At the office we have a printer that the entire floor uses (copying machine/printer/fax etc).
I installed it in ubuntu 9.04 in two minutes (just told it to search for a network printer, it found it, and installed the drivers for it).
Everybody else at the office is using mac os or windows, and I'm the first linux user that needs to use this printer.
Each user has a code assigned, so that they can track how much each of us is printing, and my problem is that I can't see where to put in this code.
Does anyone have any experience with this printer?

---

### Post by chichilalescu on 2009-07-07
solved it (putting in some basic information if anyone else needs it).

I installed the deb from [http://www.linuxprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_MP_3350](http://www.linuxprinting.org/show_printer.cgi?recnum=Ricoh-Aficio_MP_3350), and when adding the printer I said I had a custom ppd file (the one from the above page).

Then I modified the usercode in the ppd file, and I was able to choose it somewhere in the options for the printer.

the big problem was installing the deb, because it required the lsb package, which in turn required a forced version for qt4. anyway, it was suspiciously complicated to use this printer (I'd gotten used to ubuntu working for everything).

---

