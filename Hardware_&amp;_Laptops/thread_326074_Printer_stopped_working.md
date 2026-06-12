---
title: "Printer stopped working"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Ethos on 2006-12-27
Hello I had my hp officejet 4215 working fine in ubuntu, until recently i didnt need to print anything, but tonight I attempted to. My printer has dissapeared, so I went to system-admin-printing and when i click printers it says "the CUPS server could not be contacted" ..... HELP! :(   Thanks

---

### Post by dbbolton on 2006-12-27
what does gnome-cups-manager have to say ?

---

### Post by highneko on 2006-12-27
Sometimes I have problems and I noticed my printer's not turned on. Maybe this could have happened to you?

---

### Post by Ethos on 2006-12-27
** (gnome-printer-view:21773): WARNING **: IPP request failed with status 1280

** (gnome-printer-view:21773): WARNING **: IPP request failed with status 1280




Thats what I get from the gnome-cups-manager

---

### Post by Ethos on 2006-12-27
bump

---

### Post by Ethos on 2006-12-27
bump again...sorry i need my printer and i dont know what to do..

---

### Post by juseal on 2007-01-26
I followed this thread and it started working for me.
[http://ubuntuforums.org/showthread.php?t=258124&highlight=the+cups+server+could+contacted](http://ubuntuforums.org/showthread.php?t=258124&highlight=the+cups+server+could+contacted)

A condensed version is:

Remove cups

sudo apt-get remove cupsys cupsys-client

Purge cups

sudo apt-get remove --purge cupsys cupsys-client

Re-install cups

sudo apt-get install cupsys cupsys-client

I hope that helps

---

### Post by element on 2007-01-31
> **juseal said:**
> I followed this thread and it started working for me.
[http://ubuntuforums.org/showthread.php?t=258124&highlight=the+cups+server+could+contacted](http://ubuntuforums.org/showthread.php?t=258124&highlight=the+cups+server+could+contacted)

A condensed version is:

Remove cups

sudo apt-get remove cupsys cupsys-client

Purge cups

sudo apt-get remove --purge cupsys cupsys-client

Re-install cups

sudo apt-get install cupsys cupsys-client

I hope that helps

I had the same problem and that worked for me. Thanks!

---

