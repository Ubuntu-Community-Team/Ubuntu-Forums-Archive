---
title: "Network printer problem"
date: 2012-12-05
forum: Hardware
---

### Post by miloske on 2012-12-05
I installed HP Laserjet M1132 multi-functional on an XP Home machine that functions as a print server. Then I installed it as network printer on all the other Windows machines (XP Home and Win7) without any problems, but I couldn't install it on any of the linux machines. Most of them had some version of Ubuntu (12.04, 9.10 and some others), Peppermint and some other distributions, I was in a hurry, running from a computer to computer and I didn't have time to check it all. The problem on all the linux machines was pretty much the same - they see the print server on the network (I search SMB network for shared printers) and they install drivers for it, but when I try to print something I get prompt for password and a message that print job was sent, but nothing comes out of the printer.

This company had some idiot administrator who never bothered to document his work and he treated all the computers as his toys. We called him and asked for password, he supplied several passwords, but none seems to work. The password prompt sometimes goes away just with blank password and sometimes it accepts anything.

Could the problem be in drivers, the shared printer only has drivers for Windows 2000 and XP, should I try to add drivers for Windows 98? The printer Properties dialog on print server only has options for additional drivers for older versions of Windows, there's no option for adding drivers for other operating systems.

Any ideas?

---

### Post by drdos2006 on 2012-12-05
Have a look at this blog, it may help.

[http://blog.amoktech.com/](http://blog.amoktech.com/)

regards

---

### Post by gordintoronto on 2012-12-05
In Ubuntu 12.04, run Printers. Click on "+" or "Add" and select Network printer. Wait about 10 or 15 seconds, and the printer should appear. Select it and click on various "OK", "continue" or "Yes, that one" boxes until it's installed.

9.10? That needs an upgrade.

---

