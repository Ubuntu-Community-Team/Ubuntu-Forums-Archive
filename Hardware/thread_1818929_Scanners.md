---
title: "Scanners"
date: 2011-08-05
forum: Hardware
---

### Post by aSystemOverload on 2011-08-05
Hi

I've just installed Ubuntu on a machine, tried to get my wireless printer/scanner working, but I can't seem to get the scanner part working.  Only software listed for scanning is SIMPLE SCAN and it just says, NO SCANNERS AVAILABLE and if you choose CONFIGURE SCANNER, it says "Scan Source: Epson PID 0856",, so why doesn't it work... HELP? 

Thnx

---

### Post by nteckhardt on 2011-08-05
I am having the same issue. I have a wireless pinter/scanner. I can print no problem. However, when I want to scan a document with Simple Scan it will not let me. However when I view the preferences window, the scan source is blank. It sounds as though we may have similar issues.

---

### Post by aSystemOverload on 2011-08-06
Hmmmm, hoping someone can help us, will put an obstruction in the way of me moving to Linux GRRR

---

### Post by MartyBuntu on 2011-08-06
Have you tried installing XSane?
You might have better luck with that than simple scan.

What is the exact model of the printer/scanner?

---

### Post by aSystemOverload on 2011-08-06
Yeah  I found that, the printer/scanner is an Epson Stylus SX515w (I think), I'll confirm it when I'm back there on Monday.

---

### Post by agklimit on 2011-08-06
I'm quite happy with Image Scan! for Linux 2.26.4 (Ubuntu 11.04 and an Epson Perfection V350 Photo scanner). I've just tested scanning from film, and it works fine. I've installed this after following instructions from Avasys website ([http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do))

---

### Post by IcarusR on 2011-08-06
Xsane does not support sx515w.
You need to download drivers from avasys. Go to the following url & select your printer/scanner, OS & version then on next page download drivers.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do")

Both simplescan & xsane should then recognise your scanner/printer

---

### Post by aSystemOverload on 2011-08-06
Oooohhh, will try that Monday, if it works, thanks!  If it doesn't, thanks anyway, lol.

---

### Post by aSystemOverload on 2011-08-08
I've got it working, thanks for that.  Only issue is it is generating PDFs much larger than it should (1 MB for a A4 sheet of 25% filled writing).

Any ideas?

---

### Post by George Stephenson on 2011-08-20
I've been there, done that also.  Have downloaded the stuff from avasys for my new Epson SX425W (DX6050 died).  Can't find the driver on the PC and can't get PC or Scanner to speak to each other.  What next?

(prints fine - ubuntu 10.04lts has a printer driver, but not a scanner driver.)

---

