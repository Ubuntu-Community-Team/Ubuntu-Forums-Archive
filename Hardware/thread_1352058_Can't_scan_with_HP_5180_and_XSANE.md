---
title: "Can't scan with HP 5180 and XSANE"
date: 2009-12-11
forum: Hardware
---

### Post by peterout on 2009-12-11
Just installed Ubuntu 9.10 and having tried many previous releases I can say that I was very impressed! I was very impressed when my HP printer/scanner which is networked was detected OK and printing is no problem. However my happy mood was dashed when I opened XSANE and was told no devices were found. The HP site says that 5100 devices should print and scan over a network with Ubuntu 9.10. Well, half right! Googling around seems to indicate that SANE does not in fact support the HP 5100 series for scanning. This is a real disappointment. Every time I install a Linux distro there is always something that drives me back to horrible (but it just works) Windows.
Any ideas to get my scanner functioning?

---

### Post by peterout on 2009-12-12
Well, no responses! So I followed google search to HP Linux site and decided to download the version of HPLIP that was there that was slightly newer than the one included with 9.10.
Used the dreaded  (to me anyway) terminal to install and despite a few worrying messages about things being missing it has solved the problem. So now I CAN scan. 
The final step was to run HPSETUP. Was this all that was missing from my initial install? Not expecting any answers as before, but someone might be interested I suppose.

---

### Post by Camilia on 2009-12-12
No devices found, means no connection for me. I doubled check the connections and got it to come up.

For printer look for hplip at system > administrative > synaptic package

---

