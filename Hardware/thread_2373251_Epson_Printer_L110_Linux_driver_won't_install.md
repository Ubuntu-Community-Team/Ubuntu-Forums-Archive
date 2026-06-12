---
title: "Epson Printer L110 Linux driver won't install"
date: 2017-10-04
forum: Hardware
---

### Post by Patrik_Samju on 2017-10-04
I have this link [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822) from the previous thread of "Installing L110 printer driver for Ubuntu 10 & 12" [https://ubuntuforums.org/showthread.php?t=2069065](https://ubuntuforums.org/showthread.php?t=2069065). 

When I clicked the install button, nothings happen. My Ubuntu is 16.04.

---

### Post by howefield on 2017-10-04
Which deb package did you download ?

Might be easier to use the terminal to install the package, run the following command.. (assuming the package is in your Downloads folder and is the 64 bit package)

```
sudo apt install ~/Downloads/epson-inkjet-printer-201207w_1.0.0-1lsb3.2_amd64.deb
```

---

### Post by rbmorse on 2017-10-04
Yes, and make sure that you downloaded a 64-bit driver.  Some of the older ones were only available in 32-bit form, back in the day.

---

