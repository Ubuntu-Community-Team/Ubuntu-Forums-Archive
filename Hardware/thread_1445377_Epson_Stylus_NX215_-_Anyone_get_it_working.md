---
title: "Epson Stylus NX215 - Anyone get it working?"
date: 2010-04-02
forum: Hardware
---

### Post by KevinLangman on 2010-04-02
Hi

I just got a Epson Stylus NX215 printer/scanner. 

Using Unbuntu 9.10 64bit.

The default CUPS+Gutenprint v5.2.4 does not have support for this printer but the new Gutenprint v5.2.5 claims to have added support for the NX215. So I downloaded the source installed the required development packages then built and installed the new Gutenprint (configure, gmake, gmake install). That all went well but when I try and print it still just spits out paper with nothing or small amounts of garbage on the page. The OS does detect the printer and automatically select the NX215 driver after the Gutenprint v5.2.5 install. 

Anyone had any success with the NX215 or can spot any process I missed to get the new Gutenprint installed correctly?

Any suggestions would be much appreciated.

---

### Post by anglican on 2010-04-02
> **KevinLangman said:**
> Hi

I just got a Epson Stylus NX215 printer/scanner. 

Using Unbuntu 9.10 64bit.

The default CUPS+Gutenprint v5.2.4 does not have support for this printer but the new Gutenprint v5.2.5 claims to have added support for the NX215. So I downloaded the source installed the required development packages then built and installed the new Gutenprint (configure, gmake, gmake install). That all went well but when I try and print it still just spits out paper with nothing or small amounts of garbage on the page. The OS does detect the printer and automatically select the NX215 driver after the Gutenprint v5.2.5 install. 

Anyone had any success with the NX215 or can spot any process I missed to get the new Gutenprint installed correctly?

Any suggestions would be much appreciated.

Go to:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Epson support for linux is, in my experience, excellent. I don't have this model, but it would appear to be fully supported for both printing and scanning.

H

---

### Post by KevinLangman on 2010-04-04
I should have just followed the old thread's suggestions in the first place.

[http://ubuntuforums.org/showthread.php?t=1353566](http://ubuntuforums.org/showthread.php?t=1353566)

I followed these instructions:

[http://avasys.jp/eng/linux_driver/faq/id000608.php](http://avasys.jp/eng/linux_driver/faq/id000608.php)

The directions are a little stale (8.10 using pipelite 1.3.0) but the process does work even on 9.10-AMD64 using pipelite 1.4.0.

---

