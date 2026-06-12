---
title: "Canon Pixma MG5350 all in one scanner"
date: 2013-12-22
forum: Hardware
---

### Post by robert48 on 2013-12-22
I have a Pixma MG5350 connected via wireless LAN and also by USB cable. It prints from a PC and iPad wonderfully using Ubuntu 13.10 32bit.

Neither Xsane nor Simple Scan can see the scanner part. I have downloaded a source driver from Canon, namely ScanGear MP version 1.8. I don't know how to compile the source and ideally link it to the Xsane interface.

Can you help me to get the scanner to work please?

Kind Regards
Bob

---

### Post by Frogs Hair on 2013-12-22
***Moved to Hardware ***

---

### Post by aikishugyo on 2013-12-23
SANE (the backend which Xsane tries to use) should support this scanner in 1.0.24 or in the git repository code (check the SANE CVS and release [1.0.24] supported-scanner webpages).

---

### Post by robert48 on 2014-01-04
Thanks for the response.

I have now found version 1.0.24 source, downloaded it and am ready to configure, make and install (I think!). Should I first delete the old version? Is it ok to just remove it using Ubuntu Software Centre or will it require 'purging'? If the later, how best do I do that please?

Regards
Bob

---

