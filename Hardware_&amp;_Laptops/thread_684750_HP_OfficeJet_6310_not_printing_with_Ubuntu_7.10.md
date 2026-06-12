---
title: "HP OfficeJet 6310 not printing with Ubuntu 7.10"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by holmestp on 2008-02-01
Just loaded on 7.10 to update a fairly new Dell Linux box.  Now cannot get the printer to work, which worked fine with the previous version of Ubuntu that came on the Dell. (printer is also new, had it about a month).   Recognizes the printer when I plug it in, finds the driver (HP Officejet 6300 Foomatic/hpijs), but no reaction to print jobs.  They are in the print que, but just sit there, and then change to "stopped".  Tried turning on and off printer and computer, unplugging printer, different USB port, removing the printer and recognizing it again.  No luck.  Printer works - I can copy and fax with it. Thanks.

---

### Post by oldsoundguy on 2008-02-01
system> administration> printing> and make sure the printer is set up there.  I have a 6110x that works fine.

---

### Post by holmestp on 2008-02-01
Seems to be set up correctly.  I seem to having a similar problem to many others, after upgrading to 7.10, printer function seems to be affected.  trying to follow discussion on other printer problems.

---

### Post by holmestp on 2008-02-08
solution found: scrolled thru drivers trying each one, finally found that drivers for other printers will work if they have:  "cups+Gutenprint" in their name.  so insteady of HP 6310 driver, I used HP 7110 cups+Gutenprint.  None of the other "recommended" drivers would work.

---

### Post by Richard723 on 2008-02-17
> **holmestp said:**
> Seems to be set up correctly.  I seem to having a similar problem to many others, after upgrading to 7.10, printer function seems to be affected.  trying to follow discussion on other printer problems.

I just spent 3 hours looking as to why my HP6310 will not print. Double click the printer que in the bottom right corner. Then click on the printer menu. Uncheck paused printing. I feel like a rookie, hope all you guys not printing do too haha! I never remembered clicking on pause either. Restart and restore did not unchecl mine. I had to do it myself

---

