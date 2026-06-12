---
title: "Questions about the ATI Drivers"
date: 2006-01-03
forum: Hardware &amp; Laptops
---

### Post by Donnut on 2006-01-03
OK, ive installed the newest (8.20.8) Drivers on my laptop, found they had no widescreen support, so I am asking, Is it OK to use the ATI drivers packaged with Ubuntu?  (when I do a dpkg-reconfigure xserver-xorg) Are they actually ATIs 8.16.2 drivers?  They seem to be the only ones I can succesfully use now...   Thanks.

---

### Post by hod139 on 2006-01-04
I just recently installed the newest ati drivers (8.20.8 ) and I do have widescreen support.  I followed [this howto]("http://ubuntuforums.org/showthread.php?p=423584") directly.  

The ATI driver packaged with ubuntu is _not_ the proprietary ati driver (really bad name imho).  The 3D proprietary driver is actually called fglrx, not ati.  Make sure in your /etc/X11/xorg.conf file, you are using the fglrx driver, not the ati driver in the video selection.  See the above linked howto for step by step instructions.  The new ATI driver, that is the proprietary 3D fglrx driver, works really great for me, and I can now even use suspend since ATI finally fixed that bug!!

---

