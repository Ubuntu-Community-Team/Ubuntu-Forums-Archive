---
title: "Brother MFC-7362N can't scan with gscan2pdf"
date: 2014-07-31
forum: Hardware
---

### Post by psyclone on 2014-07-31
Hi,
I'm getting the following result when running gscan2pdf

"Error opening device: Invalid argument"

I've installed the driver, and gscan2pdf can see the printer. 

e1-desktop@e1desktop:~$ dpkg -l | grep -i brother
ii  brother-cups-wrapper-common                           1.0.0-10-0ubuntu6                                   amd64        Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                            1.2.1-0ubuntu4                                      amd64        Cups Wrapper drivers for extra brother printers
ii  brother-cups-wrapper-laser                            2.0.1-2-0ubuntu6                                    amd64        Cups Wrapper drivers for laser brother printers
ii  brother-cups-wrapper-laser1                           1.0.2-1-0ubuntu8                                    amd64        Cups Wrapper drivers for laser1 brother printers
ii  brother-cups-wrapper-mfc9420cn                        1.0.0-1-0ubuntu6                                    amd64        Cups Wrapper drivers for mfc9420cn brother printers
ii  brother-lpr-drivers-common                            1.0.0-4-0ubuntu3                                    amd64        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                             1.2.0-2-0ubuntu5                                    amd64        LPR drivers for extra brother printers
ii  brother-lpr-drivers-laser                             2.0.1-3-0ubuntu5                                    amd64        LPR drivers for laser brother printers
ii  brother-lpr-drivers-laser1                            1.0.0-3-0ubuntu6                                    amd64        LPR drivers for laser1 brother printers
ii  brother-lpr-drivers-mfc9420cn                         1.0.0-3-0ubuntu4                                    amd64        LPR driver for mfc9420cn brother printer
ii  brother-udev-rule-type1                               1.0.0-1                                             all          Brother udev rule type 1
ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                               0.4.2-3                                             amd64        Brother Scanner Driver
ii  cupswrappermfc7362n                                   2.0.4-2                                             i386         Brother MFC7362N CUPS wrapper driver
ii  mfc7362nlpr                                           2.1.0-1                                             i386         Brother MFC-7362N LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers

help!

---

### Post by TheFu on 2014-07-31
It has been a few years since I setup scanning on my Brother all-in-one (different model) - the only trick that I recall was having to place my userid into the appropriate group on the machine where the scanning was happening.  A quick look at my groups on that system doesn't show anything now (scanner isn't on), but that userid is part of the plugdev and lp groups.

BTW, I use gscan2pdf too.  Thought the error I saw was related to permissions, so don't think this is the same as yours, but ... perhaps?

---

### Post by JLUbunt on 2014-08-11
Hello
I use gscan2pdf on 12.04 LTS works perfectly. I put 14.04 on another computer as I'm planning to upgrade. gscan2pdf cannot find the scanner. I tried Simple scan works with 12.04 but same problem with 14.04. I looked at scan2pdf on the software centre for 14.04. 3 reviews indicate the scan2pdf stops working after upgrades from 12.04. 
Not sure if this helps. I'd like to upgrade but need to use a scanner.

---

### Post by JLUbunt on 2014-08-11
Just tried to print from the other computer to my Brother MFC-9120CN from the other computer with 14.04. 14.04 found the printer to install the Driver, but cannot find the printer to print. I had this problem a long time ago found a way to reinstall the drive. I've found the IP address of the printer.  If anyone can let me know where to find to type it into 14.04 as a static IP address I'll have a go.  Thanks.

---

### Post by JLUbunt on 2014-08-11
Managed to copy the info from 12.04 and typed it into the 14.04 into the "Device URI". I found the URI from the printer display and typed in socket://xx.x.x.xx:xxxx. !4.04 finds and prints from 14.04. scan2pdf and simple scan do not find the device. I don't have the skill to do much else.

---

