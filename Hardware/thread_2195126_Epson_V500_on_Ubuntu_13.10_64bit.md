---
title: "Epson V500 on Ubuntu 13.10 64bit"
date: 2013-12-22
forum: Hardware
---

### Post by till.halbach on 2013-12-22
After spending a considerable number of hours on getting the Epson's Perfection V500 Photo scanner to work, you might benefit from this simple howto.

Disclaimer: This is for Ubuntu 13.10, 64 bit

a) Start reading the FAQ for your understanding.[INDENT][http://download.ebz.epson.net/faq/linux/faq_ls_00002.html](http://download.ebz.epson.net/faq/linux/faq_ls_00002.html)[/INDENT]
b) Direct your browser to the package list.
[INDENT][http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)[/INDENT]
c) Download and install (in the exact order order)
[INDENT]1) iscan-data_1.25.0-1_all.deb[/INDENT]
[INDENT]2) iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/INDENT]
[INDENT]3) iscan-plugin-gt-x770_2.1.2-1_amd64.deb[/INDENT]
d) With the sane package installed, do[INDENT]sudo sane-find-scanner 
should show something like this:
[snip][/INDENT]
[INDENT]  # you have loaded a kernel SCSI driver for your SCSI adapter.[/INDENT]
[INDENT]found USB scanner (vendor=0x04b8 [EPSON], product=0x0130 [EPSON Scanner]) at libusb:002:005[/INDENT]
[INDENT]  # Your USB scanner was (probably) detected. It may or may not be support[/INDENT]
[INDENT][snip][/INDENT]
e) Test proper installation by issueing [INDENT]sudo scanimage -L
giving[/INDENT]
[INDENT]device `epkowa:interpreter:002:005' is a Epson Perfection V500 flatbed scanner[/INDENT]

g) You can now use iscan or simple scan to operate your scanner.

HTH

---

### Post by Tom_Ryan on 2014-04-06
thank you very much

---

