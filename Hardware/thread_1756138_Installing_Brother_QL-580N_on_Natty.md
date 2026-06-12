---
title: "Installing Brother QL-580N on Natty"
date: 2011-05-11
forum: Hardware
---

### Post by MidBSD on 2011-05-11
I'm trying to install the Brother QL-580N on my laptop but I'm having no luck.

I thought I had this installed about one month ago but it doesn't appear to be working anymore.

I've downloaded the drivers from:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_esp.html#QL-580N](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_esp.html#QL-580N)

Two files being:
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/ql580ncupswrapper-1.0.0-1.debian.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/ql580ncupswrapper-1.0.0-1.debian.i386.deb&lang=English_gpl)

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/ql580nlpr-1.0.0-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/ql580nlpr-1.0.0-1.i386.deb&lang=English_lpr)

It was quite some time ago but I may have needed to change one of the files to allow installation on my 64Bit system.

I can access the printer from it's web control panel so it's all working and I've printed out test pages from there too.

When I try from the Administration -> Printers and add the printer, no amount of cajoling seems to make it want to work.

The printer properties page keeps saying "Processing - Sending Data files (0 bytes)" and the cups error log just reports:

W [12/May/2011:02:47:18 +0100] [Job 54] Remote host did not respond with data status byte after 300 seconds!
E [12/May/2011:02:57:15 +0100] Ignoring empty "marker-names" attribute

Anyone with any suggestions as to how to diagnose this?

---

