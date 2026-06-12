---
title: "Removing iscan 2400dpi scan limitation (Epson Perfection V350 and others)"
date: 2009-03-04
forum: Hardware
---

### Post by julian.coccia on 2009-03-04
Just in case anyone is experiencing a 2400dpi limitation on the V350 Photo (I think it also happens with the V100), there is a workaround.

[http://juliancoccia.posterous.com/removing-2400dpi-limitation-fo](http://juliancoccia.posterous.com/removing-2400dpi-limitation-fo)

Pasting it all here:

I have recently realized that the Linux driver for the Epson Perfection V350 has an imposed limitation of 2400dpi, while the scanner is capable of doing 4800dpi under Windows.
 
Apparently, this scanner requires a binary plugin which returns a maximum scanner resolution to iscan, which is distributed under GPL and the code is made available here: [http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)
 
After a quick look at the code, I realized the "iscan" scanning program was limiting the resolution settings to whatever the proprietary plugin was returning as max_resolution. However, if you remove this limitation and tell it to scan at 4800, it will do it. 
 
As a result of that, I now have 4800dpi support under Linux. If you are interested, download the source and replace the frontend/pisa_main_window.cc file with the one I include here before building. 

If you are lazy, instead, simply install the binary version of the scanner and plugins and replace the /usr/bin/iscan file with the one I include here.
 
Modified iscan source and binary:
[http://julian.coccia.com/stuff/iscan-4800dpi.zip](http://julian.coccia.com/stuff/iscan-4800dpi.zip)

---

