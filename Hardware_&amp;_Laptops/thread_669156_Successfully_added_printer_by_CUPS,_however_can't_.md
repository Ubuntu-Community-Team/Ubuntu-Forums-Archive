---
title: "Successfully added printer by CUPS, however can't use it from evince or firefox"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by jutirain on 2008-01-16
Hi all,

I've successfully added a printer by CUPS via [http://localhost:631](http://localhost:631).

I can print a test page through the web interface that CUPS provide, however, when I try to print some pdf documents, Evince can't found the printers just added, then crashed...

Firefox has similar problem, if I use File -> Print in Firefox, it can only find postscript printer.

Any suggestion?
Thanks a lot!

---

### Post by murmel on 2008-01-16
I've attached my configuration. Try it out. :)

---

### Post by c0met on 2008-01-16
I was just wondering if you had set your installed printer as the default one? It might be that Firefox and Evince don't see it as default.

---

### Post by murmel on 2008-01-16
Hehe, my bad. System -> Administration -> Printers (or w/e) and press "Use as default printer" or something like that.. Will change it for FF to ! :)

---

### Post by jutirain on 2008-01-16
I've already set the default printer through web interface of CUPS, however, Evince & Firefox just can't get it.

I've tried to use System -> Administratnion -> Printing but the system response:
The CUPS server could not be contacted.

I'm using Ubuntu 7.04 on VAIO SZ laptop, connect to the printer by wireless network.

Any other idea? :(

---

### Post by c0met on 2008-01-16
What do you have listed under [COLOR="DarkRed"]**System >> Preferences >> Default Printer**[/COLOR]?

---

### Post by jutirain on 2008-01-17
The problem was solved. :)

I've once set cups server in /etc/cups/client.conf, after delete the server setting, I can set up default printer in Administration -> Printing.

Thanks a lot.

---

