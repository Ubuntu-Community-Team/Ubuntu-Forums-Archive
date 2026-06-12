---
title: "EPSON AcuLaser CX11NF - It's possible?"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by mundano on 2006-04-07
Hi..

I have a lan with some 2 Windows PC, 2 Kubuntu machines and one EPSON AcuLaser CX11NF network printer/scaner/fax. 

The original epson CD has some app to install the printer in Windows and Mac computers, but none to Linux. I have configured the IP and the door that the printer is using, and have tried some drivers in the printer seccion of System Settings, but none worked. I also have tried generic drivers, raw printer, ps printer... But everytime i try to print it just show a message sayong "Printing.. Please Wait.." and the printer does nothing.

Can anyone give me some tips to solve this?


* sorry the bad english..

---

### Post by TheDom on 2006-04-25
Hi there.

I am running Ubuntu on two boxes which I use for my day-to-day work in the office. We have recently purchased one of these printers (ugh!) and I cannot print to it. I have tried the same steps as listed by the original poster, but with no success.

Has anyone got one of these working at all?

Any help appreciated.

---

### Post by TheDom on 2006-05-02
Hopefull bump?

Have Epson really screwed Ubuntu (and Linux in general) users with this model?

---

### Post by evaristegalois on 2006-07-29
same experience. no luck with this printer. xsane recognizes the scanner but doesn't work with it either. any help out there?

--evaristegalois

---

### Post by getafix123 on 2006-12-29
I got this printer yesterday ... scanner using XSANE works out of box (USB) ... and Printer works fine with CUPS

remember to download the driver from [http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html)

su - (better with a proper root shell)
a) download the tar ball
b) expand the tar ball
c) ./configure
d) make install
e) configure using CUPS printer admin web interface .. works using both IPP and USB

u may get an error on ./configure saying cups-config not found in path .. if so open 'adept' .. search for 'cups' ... install the cups-devel package .. repeat steps 'c, d, e'

HTH

S.

---

### Post by one0 on 2007-12-12
Go here: [http://www.gedda.info/?p=132](http://www.gedda.info/?p=132)

This works well for feisty... for gusty, you must run the command mentioned in the replies about aa-complain. You also have to wrestle a bit to get it to stop defaulting to A4 paper.

---

### Post by Bdanger on 2008-05-04
> **one0 said:**
> Go here: [http://www.gedda.info/?p=132](http://www.gedda.info/?p=132)

This works well for feisty... for gusty, you must run the command mentioned in the replies about aa-complain. You also have to wrestle a bit to get it to stop defaulting to A4 paper.

Can you provide the insructions for getting it to stop defaulting to A4 paper?  I changed it to Letter but it still comes up on the printer screen as set to A4...

---

