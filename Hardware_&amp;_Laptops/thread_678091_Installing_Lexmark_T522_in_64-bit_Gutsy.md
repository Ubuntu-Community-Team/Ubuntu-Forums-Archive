---
title: "Installing Lexmark T522 in 64-bit Gutsy"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by phantom42 on 2008-01-25
I am trying to install a Lexmark T522 network printer, but [this driver]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:298:0:0&emeaframe=&fileID=13146&searchLang=en&os_group=Debian%20GNU")  I got from the Lexmark website (which worked just fine in 32-bit edgy) wont install because my new install is 64-bit.
 What I want to know is this: Is there a way to install this driver in 64-bit Gutsy? 
Is there a 64-bit driver anywhere that I can use? and
Is there a way for me to use this printer without installing  the Lexmark software?
I'm pretty sure it uses some sort of generic postscript driver, whatever that means.
Thanks in advance.

---

### Post by Marky-boy on 2008-05-18
Bump

I have this problem with many (most?) printers that are "discontinued" by the manufacturer, as is the case with the T522. Sadly, the i386 architecture divers are the only ones I can find, too, and will not run in AMD64.

You can force the architecture:

sudo dpkg -i --force-architecture /path/name_of_debian_package.deb

This gets the driver installed ok on Hardy 64. Hasn't helped me to get printing working though - across a windows network. As I only have temporary access to this printer I am not going to persevere - but I wish you luck.

Mark

---

