---
title: "How do I install a Canon S900 printer"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by kpictjl on 2006-10-15
How do I install a Canon S900 printer in Dapper Drake?   When I do the actions shown below the Canon list doesn't have S900.  Google's and forum searches turn up nothing.  Any help is appreciated.  Thank you.

```
 
How to add a printer

    * Go to System -> Administration -> Printing.
    * Choose "Add printer". 

A "Add printer wizard" should start and tell you what to do.

```

---

### Post by clownius on 2006-10-15
Try looking on the canon europe website for linux drivers.  I just went through this with an ip4200 so have a look at that thread to it may provide u with some assistance...or more confusion

---

### Post by kpictjl on 2006-10-15
just looked on canon usa and europe...no luck.

---

### Post by kpictjl on 2006-10-17
I made it work using [www.turboprint.de/english.html](www.turboprint.de/english.html).  I had to install the printer, delete it and then re-add it.  I'm not sure why.

There, I've answered my own question...not sure why I did that?

Is there a groovy internet term for the self answer?

---

### Post by kpictjl on 2006-12-17
turboprint worked, sort of, it printed a turboprint logo on each of my pages.  I would have to pay to avoid the logo.

A little more digging revealed this...
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S900](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S900)

Basically us the s800 driver that comes with the live cd and then change the resolution via the printer properties to 1200x1200.

This thread also helped me print from my Windows XP PC.
[http://www.ubuntuforums.org/showthread.php?t=268245](http://www.ubuntuforums.org/showthread.php?t=268245)

Thanks.

---

