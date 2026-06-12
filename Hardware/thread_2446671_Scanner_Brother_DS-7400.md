---
title: "Scanner: Brother DS-7400"
date: 2020-07-04
forum: Hardware
---

### Post by webmanoffesto on 2020-07-04
Never mind, I got XSane to work with Gimp.
------------------------------------------------------------------

My question was:
I have a new Brother DS-7400 mobile (small) scanner. I downloaded and installed the drivers. In Simple Scan the Scan Source shows as Brother DS-740D. But when I click on scan I get "Failed to Scan: Error Communicating with Scanner". 

How do I get this working? 

Ubuntu 16.04 LTS, 64 Bit

[FONT=courier new]$ dpkg -l | grep -i Brother[/FONT]
[FONT=courier new]ii  brscan-skey                                   0.2.4-1                                         amd64        Brother Linux scanner S-KEY tool[/FONT]
[FONT=courier new]ii  brscan4                                       0.4.7-1                                         amd64        Brother Scanner Driver[/FONT]
[FONT=courier new]ii  brscan5                                       1.2.2-0                                         amd64        Brother Scanner Driver brscan5[/FONT]
[FONT=courier new]ii  mfcj880dwcupswrapper:i386                     1.0.0-0                                         i386         Brother Inkjet printer CUPS Driver [/FONT]
[FONT=courier new]ii  mfcj880dwlpr:i386                             1.0.0-0                                         i386         Brother inkjet lpr printer Driver [/FONT]
[FONT=courier new]ii  printer-driver-brlaser                        3-5~ubuntu1                                     amd64        printer driver for (some) Brother laser printers[/FONT]
[FONT=courier new]ii  printer-driver-ptouch                         1.4-1                                           amd64        printer driver Brother P-touch label printers[/FONT]

---

### Post by pqwoerituytrueiwoq on 2020-07-05
It could be a permissions error, try running scanimage as root
[FONT=courier new]scanimage -L[/FONT]
This should list your scanner, if it does not try it as root (sudo)
also try to scan a document using scanimage

---

