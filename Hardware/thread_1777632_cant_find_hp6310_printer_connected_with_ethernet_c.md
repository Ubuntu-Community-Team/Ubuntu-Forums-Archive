---
title: "cant find hp6310 printer connected with ethernet cable to laptop"
date: 2011-06-08
forum: Hardware
---

### Post by kostasgrk on 2011-06-08
Hi guys...i have a printer hp6310 all in one connected to my laptop directly by ethernet cable.
I just installed ubuntu..i had windows vista and i totally remove them so now i`m using only ubuntu 11.04
I went to printers to find it but i cant see the printer anywhere..what shall i do?

---

### Post by TopEnder on 2011-06-08
G'Day, Try installing HPLIP Toolbox from Ubuntu Software Centre and the add-ons & hopefully you will see your All-In One.  You may need to restart the Laptop with the All-In-One attached & powered on.  If you still don't see the All-In-One then you might have to use a USB cable.

---

### Post by kostasgrk on 2011-06-08
ubuntu doesnt find the printer again.:( any other suggestion?

---

### Post by TopEnder on 2011-06-08
> **kostasgrk said:**
> ubuntu doesnt find the printer again.:( any other suggestion?
Kostasgrk, Been away, something else to try in HPLIP Toolbox (HP Device Manager) select Device and see if the default connection type is set to Network/Ethernet/Wireless network if not select,  See if HP Device manager picks up the Printer & Fax,this works for me on Ubuntu/Xubuntu 11.04 my HP6310 All-In-One only works with USB cable connected & selected in HP Device Manager/Device using Ubuntu 10.10 LTS.  TopEnder

---

### Post by kostasgrk on 2011-06-09
well it works with a usb cable but a solution with ethernet would be appreciate:)

---

### Post by TopEnder on 2011-06-10
Kostasgrk,  I am no expert but suggest you make sure you have all the packages required/suggested installed e.g. HPLIS  Toolbox & suggested packages, Cups packages  & suggested additional packages, I'd check for these packages in both  Ubuntu Software Centre & Synaptic Package Manager.    Check the settings in both HPLIS  Toolbox and the HP6310 (Front Panel)  setup, making sure the printer/fax  & HPLIS  Toolbox are setup correctly to each others settings.  I'd also check to see if the Laptop setting are correct setup ethernet connectio etc (no experience with laptops) TopEnder

---

### Post by TopEnder on 2011-06-10
Kostasgrk,  This link may help you with your printer connection problem.  TopEnder
 
[http://hplipopensource.com/hplip-web/index.htm](http://hplipopensource.com/hplip-web/index.htm)

---

