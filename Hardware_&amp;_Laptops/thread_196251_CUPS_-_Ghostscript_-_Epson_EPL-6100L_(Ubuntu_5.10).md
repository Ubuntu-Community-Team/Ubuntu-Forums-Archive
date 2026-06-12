---
title: "CUPS - Ghostscript - Epson EPL-6100L (Ubuntu 5.10)"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by planktom on 2006-06-13
Warning: This text was manually translated from german to english. We apologize for mistakes

Hi,
I just wanted to print...
Printer is working (under vmware - xp). I think that this might be the cause: -sIjsServer=ijs_server_epsonepl. I've compiled a new version of Ghostscript but I couldn#t see anything like "ijs_server_epsonepl". In the sourcecode I've found ijs_server.c.
Here's a snip of /var/log/cups/error_log

D [13/Jun/2006:14:47:22 +0200] [Job 36] foomatic-gswrapper: gs '-dBATCH' '-dSAFER' '-dNOPAUSE' '-sProcessColorModel=DeviceGray' '-dBitsPerSample=1' '-sDEVICE=ijs' '-sIjsServer=ijs_server_epsonepl' '-dIjsUseOutputFD' '-sDeviceManufacturer=Epson' '-sDeviceModel=EPL6100L' '-sIjsParams=EplFlowControl=off,EplDpi=600,EplDensit y=3,EplRitech=on,EplTonerSave=off,' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [13/Jun/2006:14:47:23 +0200] [Job 36] ESP Ghostscript 815.02 (2006-04-19)
D [13/Jun/2006:14:47:23 +0200] [Job 36] Copyright (C) 2004 artofcode LLC, Benicia, CA. All rights reserved.
D [13/Jun/2006:14:47:23 +0200] [Job 36] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [13/Jun/2006:14:47:23 +0200] [Job 36] sh: ijs_server_epsonepl: command not found
D [13/Jun/2006:14:47:23 +0200] [Job 36] ESP Ghostscript 815.02: Can't start ijs server "ijs_server_epsonepl"
D [13/Jun/2006:14:47:23 +0200] [Job 36] **** Unable to open the initial device, quitting.
D [13/Jun/2006:14:47:23 +0200] [Job 36] renderer return value: 1
D [13/Jun/2006:14:47:23 +0200] [Job 36] renderer received signal: 1
D [13/Jun/2006:14:47:23 +0200] [Job 36] Process dying with "Possible error on renderer command line or PostScript error. Check options.", exit stat: 3

To make the new version of ghostscript running, I had to change a softlink - should the same be necessary for '-sIjsServer=ijs_server_epsonepl'?

Thanks for each help!

Ciao
Tom

---

### Post by planktom on 2006-06-14
Solution!
[http://www.ubuntu-forum.de/artikel/1729/Epson-5700L-Cups-printer.html](http://www.ubuntu-forum.de/artikel/1729/Epson-5700L-Cups-printer.html)

---

