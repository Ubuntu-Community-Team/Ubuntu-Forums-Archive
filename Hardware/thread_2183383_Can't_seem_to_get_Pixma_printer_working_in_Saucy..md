---
title: "Can't seem to get Pixma printer working in Saucy."
date: 2013-10-24
forum: Hardware
---

### Post by bigbri1111 on 2013-10-24
I have a Canon Pixma ip7220, and I tried using the Michael Gruz repository, but it failed on Saucy.  I can't seem to find a binary either, I would be happy to just compile it myself...

---

### Post by aikishugyo on 2013-10-25
By all means, go ahead and download the latest CVS gutenprint and try that. The iP7200 is supported experimentally.

---

### Post by heir4c on 2013-11-03
[http://www.driverlook.com/canon-pixma-ip7220-wireless-printer-driver-linux-ubuntu-mint-mac-os-x/](http://www.driverlook.com/canon-pixma-ip7220-wireless-printer-driver-linux-ubuntu-mint-mac-os-x/)
Scroll a little bit down to: "iP7200 series IJ Printer Driver Ver. 3.80 for Linux (debian Packagearchive)"
Packages downloaden and unpacking them (rightclick on the package). 
Than in the folder: cnijfilter-ip7200series-3.80-1-deb you have a 3 folders. 
One is the 'packages' folder. Open it and than you see 4 .deb files. 2 for 32-bit and 2 for 64bit. 
Choose the right ones and install first the cnijfilter-common deb file and than the cnijfilter-ip7200series deb file.

(I downloaded the files and try it here out in 14.04 and they install without a problem.)

---

