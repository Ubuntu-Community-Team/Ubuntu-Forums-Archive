---
title: "Printer not recognized as a printer"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by Circir on 2007-05-20
I have a Canon Smartbase MPC190 and I've been trying to get it to work. 
[http://openprinting.org/show_printer.cgi?recnum=Canon-smart_base_mpc190](http://openprinting.org/show_printer.cgi?recnum=Canon-smart_base_mpc190)
lsusb recognizes the printer, but it doesn't use the usblp module and as such I can't use it.

[25502.676847] usb 2-2: new full speed USB device using uhci_hcd and address 8
[25502.849733] usb 2-2: configuration #1 chosen from 1 choice

Dmesg only prints the aforementioned when it should print also something along the lines (I think at least):
Nov 10 15:31:18 quartus kernel: [17280704.532000]
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 23 if 0

[http://circir.blogspot.com/2007/05/no-luck-with-printer.html](http://circir.blogspot.com/2007/05/no-luck-with-printer.html) (Mine)
( [http://osdir.com/ml/printing.hplip.user/2006-11/msg00076.html](http://osdir.com/ml/printing.hplip.user/2006-11/msg00076.html) )

---

