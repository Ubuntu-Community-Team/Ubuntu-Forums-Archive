---
title: "HP Photosmart c4140"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by K3l3v on 2007-11-18
I bought this printer a few months back, thinking that it should work with linux, no problem...  I got that idea from [this website]("http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4100").  Silly me!  I should have known that all-in-wonder printers never work perfectly!  Not even when they are run under windoze with the manufacturer's own software.

However, today I figured out how to get the printer to work...  Hopefully this will help someone else who's struggling with those Photosmart printers.

First, I downloaded [HPLIP from here]("http://hplip.sourceforge.net/downloads.html").  I hear there's a debian package already, but that's not how I did things...

Second, I installed HPLIP according to [the instructions on the website.]("http://hplip.sourceforge.net/install/install/index.html")  When the GUI interface came up, I didn't see my printer's *.ppd file listed...  So I went [here]("http://www.linuxprinting.org/show_driver.cgi?driver=hpijs") and generated one.  Downloaded the new *.ppd file to the right directory (the same one that the GUI was pulling from), manually selected it from file, and continued with the installation.

Lastly, the GUI setup offers the option to print a test page (via a check box in the last dialog box).  I am now looking at a properly formatted, properly colored printout from my printer via linux for the very first time!  *sniff*

Hope that helps.

---

