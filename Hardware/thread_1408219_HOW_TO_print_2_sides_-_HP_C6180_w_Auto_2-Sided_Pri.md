---
title: "HOW TO print 2 sides - HP C6180 w/ Auto 2-Sided Printing Accessory"
date: 2010-02-16
forum: Hardware
---

### Post by FredVanH on 2010-02-16
Before starting this, I had had to download and install hplip-3.9.12 from [http://hplipopensource.com](http://hplipopensource.com) so that the fax feature of this all-in-one could be installed.
Even though I had an HP Automatic Two-Sided Printer Accessory installed on the back of the machine (it grabs each sheet after the first side and flips it over), my Ctrl-P print dialog in Writer did not have 2-sided as an option.  What got it to work was setting the properties defaults for all print jobs:
1.   System | Administration | Printing.
2.  Double click the Photosmart_C6100 icon.
3.  In the resulting Printer Properties, etc. dialog, click 'Installable Options', Check the "Duplexer Installed" checkbox and click the Apply button.
4.  In the same Printer Properties, etc. dialog, click ""Printer Options" and set the "Double-sided printing" dropdown list to "Long edge (standard)" and click the Apply button. 
Note:  The "Short edge (flip)" option will also enable printing on 2 sides of the paper;  but will print the back sides "upside down", maybe for a (physical) clipboard where you flip up the bottom to read the back.
5.  Leave the dialog by clicking the Cancel button (only after you Apply instructions 3 & 4).

I hope this helps someone.  It sure had me stymied.  I searched and all I could find was an unsolved question.  Thanks to a fellow member for finding hplip.

---

