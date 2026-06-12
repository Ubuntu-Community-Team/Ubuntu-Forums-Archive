---
title: "Mystery regarding PDF printing on HP Laserjet 2100 TN"
date: 2009-11-04
forum: Hardware
---

### Post by stardustdk on 2009-11-04
Hey all.

I have just installed a Ubuntu 9.10 at a frinds PC.

He has a HP LaserJet 2100TN printer.

A very strange problem occur:

Printing html, OpenOffice documents and all other stuf **but** PDF files works like a charm.

PDF files??? :-?

Printing 1 page: 3 minutes
Printing 2 pages: 6 minutes (1 per 3 minutes)
Printing 3 pages: 9 minutes (1 per 3 minutes)

/Me confused! 

Any ideas?

Stardustdk

BTW: The problem was identical on Ubuntu 8.04 LTS.

---

### Post by ileader on 2010-05-03
I had a similar problem when I upgraded to Ubuntu from 8 -> 9 -> 10.04, and started using printing for the first time with a Laserjet 2100 TN. 

Test pages & Open Office was quick, but FF, Chrome & PDFs were slow (of the order of minutes to print)

I solved the problem by changing the printer driver to "HP LaserJet 2100 - CUPS+Gutenprint v5.2.5" at which point everything started printing at a normal speed (seconds).

---

### Post by finito on 2010-05-03
talk about reviving old threads.

Set spooling to none.

Print directly from computer.

Spooling takes for ever for some reason.

---

### Post by cmcanulty on 2010-05-10
Am having same choke on pdf printing at our library with 5 Ubuntu machines. Ours is a HP LaserJet 2100M and prints fine except pdfs take forever, then clients keep hitting print or give up and leave. Very annoying.This is on 9.10 and 10.04.Can you please explain how to turn off print spooling, I can't find that on a search.

---

### Post by jmadgin on 2010-05-26
Though I have an HP 2500n I had exactly the same problem, huge spooling times. Up to 20 minutes. The fix for me was to open the printer properties and change the printer driver to the Gutenprint one. Instead of 20 minutes for pictures and pdfs it only takes 5-10 seconds. Hope this helps!

---

### Post by cmcanulty on 2010-05-26
Thanks will try that. Also we bought a new printer as the network card in old one had gone bad. Have to set it up tomorrow so wish me luck getting mac. windows, and Ubuntu to print well.

---

### Post by magnus07 on 2011-10-11
Changing the printer driver to the Gutenprint did the job for me.
Great simple solution.:popcorn:

---

### Post by nothingspecial on 2011-10-11
Glad it worked :D

But please don't bump old threads to the top.

Closed.

---

