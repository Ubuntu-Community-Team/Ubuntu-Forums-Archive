---
title: "Is the printing queue system in Ubuntu 18.04 slow?"
date: 2018-10-12
forum: Hardware
---

### Post by Semn on 2018-10-12
Hi, I have installed 1804 after usiung 1604. While 1604 printed a PDF through the network via the regular "search printer" function on the network, 1804 uses about 4 minutes to print one page of PDF to the printer. The printer, an OKI MC562 worked perfectly in 1604 and also in lousy Win10, but 1804 however, requires about 1 hour to print 20 pages. How is that possible? Something must be wrong?

---

### Post by Autodave on 2018-10-12
Did you upgrade from 16.04 to 18.04 or did you do a clean install?

---

### Post by Semn on 2018-10-13
I upgraded. Is this caused by the CUBS system? Can I get around this somehow?

---

### Post by Autodave on 2018-10-13
I have no idea what CUBS is.....do you mean CUPS?  

Personally, I have rarely had any luck in upgrading. I have always found it quicker and easier to backup everything that I need to keep and then do a clean install.

---

### Post by him610 on 2018-10-13
Sometimes upgrading breaks the configurations that were stable in the previous release. You could completely delete the previously installed OKI MC562 driver, but not the deb file. Reboot, then reinstall the MC562 driver from the deb file, or if you do not have it on hand you will need to download it again from the Oki support webpage. This may not work, but it is worth a try.

---

### Post by Semn on 2018-10-15
Thanks, will give it a try.
P:S: Yes, I Ment CUPS

---

### Post by Semn on 2018-10-15
Hmm I still get that CUPS error, either way I try

[IMG]http://www.fjordforsk.no/Untitled.jpg[/IMG]

---

