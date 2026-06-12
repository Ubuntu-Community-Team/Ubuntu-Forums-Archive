---
title: "Brother MFC-L2700DW driver problem"
date: 2018-05-15
forum: Hardware
---

### Post by cackerso on 2018-05-15
[INDENT] 							I have a Brother MFC-L2700DW printer/scan etc.
When I installed Kub 18.04 it detected and installed a driver.
The driver PPD seems to be in /etc/cups and the connection is given as  "ipp://BRN30055CF69ECC.local:631/ipp/print"
in the configure screen for system settings, printer.
It takes forever to print a page and the scanner doesn't work. 

In Kubuntu 16.04 I installed a driver from Brother in a Konsole that seems to work a lot better and it also
had a driver for the scanner included in the package. 

I ran the driver install like I did in 16.04,  but how do I get  18.04 to use this driver downloaded from the Brother site rather than  the one it has already installed?
I tried just running the Brother linux driver install but I didn't work.
[/INDENT]

---

### Post by kurt18947 on 2018-05-17
I haven't used Kubuntu in a long time so I'm not familiar with it. Have you perused 

[http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)

I haven't done the "before the installation" since maybe 2012.  Do pay attention to the FAQs. I had a problem with my scanner being recognized, the solution was in the FAQ. I've had very good luck with Brother's installer but I'm sure that's a YMMV situation. My experience with the "driverless install" is that the printer works for the most part, the scanner did not. I disabled the automatic install and installed Brother's driver so the scanner works. There is a Brother installer glitch that installs files for both the printer & scanner in in the wrong place.  The fix is in the FAQs.

---

