---
title: "Brother HL-2280DW Printer/Scanner"
date: 2012-07-31
forum: Hardware
---

### Post by chunderbunny on 2012-07-31
This post is more for information than anything. I bought this printer/scanner and managed to get everything working in Ubuntu 12.04 fine. 

When you plug it in it is detected as a printer, in the print driver select dialogue there is no specific driver for this printer, however I used the following driver and everything seems to work (printing, duplex etc). 
```
Brother HL-2170W Foomatic/hpijs-pcl5e 
```
The print quality seems okay for such a cheap device. 

Getting the scanner to work was a little more involved. Ubuntu doesn't seem to come with any drivers for this scanner, the 'simple-scan' program does not detect the scanner at all. 

The driver is available on the Brother website [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan4"), I downloaded the 64-bit 'brscan4' .deb package. 

Double clicking on the .deb brings up the Ubuntu software centre, when you click 'install' you get a warning that the package is of poor quality (it's missing an 'installed size' I think) but you can safely click 'Ignore' and it will install just fine. 

When you start up 'simple-scan' the scanner will now be detected, however when you click on 'scan' you get a message saying that the simple-scan cannot connect to the scanner. I don't know how to fix this properly, but if you run simple-scan as root ('gksudo simple-scan' in the terminal) then it works. 

P.S.
If there are any devs reading then is it a bug that simple-scan needs to be run as root? And can the brother drivers be included by default? I couldn't find any license information on driver package.

---

### Post by kurt18947 on 2012-07-31
Well, it's sort of a bug I guess.  The fix is here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

There is also 2nd problem that I think only occurs on 64 bit operating systems:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

Brother has an installer script for printing which has worked very well for me.  It takes care of any 32 bit/64bit issues.   

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html)     #6

---

### Post by chunderbunny on 2012-08-01
Thanks, I'm not used to finding relevant documentation on vendor websites. 

How can we get Ubuntu to support Brother printers/scanners out of the box? Should I file a bug?

---

### Post by kurt18947 on 2012-08-01
> **chunderbunny said:**
> Thanks, I'm not used to finding relevant documentation on vendor websites. 

How can we get Ubuntu to support Brother printers/scanners out of the box? Should I file a bug?

I'm not sure but I'm sceptical.  Brother's linux drivers are not open source.  They're sorta like Oracle's Java.  No cost to install or use but still property of the company.  If they had a script to install their scanners like they have for their printers it'd sure help.

---

