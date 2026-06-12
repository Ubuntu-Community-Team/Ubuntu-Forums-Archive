---
title: "HP P3005x Printer works in 7.04, but fails in any newer Ubuntu releases"
date: 2009-04-13
forum: Hardware
---

### Post by Mark20 on 2009-04-13
Hi all,

I dual boot Windows XP and Ubuntu 8.10 on my Desktop.  Printing from XP to a networked HP 3005X printer works flawlessly, but as soon as I try to print from Ubuntu 8.10 the printer crashes with an error message - 49.4c02...whatever that means.  I then tried earlier Ubuntu releases, and the same problem exists for 8.04, and 7.10, but in 7.04 printing works perfectly!  In all cases I attempted to print with the standard postscript driver, and I selected LPR/LPD.

I was wondering if anyone had any suggestions for fixing this.  I was going to try one of the following:

**_Option 1_**
Diff the 7.04 driver and the 8.10 driver and try to back out the changes.

**_Option 2_**
Set up some kind of print server on XP, so that I can keep XP running as a VMware guest and then access the shared printer from Ubuntu.  

Maybe someone more experienced with printing could suggest which method would be better, or another course of action.

Thanks,
Mark

---

### Post by fgysin on 2010-04-26
I go the same problem under Ubuntu 9.10.
I found out though that printing only fails when I use the Evince pdf reader to print pdfs. If I use the Adobe Acrobat reader printing worsk as it should. Must be something with the Ubuntu pdf drivers?

---

