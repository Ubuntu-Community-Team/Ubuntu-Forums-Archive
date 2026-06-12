---
title: "Epson Stylus Photo RX685 scanner in 10.04 Lucid Lynx"
date: 2010-05-16
forum: Hardware
---

### Post by TurboTippy on 2010-05-16
Hello All

I've been dabbling with Linux for many years, but until now have found it not to really be real windows replacement - until yesterday! I am seriously impressed with the latest 10.04 build, which apart from my scanner installed easily, with most things working straight out of the box. It also means I can finally move 64 bit without too much effort. So I've committed myself to working on this problem.

I've scoured these forums and haven't found anyone with the same scanner so looking for ideas. CUPS picks up the printer, but the XSane doesn't see the scanner.

Any ideas where to start? Really hoping I can get this sorted.

TT

---

### Post by sau99ms on 2010-05-16
> **TurboTippy said:**
> Hello All

I've been dabbling with Linux for many years, but until now have found it not to really be real windows replacement - until yesterday! I am seriously impressed with the latest 10.04 build, which apart from my scanner installed easily, with most things working straight out of the box. It also means I can finally move 64 bit without too much effort. So I've committed myself to working on this problem.

I've scoured these forums and haven't found anyone with the same scanner so looking for ideas. CUPS picks up the printer, but the XSane doesn't see the scanner.

Any ideas where to start? Really hoping I can get this sorted.

TT

Try installing simple-scan in synaptic first and see if that works instead. XSane is needlessly over-complicated....

Then turn on your printer/scanner, open Simple Scan then go to Document -> Preferences and see if you can find the scanner source you're looking for.

Post back and let me know if this works. Did the job for me...

Mark

---

### Post by TurboTippy on 2010-05-16
Thanks

Simple scan was already installed, but have re-installed it. On running it, it can't find the scan source, nor is it shown in preferences.

---

### Post by ellgor on 2010-05-16
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

---

### Post by TurboTippy on 2010-05-17
Well, I had to learn a little, how to start gdebi and found that the iscan_2.24.0-4.ltdl7_i386.deb package works ¬!!!!! nice one guys, really happy with this. Now if I could get network printing working, I have a my full windows replacement!

---

