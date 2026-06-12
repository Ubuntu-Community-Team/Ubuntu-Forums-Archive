---
title: "Can't scan with Epson XP-211 printer"
date: 2014-06-23
forum: Hardware
---

### Post by ceciliasp on 2014-06-23
Hi, I've installed and configured the Epson XP211 printer in Ubuntu 14.04 LTS with the official EPSON drivers and it prints ok, but I have two problems:

1) I can't print in draft mode (even though I select the option plain paper - speed)
2) I can't scan wirelessly (I've tried Simple Scan, ScanLite and Xscan and none of them seem to find the device).

Is there any solution to this?

Txs

---

### Post by pdc on 2014-06-24
Hi Cecilia

> I can't scan wirelessly

If you google on > linux epson wireless scanning setup   you should get a hit from > support.epson.ru/upload/library_file/11/scanner_linux.pdf

that has details: if you have a usb cable, you may find that quicker! (you need to edit the file /etc/sane.d/epkowa.conf); I also suspect you need a static ip address for the printer for the scanning files to find it each time .................

---

### Post by ceciliasp on 2014-06-27
Well I guess it all depends on how you make the question right?
I looked in Google with all kinds of phrases, except that one....

---

