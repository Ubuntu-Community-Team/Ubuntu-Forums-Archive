---
title: "kmfilter and Konica Minolta Printer"
date: 2009-09-09
forum: Hardware
---

### Post by mpsz on 2009-09-09
Hi, 
I tried to install for my Konica Minolta Bizhub 160 a file PPD I dowloaded from KonicaMinolta website.
But when I try to install it I get this error.

I looked on the Internet but didn't find anything about this Kmfilter...

Falta el controlador
La impresora «KonicaMinolta» necesita el paquete «kmfilter», pero éste no está instalado. Por favor, instálelo antes de usar esta impresora.

"The printer KonicaMinolta" needs the package "kmfilter" but it's not installed. Install it before using this printer.

Any Idea?
Help please.

---

### Post by pppetter on 2009-12-18
Hi there!

I have exactly the same problem! everything works fine, the system finds the printer and everything, but says that it's missing kmfilter. I also saw a line "cups-filter-system" or something similar.

I telephoned konica support here in sweden, but the guy had no clue. Fact is that the swedes had version 1.7 of the driver(which he was looking at), while I downloaded v1.8 from the U.S site :P

If anyone has any clue about what this is, please post ANYTHING. I have been surching the web for an hour or more, and found nothing! 

And btw. I am actually installing the printer on an opensuse system, so this is most probably a non linux distribution specific problem ;)

---

### Post by huflueck on 2010-05-07
CUPS filters are scripts and must be placed inside the /usr/lib/cups/filter directory.

The one you need with CUPS for the Konica Minolta PPD files resides after a standard KMPU installation in:

  /usr/lib/kmpu/printutility.filter.cups

So you can 

  ln -s /usr/lib/kmpu/printutility.filter.cups /usr/lib/cups/filter/kmfilter

and printing should work after this...

---

### Post by paul_dc on 2010-09-27
hi! i have the same problem try with the ln but no luck.. something on the lines of can't read the filter..

---

