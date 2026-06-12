---
title: "EPSON Stylus TX117 scanner"
date: 2011-07-04
forum: Hardware
---

### Post by gilk on 2011-07-04
(I've seen the[ post already posted]("http://ubuntuforums.org/showthread.php?t=1546703&highlight=EPSON+Stylus+TX117+scanner") - this is not the same...)
configuration - Ubuntu 11.04
scanner/printer Epson TX117
printer works fine!
scanner works(!) with LibreOffice...!

Does not work wit any other software...?!? 

tried: Xscan, Simple Scan, gscan2pdf - they all show "fail to scan  No scanner available".
And still the open office document does see the scanner. that means the driver is OK (?)

Any idea/advise...?

Thanks
Gil

---

### Post by beew on 2011-07-04
Did you install the scanner driver?

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

---

### Post by gilk on 2011-07-04
The computer recognized the printer/scanner, and automatically installed the drivers.
As I mentioned - the scanner works well but only with OpenOffice...

---

### Post by nomko on 2011-07-04
According to this site: [http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON) the Epson Stylus TX 110 series is supported by sane. Where did you get the drivers? Or was the scanner recognized out-of-the-box?

---

### Post by beew on 2011-07-04
> **gilk said:**
> The computer recognized the printer/scanner, and automatically installed the drivers.
As I mentioned - the scanner works well but only with OpenOffice...

I don't know about  your model. I have a Nx415. In Natty it recognised and pick up the driver automatically, both printer and scanner work.

But in Maverick I have to install the drivers manually from the site I linked to above. Now this is the funny thing. If I just install the same driver I installed in Natty (the same one work for Maverick) then only the printer works. In Maverick I have to install those ADDITIONAL driver packages for scanner to work so maybe they are a bit different. No harm in trying them, if they don't work or interfere with the existing driver just uninstall those .debs.

I am not sure what do you mean by the scanner works only with OpenoOffice. You scan by putting something in the scanner and simple scan will output in jpg and then you can save as pdf. I am not sure how OpenOffice comes in.

---

### Post by gilk on 2011-07-04
> **beew said:**
> I don't know about  your model. I have a Nx415. In Natty it recognised and pick up the driver automatically, both printer and scanner work.
...
I am not sure what do you mean by the scanner works only with OpenoOffice. You scan by putting something in the scanner and simple scan will output in jpg and then you can save as pdf. I am not sure how OpenOffice comes in.

Well I mean just as it worked for you on Natty, drivers were installed by Ubuntu.
Regarding openoffice, if I use OO and go to insert/picture/scan/request - the scannere works, and scans the picture into a document...

---

### Post by cetmey on 2012-08-22
I would suggest you to try the following steps:
 
Step 1: Run the Printer troubleshooter and then test.
 
Step 2: Make sure the printer is set as default.
 
1. On the Ubuntu taskbar, click on the start button, click Control Panel, and then click Printers. The Printers folder opens.
2. Look for a green check mark next to your Printer This check mark indicates which product is the default printer Ubuntu.
 
Also make sure the printer is not paused or offline.
1.    On the print queue menu bar, click Printer, and then look for the Pause Printing and Use Printer Offline items in the menu.
2.    Make sure that there is no check mark next to either item. If a check mark displays next to either item, click to clear it.
 
If the issue persists,

Step 3: Next, try updating the printer driver on your computer. Printer problems sometimes stem from out-of-date driver software, and can be solved by installing—or reinstalling—the latest driver.
Hence, I would also suggest you to remove the hardware, uninstall the software and drivers, then reboot the system and reinstall the latest drivers for the printer from the manufacturer’s site and check.

[EPSON Stylus TX117 Driver]("http://www.driversepson.com/epson-tx117-driver/")

---

