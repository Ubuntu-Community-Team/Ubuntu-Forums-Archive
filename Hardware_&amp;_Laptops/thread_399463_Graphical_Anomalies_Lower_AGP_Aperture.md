---
title: "Graphical Anomalies: Lower AGP Aperture"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by ambien on 2007-04-02
I have been having issues with my Radeon X1300 graphics card, when I stumbled on this article at 

[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

that describes my problem EXACTLY! 

"
This was experienced with an ATI Radeon X1600 Pro 512mb:

After following instructions for both Method 1 and Method 2, whenever the Composite Extension is disabled, the display would be almost unusable, but the fglrxinfo command would display the correct information. If the Composite Extension is re-enabled the display would be usable, but fglrxinfo would report using mesa drivers.

To resolve the problem it maybe needed to lower the AGP Aperture setting in my BIOS to 128mb (or lower worked too). The AGP Aperture was initially set to 256mb. After setting the AGP Aperture to 128mb, everything worked perfectly; the Composite Extension is disabled, fglrxinfo reports the correct drivers, and direct rendering is enabled. Some systems may require setting the AGP Aperture to the highest setting (256mb or 512mb). 
"

My question is how do I configure my AGP in BIOS like the article says? Has anybody else had/fixed this problem? 

Thanks in advance!

---

