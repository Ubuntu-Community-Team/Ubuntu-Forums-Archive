---
title: "Printing: postscript files with duplex doesn't work"
date: 2013-05-21
forum: Hardware
---

### Post by iaw4 on 2013-05-21
Standard Ubuntu 13.04, 64-bit.  Nothing Special.

Printer: Lexmark C544dn .  Postscript.  /dev/usb/lp0 and CUPS seem to be mostly working---CUPS can receive files, queue them, and print them.  that is, pdf files get queued and sent out.  I can also grab the d* file from the CUPS queue and copy it to /dev/usb/lp0 to get non-duplex output.

alas, when I select options, such as duplex printing from a simple pdf display program (such as okular), I get a page with line noise (garbage) on the first two lines, which I believe to be the printer assuming that I am trying to print a text page, not a postscript file.  (cp somefile.txt /dev/usb/lp0 works, except that \n seems to be a linefeed not a carriage return.)

there must be some job control pass-through miscommunication.

how would I use the CLI to send a postscript file to the printer (device) without CUPS instructing the printer to print the document in duplex?

hints appreciated.  generally, CUPS seems to be less temperamental on OSX than on linux.

/iaw

---

