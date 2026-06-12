---
title: "X.org start problems"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by Fed on 2005-08-06
Hi,
Im trying Ubuntu for the first time, and I decided to try the Live CD option since my main OS drive failed and is currently getting replaced. The problem Im having is that when I try to startup Ubuntu, X.org says that it failed to start. In the details, I can see that my graphics card should be supported, Radeon X800XT PCI-E, and then spews out the following lines:
ATI:  Candidate "Device" section "ATI Technologies Inc, Radeon X800 XT (R423)"
ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
No devices detected.

Fatal server error:
no screens found

Any ideas or help on this?
Thank you.

---

### Post by Fed on 2005-08-06
Well folks, my problem is solved. And it was solved by another thread in here, that I just hadnt dug up at the time of the post. There are really a lot of people with problems with x800 pci-e cards and all of them except that one that I found end without a solution. The solution however, is very simple, changing driver from "ati" to "radeon" in your xorg.conf. Hopefully this helps someone else out there.

 :grin:

---

