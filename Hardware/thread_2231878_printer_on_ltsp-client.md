---
title: "printer on ltsp-client"
date: 2014-06-28
forum: Hardware
---

### Post by hendrikmaes on 2014-06-28
Hello,
I'm trying to install a Lexmarkprinter on a ltsp-client and allthough I adapted lts.conf I can't get it functioning (CUPS says 'printer busy' and nothing comes out of the printer).

In my lts.conf I have

[Printer]
 PRINTER_0_DEVICE = "/dev/usb/lp0"
 PRINTER_0_PORT = 9100

It's a Lexmark X1270 printer and it's working perfectly when connected to the server, with the lexmark Z600 driver.

Thanks in advance for any help.

---

