---
title: "Remove Printer Grayed out"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by Yotto on 2005-06-02
I added a printer to my system, and inadvertantly chose the wrong driver so it didn't print. I have since added a new printer with the correct driver, and am fine there, but I can't remove the old printer, as the "remove" option is grayed out. I also can't delete it with the delete key.  It's likely not a big deal, but I'd like to not have the broken printer installed any more.

How would I get rid of this?

---

### Post by David Haas on 2005-06-06
Once one selects the PPD file for a printer, an unzipped copy is placed in /etc/cups/ppd. If your former printer is still listed there, you could delete it. However, I don't know whether this would remove the printer icon from the print manager GUI. If not, then another forum member would probably know how to do this.
David

---

### Post by damormino on 2007-08-20
In Ubuntu 7.04 (Fiesty):
[LIST=1]
[*]From the System menu, select Administration > Printing
[*]Select the printer (single-click).
[*]From the Edit menu, select Become Administrator.
[*]Right-click the printer, and select Remove.
[/LIST]

---

