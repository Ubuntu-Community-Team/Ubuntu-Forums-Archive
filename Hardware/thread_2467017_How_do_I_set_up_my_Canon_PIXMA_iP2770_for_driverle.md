---
title: "How do I set up my Canon PIXMA iP2770 for driverless printing?"
date: 2021-09-13
forum: Hardware
---

### Post by ardouronerous on 2021-09-13
When I switched to Ubuntu 12.04 from Windows back in 2012, the Gutterprint driver for my Canon printer just sucked, it was feature incomplete, it lacked printing in draft mode, so I downloaded and installed the official Canon Linux drivers from their website and I've been using the same drivers since 12.04 to 18.04, however, when I upgraded to 20.04, the drivers refused to install due to compatibility issues and the Gutterprint drivers still sucked, so I was forced to download the Canon drivers for Windows and run my printer via WinXP on Virtualbox to print. I even tried to install the Windows drivers on WINE, it didn't work.

I was told to give driverless printing a try, but I need a good user friendly guide on this topic though, thanks.

---

### Post by brian_p on 2021-09-13
[https://wiki.debian.org/CUPSDriverlessPrinting]("https://wiki.debian.org/CUPSDriverlessPrinting")

---

### Post by linuux on 2021-09-17
> **ardouronerous said:**
> When I switched to Ubuntu 12.04 from Windows back in 2012, the Gutterprint driver for my Canon printer just sucked, it was feature incomplete, it lacked printing in draft mode, so I downloaded and installed the official Canon Linux drivers from their website and I've been using the same drivers since 12.04 to 18.04, however, when I upgraded to 20.04, **the drivers refused to install due to compatibility issues** and the Gutterprint drivers still sucked, so I was forced to download the Canon drivers for Windows and run my printer via WinXP on Virtualbox to print. I even tried to install the Windows drivers on WINE, it didn't work.

I was told to give driverless printing a try, but I need a good user friendly guide on this topic though, thanks.What does that mean?

You tried to re-install the drivers but they didn't work?  When you upgraded the distro version, what messages were returned for the Canon drivers?

I posted how to install drivers for Canon (Pixma) printers before.  I am curious if you (and anyone else who uses Canon printers) tried the steps.  Also, you could use it as a guide to see if the same drivers/software packages are installed.  They probably are needed in order for the printer to work, both printer features and the scanner (if a multifunction printer).  

[https://www.ubuntupit.com/how-to-install-canon-printer-driver-in-ubuntu-linux/](https://www.ubuntupit.com/how-to-install-canon-printer-driver-in-ubuntu-linux/)

[https://itsubuntu.com/how-to-install-canon-printer-driver-in-ubuntu-20-04/](https://itsubuntu.com/how-to-install-canon-printer-driver-in-ubuntu-20-04/)

[https://project-anniemei.com/canon-pixma-ip2770-ip2772-driver/](https://project-anniemei.com/canon-pixma-ip2770-ip2772-driver/)

According to the last link above, the 'crucial' software package is named, something like, "cnijfilter-ip2700series-X" (where 'X' is the version number of the driver).  

I would install 'Synaptic Package Manager' and see if there's any files/packages with the name 'cnijfilter-' in them and look for the 2700 series one.   If that doesn't work, you can try the PPA method.   If neither work and you receive 'incompatible' type of output or 'drivers not found' messages in return, then it's probable that Canon is not providing drivers anymore.

---

