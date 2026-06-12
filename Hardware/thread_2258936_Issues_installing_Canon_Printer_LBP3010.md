---
title: "Issues installing Canon Printer LBP3010"
date: 2014-12-31
forum: Hardware
---

### Post by Dan_Corner on 2014-12-31
Hi all!

I have been trying to install my Canon LBP3010 printer on Ubuntu 14.04.01 64bit but I have run into a few issues. Initially I tried to add the printer, but cups didnt have the correct driver. I have since installed the correct driver (from the download Linux_CAPT_PrinterDriver_V260_uk_EN.tar.gz) but when I try and add the printer, in the system settings box, my printer no longer comes up, only an option saying 'CAPT Printer' and a dialogue saying 'enter the devices URI'. What should I do?

---

### Post by Dan_Corner on 2015-01-01
Ok so Ive made some progess. The computer now recognises the pinter, but all that comes up in the CUPS status is "Sending data to printer." What should I try?

---

### Post by pdc on 2015-01-01
Hi Dan;

post #2 gives the details of installing the CAPT driver; [http://ubuntuforums.org/showthread.php?t=2076037&highlight=canon](http://ubuntuforums.org/showthread.php?t=2076037&highlight=canon)

3 steps

1) install CAPT drivers
2) register printer with lpadmin
3) register printer with ccpd daemon

............ so I can maybe help check these ................ are you using 32bit ......................... it's a usb connection?

_____________

I will subscribe to this thread so I get notification of a reply; you might find that helpful too.....................thread tools.................subscribe

_________________

If I leave this link here [http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917) post #4 is Sivella giving a howto and post #6 is his excellent howto-automate the ccpd each time ....................... we can come to that later .............

---

