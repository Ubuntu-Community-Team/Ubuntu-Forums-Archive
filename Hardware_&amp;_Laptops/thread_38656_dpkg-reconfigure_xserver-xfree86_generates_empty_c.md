---
title: "dpkg-reconfigure xserver-xfree86 generates empty config file"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by Poldi on 2005-06-01
hi all.

I am on Hoary 5.04 and wanted to change X11.org back to XFree86.

I did apt-get install xserver-xfree86

this left my without a working X, due to an empty /etc/X11/XF86Config-4 file.

I then did dpkg-reconfigure xserver-xfree86.

still, after setting everything to default (but my card - an old S3 Savage known to work) my XF86Config-4 stays empty.

system is a Thinkpad T20. the machine did work with Warty/XFree86 without any configuration (it works with X11.org/Hoary, too - but I need to test sth. with XFre86 on Hoary) 

what am I missing?

kind regards,
Carsten

---

### Post by stanwebber on 2005-07-06
the same goddamn thing happened to me.  XF86Config-4 is empty!

---

