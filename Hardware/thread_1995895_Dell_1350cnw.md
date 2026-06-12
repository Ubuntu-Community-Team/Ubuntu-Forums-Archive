---
title: "Dell 1350cnw"
date: 2012-06-03
forum: Hardware
---

### Post by Zymous on 2012-06-03
I have the Dell attached to my router. The Dell appears when searching for a network printer, but it doesn't work when I attempt to print to it.

There doesn't appear to be any official support for this printer, and very little when searching for it on the internet, but it is possible to get this printer working, thanks to information in this thread [http://www.linuxquestions.org/questions/linux-hardware-18/dell-printer-1350cnw-925655/](http://www.linuxquestions.org/questions/linux-hardware-18/dell-printer-1350cnw-925655/)

The printer is substantially the same as the Phaser 6000, for which there is Linux support [http://www.support.xerox.com/support/phaser-6000/downloads/engb.html?operatingSystem=linux&fileLanguage=en_GB](http://www.support.xerox.com/support/phaser-6000/downloads/engb.html?operatingSystem=linux&fileLanguage=en_GB)

Download the deb file and install it.

Make sure you are authenticated as user in the lpadmin group (see the section Web Interface section on this page Web [https://help.ubuntu.com/11.04/serverguide/cups.html](https://help.ubuntu.com/11.04/serverguide/cups.html) ) 

Go to [http://localhost:631/printers/](http://localhost:631/printers/) and click on the Manage Printers button. Click on Dell_Dell_1350cnw_Color_Printer and then choose Modify Printer from the drop down list that is on the Administration button. Click through until you are on the page that allows you select Xerox as the manufacturer and then select the Xerox 6000B v1.0

Simple printing to the Dell should then work.

-- 
Zym

---

