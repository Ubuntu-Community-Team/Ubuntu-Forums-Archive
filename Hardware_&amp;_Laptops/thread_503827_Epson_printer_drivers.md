---
title: "Epson printer drivers"
date: 2007-07-18
forum: Hardware &amp; Laptops
---

### Post by weverjames on 2007-07-18
anyone knows where I can get  driver for my Epson stylus CX7000f.  Ubuntu recognized it inmediatlly, however it sometimes print and sometimes won't.  And the scanner is not recognized.
It does not matter if it is not free software.  Any suggestion?
I came from PCLINUXOS and I did not have this problem.  I am wondering what driver they use and if I can get it in my ubuntu.

---

### Post by linuxwizard on 2007-07-19
I don't see that model. I see DX7000f.

[http://www.openprinting.org/printer_list.cgi?make=Epson](http://www.openprinting.org/printer_list.cgi?make=Epson)

---

### Post by gobbles414 on 2007-07-19
I have a friend who recently tried to use an Epson CX5000 with her Ubuntu system. She encountered the same sort of problems. After a few days of such problems, the printer stopped working entirely and a solid "INK" light activated on the printer. According to the manual, this meant that one of the ink cartridges was empty -- very unlikely seeing as the cartridges were brand new. I then tried to get the printer working by connecting it to a Microsoft WIndows computer, but the printer would not communicate with Windows at all.  So, the printer was either defective, or the CUPS drivers somehow damaged it. I'm leaning towards defective.

Regarding the scanner, I have discovered two options that may work for you. The first is discussed at the following URL: ([http://ubuntuforums.org/showthread.php?t=495721](http://ubuntuforums.org/showthread.php?t=495721)). In addition to the info there, I also added my friend's user account to the group called *scanner* You can accomplish that by *going system --> administration --> users and groups*. That may or may not have been required.

The other option is to add *gksudo* to the beginning of any scanning program's launch command (e.g. *gksudo xsane* or *gksudo gscan2pdf*.).The downside to this is that only root will have full read/write access to the files you create when scanning. You can, of course change the permissions of these files manually later. You can edit the launch command associated with any program by accessing *preferences --> main menu*.

I hope that this helps. Please report back!

---

### Post by gobbles414 on 2007-08-24
I recently discovered that the built-in USB 2.0 ports on my friend's computer are defective. Thus, it is likely that the defective ports corrupted the firmware on her Epson all-in-one. Also, I'm curious to know if your issue has been solved weverjames?

---

