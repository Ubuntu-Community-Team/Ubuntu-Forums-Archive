---
title: "Problem scanning with HP all in one officejet pro 8600 on 10.04"
date: 2013-10-02
forum: Hardware
---

### Post by okos on 2013-10-02
Hello all,

I spent an evening trying to figure out why my computer could no longer scan from my network printer. Well I solved that problem ;) and here is how I did it:

1. Xsane could not find the scanner.
2. I used wireshark to determine that the scanner was not looking in the right place. The MDNS was not doing the correct query.
Here is the query output:
```
_pdl-datastream._tcp.local: type PTR, class IN, "QM" question

```

The correct query should be:
```
HP843497A3933F.local: type A, class IN, "QM" question
```

3. I tried the hp-toolbox setup, but it also could not find the printer or the fax.

4. Through a process of elimination, I determined it was the hplip-3.13.2 driver that had automatically been updated through Ubuntu updates. 
5. I googled hplip and found a newer driver, hplip-3.13.9. I installed the driver and now everything works!!!
Here is the link: [http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

I hope this helps some of you.

Okos

---

