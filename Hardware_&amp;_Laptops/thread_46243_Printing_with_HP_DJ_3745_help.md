---
title: "Printing with HP DJ 3745 help"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Nolgthorn on 2005-07-03
I am having troubles getting my mother's printer operational under Hoary. The problem is that it will print a page, but, ignores the bottom margin printing directly to the bottom of the page.

She commonly uses Times New Roman font, which as far as I believe is True Type. She is doing a paper for the university so it has to look right. I have the latest version of CUPS installed, also hpijs and foomatic-db-hpijs the printer driver from HP and it's incorporation into CUPS.

Unfortunately although the printer model shows up on the HP website, it does not appear under the CUPS menu. I have resorted to using the HP DJ 3650 driver, and have the page size set correctly on all fronts as A4.

Has anyone been able to find a solution to some of these HP printer problems in Ubuntu?

---

### Post by Nolgthorn on 2005-07-04
Bump

---

### Post by David Haas on 2005-07-05
I see the the PPD file HP-DeskJet_3740-hpijs.ppd.gz is present at /usr/share/cups/model/foomatic-ppds/HP. Perhaps this would work better for your 3745 than the 3650 file?
David

---

### Post by dwerf on 2006-02-05
I'm trying to install the same printer. I indeed installed the 3740 driver for the 3745 printer, but anything that is supposed to be black, comes out red! It doesn't do that in Windows, so there is a driver problem.

Any suggestions?

---

