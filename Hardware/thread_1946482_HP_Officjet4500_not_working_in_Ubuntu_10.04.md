---
title: "HP Officjet4500 not working in Ubuntu 10.04"
date: 2012-03-24
forum: Hardware
---

### Post by johnnydoe on 2012-03-24
My printer is connected to my router as is my laptop.  Ubuntu found the printer and the device's UI is: socket://HPDD87D1:9100.  HPDD87D1 is the hostname, and it is using port 9100.  However, it will not print a test page.  It just says "connecting to printer," for hours.

---

### Post by Bucky Ball on 2012-03-24
You probably need to install HPLIP, or upgrade it. What is the printer model?

Firstly, you need this. Download the firmware and follow the instruction on this link:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=18972&prodSeriesId=1143083&prodNameId=1143084&swEnvOID=2020&swLang=8&mode=2&taskId=135&swItem=pl-59643-5](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=18972&prodSeriesId=1143083&prodNameId=1143084&swEnvOID=2020&swLang=8&mode=2&taskId=135&swItem=pl-59643-5)

---

### Post by johnnydoe on 2012-03-24
It is a HP OfficeJet 4500.  The link you provided says that the firmware covers HP DesignJet 4500.  Would that work as well?

---

### Post by Bucky Ball on 2012-03-24
My mistake. On this page:

[http://www8.hp.com/us/en/support-drivers.html](http://www8.hp.com/us/en/support-drivers.html)

... you will find the 4500 OfficeJets a bit further down the page. Click yours and follow the links to the Linux driver. ;)

HP is very well supported in Ubuntu and we should be able to get this working without too much hassle (although these could be famous last words!).

---

### Post by johnnydoe on 2012-03-24
Thanks for the link.  I installed the firmware.  Restarted everything and ran hp-setup.  However the device discovery tool is not finding my printer.  I chose the Ethernet/Network/Wireless network option and it could not locate it.  I also tried manually searching for my printer's ip address, but no luck.

---

### Post by johnnydoe on 2012-03-24
I thought about using System > Administration > Printing, and try to add it again that way, but I didn't want to negate what I just did.

---

### Post by Bucky Ball on 2012-03-24
> **johnnydoe said:**
> I thought about using System > Administration > Printing, and try to add it again that way, but I didn't want to negate what I just did.

Yep, good idea and my next suggestion. Go there, add printer and click on 'Network Printer' I think it is. Wait for awhile as it sometimes takes awhile to pick it up. It should appear there if everything configured right (and the printer is actually communicating with your LAN). You shouldn't need to do anything manually if the printer is on your LAN.

Incidentally, can you ping the printer? Open a terminal and:

```
ping ***.***.***.***
```... where ***.***.***.*** is the IP of your printer ...

---

### Post by johnnydoe on 2012-03-24
Scratch that.  I had wireless isolation enabled on my router.  Thanks for your help!!

---

### Post by Bucky Ball on 2012-03-24
No probs.

It's working, then? If so, please mark thread as 'Solved' from Thread Tools at top right. ;)

---

