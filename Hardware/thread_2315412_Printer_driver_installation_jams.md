---
title: "Printer driver installation jams"
date: 2016-02-28
forum: Hardware
---

### Post by brian106 on 2016-02-28
I just wanted to install a driver for my Epson XP-215 wifi printer in Ubuntu 15.10. I go through the process of adding a printer (the only one) and the system finds it and also finds a driver, starts the installation, asks for the authentication password, continues for a while and then stops - never to advance any further.
I have repeated this exercise several times and it always goes the same way. I even tried downloading the driver from the Epson site and the same thing happened. I have tried all the usual cleaning processes (apt-get -f install  etc.) but nothing has helped so far.
After several hours on this, I am at the end of my tether. Can anyone please come to my rescue?

---

### Post by kc1di on 2016-02-29
Hello Brian , 
Sorry your having some problems.  
I don't use Epson printers but [this page]("http://tutorialforlinux.com/2015/05/25/how-to-install-epson-xp-215-expression-home-printer-drivers-quick-start-scanning-on-ubuntu-15-04-vivid-gnulinux-easy-guide/")  may be of help.

---

### Post by brian106 on 2016-03-01
> **kc1di said:**
> Hello Brian , 
Sorry your having some problems.  
I don't use Epson printers but [this page]("http://tutorialforlinux.com/2015/05/25/how-to-install-epson-xp-215-expression-home-printer-drivers-quick-start-scanning-on-ubuntu-15-04-vivid-gnulinux-easy-guide/")  may be of help.

Many thanks for your suggestion. I have made progress as a result but we're not quite there yet. On the Epson drivers download site, there is only one download package for Linux. When downloaded and opened, there is an enormous list of devices, including the XP-215. It also says that you have to first download 'one' of the files from a sub-list. I chose 'epson-printer-utility_1.0.0-1lsb3.2_i386(1).deb' as it is an Intel Atom powered mini laptop. That seems fine because it appears in the downloads folder. However, I'm not sure what to do after that because it is clearly not yet configured to communicate with the printer. If I try to 'Add' the printer, the correct printer and ip address is found but, when a long list of drivers opens there is nothing that in any way relates to the XP-215 printer.

---

### Post by brian106 on 2016-03-01
Panic over! Not quite sure how I managed it but, instead of selecting the detected reference to 'XP-215 217 (192.168.1.8)', I entered the plain url in the search box and it found and installed a driver. It then asked me if I wanted to print a test page, which I did, successfully. On the printout, the driver is shown as 'EPSON.PPD'.

---

### Post by kc1di on 2016-03-02
Glad it's working for you :)

---

