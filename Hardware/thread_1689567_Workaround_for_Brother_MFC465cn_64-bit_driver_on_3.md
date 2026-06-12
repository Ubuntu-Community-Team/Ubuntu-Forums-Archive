---
title: "Workaround for Brother MFC465cn 64-bit driver on 32-bit OS"
date: 2011-02-17
forum: Hardware
---

### Post by TomSerato on 2011-02-17
I am new to Linux/Ubuntu and have recently installed the 32-bit version of Ubuntu 10.10, through Wubi, on a Toshiba Satellite A135. I went with the 32-bit version as my existing Windows install is also 32-bit.   I have a Brother MFC465cn and need to install drivers for it (just the print driver for now). However, the only print driver available on the Brother website for Debian/Ubuntu is a 64-bit driver. I went ahead and downloaded the two .deb files and was able to install them through Ubuntu Software Center. Ubuntu and OO Writer both recognize the printer, but when I try to print to it I get a status of &quot;Processing - Not Connected?&quot;. The printer is connected to a wireless router and I get the same status message whether my laptop is connecting to the router wirelessly or with  cable.  I realize that 64-bit drivers wouldn't normally work for a 32-bit OS, but I never received an error message when installing. Has anyone out there found a workaround for a similar setup?  Thanks

---

### Post by tgm4883 on 2011-02-17
> **TomSerato said:**
> I am new to Linux/Ubuntu and have recently installed the 32-bit version of Ubuntu 10.10, through Wubi, on a Toshiba Satellite A135. I went with the 32-bit version as my existing Windows install is also 32-bit.   I have a Brother MFC465cn and need to install drivers for it (just the print driver for now). However, the only print driver available on the Brother website for Debian/Ubuntu is a 64-bit driver. I went ahead and downloaded the two .deb files and was able to install them through Ubuntu Software Center. Ubuntu and OO Writer both recognize the printer, but when I try to print to it I get a status of &quot;Processing - Not Connected?&quot;. The printer is connected to a wireless router and I get the same status message whether my laptop is connecting to the router wirelessly or with  cable.  I realize that 64-bit drivers wouldn't normally work for a 32-bit OS, but I never received an error message when installing. Has anyone out there found a workaround for a similar setup?  Thanks

I have the mfc-5440cn so it might be slightly different.

Did you add the printer after installing the drivers? I ask, because you said it was connected via the network and when I installed my drivers it automatically set it up for USB.

---

### Post by tgm4883 on 2011-02-17
Also, there are 32-bit drivers for your printer here, although I don't see 64-bit ones

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-465CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-465CN)

---

### Post by TomSerato on 2011-02-17
> **tgm4883 said:**
> Also, there are 32-bit drivers for your printer here, although I don't see 64-bit ones

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-465CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-465CN)

 Those are exactly the files I downloaded. I think I got confused because when I first searched for drivers, Brother listed Debian/Ubuntu 64 bit or Ubuntu 8.04-9.04. Then when I actually decided to try downloading I got to the download page through a different set of prompts and just assumed that I was downloading the 64 bit versions.  I added the printer first through System - Admin - Printing - Find Network Printer. The system then tried to search for drivers but couldn't find any.

---

