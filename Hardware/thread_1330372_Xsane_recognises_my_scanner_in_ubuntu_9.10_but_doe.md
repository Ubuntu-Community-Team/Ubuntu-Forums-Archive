---
title: "Xsane recognises my scanner in ubuntu 9.10 but doesn't start it up. No scanning."
date: 2009-11-18
forum: Hardware
---

### Post by Enterprisemember on 2009-11-18
Xsane recognises my scanner hp scanjet g2410 in ubuntu 9.10 but doesn't start it up. No scanning.
 
There is no problem about finding my scanner but ubuntu 9.10 xsane doesn't start it up...I mean I get an error message that xsane can't scan...
 
Who can help me because this is a real problem...I searched for days all over the internet ; found some old solutions but nothing works for me...
 
Thank you very much in advance for your help,
 
Greetings,
 
Enterprisemember,

---

### Post by mecheware on 2010-06-17
So I'm not the only one who's having this problem, I have to go back to Windows, just to use my scanner, what a bummer!

---

### Post by dabl on 2010-06-17
Is there a "libsane-extras" package in the repo?  If so, install that and try again with the scanner.

---

### Post by desertdog on 2010-06-24
The HP G2410 is a clone of the HP 2400c. 
They are both listed as "untested" on the Sane-project supported scanner list. 
A recent post on the sane-devel mailing list, it was reported that only 300dpi greyscale works, but 300 dpi color could be obtained with a simple hack.
[http://lists.alioth.debian.org/pipermail/sane-devel/2010-June/026973.html](http://lists.alioth.debian.org/pipermail/sane-devel/2010-June/026973.html)

To compile the latest sane from source, see [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

Also, there is a proprietary linux driver for the 2400, which should work on your scanner. See: [http://lists.alioth.debian.org/pipermail/sane-devel/2009-January/023517.html](http://lists.alioth.debian.org/pipermail/sane-devel/2009-January/023517.html)

---

