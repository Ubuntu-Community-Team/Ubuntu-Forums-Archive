---
title: "HP photosmart 7760 printer problem"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by zurg on 2005-10-21
ciao
I installed ubuntu couple of days ago and I think is the best distro I've tried so far, really lovely. I got a problem w\ my HP photosmart 7760 printer. It seems to be recognized by the system but not connected. I've installed the proper driver but it's still not connected; launching lpstat got the following:

```
zurg@ubuntu:~$ lpstat -t
scheduler is running
system default destination: PhotoSmart-7760
device for PhotoSmart-7760: usb:/dev/usb/lp0
PhotoSmart-7760 accepting requests since Jan 01 00:00
printer PhotoSmart-7760 now printing PhotoSmart-7760-15.  enabled since Jan 01 00:00
        Printer not connected; will retry in 30 seconds...
PhotoSmart-7760-15      zack             61440   ven 21 ott 2005 17:15:06 CEST
```


can anyone help please?

---

### Post by ColinG on 2005-10-27
I've got problems with a 7762, although it does print. It seems, in common with other distro forums, that any printer issues go, in the main, completely unanswered. 

Personally, I think linux support for printers sucks - it is a case of making sure you have one that will be compatible. Shame really, trouble is that Winoze supports more printers so there is a high probability that someone trying out Linux will come unstuck print-wise.

---

### Post by pinballkid on 2005-11-04
I'm using a photosmart 2600, so this may be of no help at all, but [hpoj]("http://hpoj.sourceforge.net/index.shtml") worked wonders for me. In fact, it works far better than my (monolythic) windows drivers!

---

