---
title: "Printer compatibility issue on Ubuntu 10.04"
date: 2011-09-01
forum: Hardware
---

### Post by TangentDelta on 2011-09-01
Hello, I joined because I am having an issue with a Kodak EasyShare 5300 not working. Ubuntu recognizes it but when I try to print something, it says processing job in the Ubuntu print job manager and sits there. I left it sitting like that for a night, and in the morning it was doing the same thing. It seems like Ubuntu recognizes the printer but the printer doesn't recognize ubuntu. 

This printer does work, but it doesn't work on ubuntu.

---

### Post by TangentDelta on 2011-09-02
Bumping topic, I really need an answer.

---

### Post by fidelandche on 2011-09-02
Have you gone to the Kodak site to see if they do a driver for linux?

---

### Post by walt.smith1960 on 2011-09-02
You might look here:
[http://www.openprinting.org/printer/Kodak/Kodak-EasyShare_5300](http://www.openprinting.org/printer/Kodak/Kodak-EasyShare_5300)
It appears that text & line art work perfectly, photos and graphics less than perfect.

---

### Post by TangentDelta on 2011-09-03
How do I go about compiling the source? for the CUPS driver?

---

### Post by walt.smith1960 on 2011-09-08
There are several files there and I suspect you don't have to compile from source.  I see a .deb file which is sort of like an .exe file.  You just click on it and Ubuntu Software Center will probably open.  I prefer Gdebi (from Synaptic) but either one should work.  The Software Center will give cautions about software quality but should still install. Gdebi seems less fussy.  There is also an install file but I'm not sure about the syntax.  Some time in Ubuntu help or google may be helpful as well.
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)

---

### Post by paulnewall on 2011-10-08
Also this driver should be included in ubuntu 11.10 when it's issued

---

