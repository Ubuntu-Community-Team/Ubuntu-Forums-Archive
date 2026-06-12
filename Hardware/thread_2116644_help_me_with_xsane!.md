---
title: "help me with xsane!"
date: 2013-02-16
forum: Hardware
---

### Post by apsot on 2013-02-16
hello, 

i was using xsane with my lexmark x1170 just fine, until devil got in me on a dark and rainy afternoon and started asking for more. I thought i could scan a larger area with my scanner, so i went to "paper geometrie"  shown here: [http://www.xsane.org/doc/sane-xsane-setup-copy-doc.html](http://www.xsane.org/doc/sane-xsane-setup-copy-doc.html) 
and changed the width and height attributes

although i experimented with a lot of values the result is always the same: my scanner makes an abrupt sound as if it scans a very sort area, the result being a white scanned document. Unfortunately i didn't save the default width and height attributes. Do you have any idea where i could find them?

thanks in advance for your help,
apo 

p.s. i have also tried the values on the link to no avail
p.s2 simple scan is working fine though

---

### Post by apsot on 2013-02-20
to restore defaults 
```
mv .sane/xsane .sane/xsane.old
```
will do. it worked for me

---

