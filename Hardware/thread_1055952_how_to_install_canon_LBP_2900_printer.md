---
title: "how to install canon LBP 2900 printer"
date: 2009-01-31
forum: Hardware
---

### Post by hirohitosan on 2009-01-31
Hi there. 
I don't know how to install canon LBP 2900 printer.
I downloaded the latest driver from Canon web site and install
cndrvcups-common_1.80-1_i386.deb
cndrvcups-capt_1.80-1_i386.deb
installation was successful but I cannot find where the ppd file are?

I tried to install the new driver through printer wizard but I cannot find where the ppd file is located

I tried also to ```
 sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd-v ccp:/var/ccpd/fifo0 -E
lpadmin: Unable to copy PPD file!

```

any help is appreciated

---

### Post by rockstarsavin on 2010-08-09
try this tutorial [http://www.design-salcon.com/?articles/canon-lbp-2900-installation-on-ubuntu-10-04.html](http://www.design-salcon.com/?articles/canon-lbp-2900-installation-on-ubuntu-10-04.html)

---

