---
title: "canon lide 60 working with breezy"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by gse on 2006-01-05
I was able to access and use a canon lide 60 scanner with breezy. I had to install libsane1.0.17 from dapper.

Install instructions: [http://paste.ubuntuusers.de/1245.txt]("http://paste.ubuntuusers.de/1245.txt")

--
20060106 11:00 GMT+1: 
I forgot to mention that one has to add an appropriate entry in /etc/udev/rules.d/45-libsane.rules like in my etc/udev/rules.d/45-libsane.rules: [http://paste.ubuntuusers.de/1250.txt](http://paste.ubuntuusers.de/1250.txt).  First of all, one has to add there a RUN+ command for the old hotplug scripts one copied earlier.

In my above outline the end of /etc/sane.d/hotplug/libsane.db had been cut which in this case is not really bad, because the entry for the lide 60 was available. But you can get the full /etc/sane.d/hotplug/libsane.db from:
[http://paste.ubuntuusers.de/1249.txt]("http://paste.ubuntuusers.de/1249.txt").
--


I won't be much around here.

cheers
greg

---

### Post by bluetoad on 2006-04-07
There is more detail in this thread [http://www.ubuntuforums.org/showthread.php?p=898632#post898632](http://www.ubuntuforums.org/showthread.php?p=898632#post898632)

---

