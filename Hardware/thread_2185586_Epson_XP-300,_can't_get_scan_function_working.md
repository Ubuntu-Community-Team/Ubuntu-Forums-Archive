---
title: "Epson XP-300, can't get scan function working"
date: 2013-11-03
forum: Hardware
---

### Post by Stan_Meissner on 2013-11-03
I have an Epson XP-300 and was able to get the print function working but am unable to get the scanner to work.  I downloaded what are labeled as scanner drivers (32 bit i386) on the Epson site and when I try to install using Ubuntu Software Center I get the error message "dependency is not satisfiable: iscan-data".  So far I have read everything I can find on the subject and am running up against my inexperience using terminal commands.  If a fix is spelled out clearly I don't have any problem opening a terminal session and following instructions but on this subject I'm finding the posts a little over my head at my present level of knowledge.  Any suggestions on how I might get this resolved will be greatly appreciated.  

:D

---

### Post by Stan_Meissner on 2013-11-18
Hey everyone, problem solved.  Printer and scanner working great.  I can't find the thread that helped me resolve this so I'll try to explain how I resolved it the best I can.  First you have to download the scanner drivers from the Epson site.  I had attempted this before without success but I found a post where someone mentioned that the driver downloads are dependent on each other and have to be installed in proper sequence.  The files for my 32 bit system were iscan-data_1.24.0-2_all.deb and scan_2.29.2-1~usb0.1.ltdl7_i386.deb and you have to install them in the proper sequence.  The printer setup went pretty smoothly but both did require a reboot and making sure that the printer was recognized.  Now the only snag left for this new Ubuntu user is to figure out file sharing but that's a task for a Saturday when I have more time.  I'm only a few weeks into working with Ubuntu and I've resolved some sticky problems including printer, scanner, screen resolution and a Broadcom network card in my wife's Gateway Laptop.  I've even got a few of my favorite Windows programs running perfectly on Wine.  Not bad for a card carrying AARP member.  ;)

---

### Post by marcjknight on 2013-12-20
Hi there. I need the files you mention in your thread, the iscan-data_1.24.0-2_all.deb and the scan_2.29.2-1~usb0.1.ltdl7_i386.deb but it appears Epson don't host it any longer. I've tried everything to find a download link with no success. Is there a chance you could email it to me? Regards

---

### Post by upa on 2014-02-03
Some problem here with the L355. Below is the driver's download page for both the printer and the scanner. The scanner one has link to FAQs at the bottom where it explains the installation order. I followed those instructions (without reboot) but still the file iscan_2.29.3-1~usb0.1.ltdl7_i386.deb keep saying it cannot satisfy dependecy
 
[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=ES&CN2=&DSCMI=25083&DSCCHK=84d3a5cf0ddcd834aeb8ea038e6d040c56d9efd9](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=ES&CN2=&DSCMI=25083&DSCCHK=84d3a5cf0ddcd834aeb8ea038e6d040c56d9efd9)

---

