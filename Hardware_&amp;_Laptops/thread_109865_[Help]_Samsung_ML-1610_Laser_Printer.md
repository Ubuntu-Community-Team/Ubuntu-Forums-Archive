---
title: "[Help] Samsung ML-1610 Laser Printer"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by MarioFrick on 2005-12-29
My parents bought me the ML-1610 laser printer for Christmas and it works perfectly when I print some text documents from OOo or any other program. The problem is when I try to print a picture (b/w of course) or a doc with a picture inside it: the printer does not start and the red error light turns on and off. At that stage I have to turn off and on again the printer in order to use it again.

I found an old thread about the same problem, but there was no answer, while it seems that some people here use the ML-1510 with no problems.

I tried using both the ML-1510 and ML-1710 drivers, which are included in Breezy, but the problem is always present with both of them.
So i downloaded the official drivers from Samsung site, installed them, but when I launch linux-config (as sudo) and I try to add a printer it always asks me for the root password, I put it but it does not authenticate (and the pwd is correct, I'm sure, I changed it too).

Any suggestions? Please give me some good news, I was so happy with this printer, cheap and very good, but I need to print some pics sometimes and have no Win anymore on my PC, I'm so happy with Ubuntu!

---

### Post by aysiu on 2005-12-30
[QUOTE=MarioFrick]
So i downloaded the official drivers from Samsung site, installed them, but when I launch linux-config (as sudo) and I try to add a printer it always asks me for the root password, I put it but it does not authenticate (and the pwd is correct, I'm sure, I changed it too).[/QUOTE] Does your sudo password authenticate for other things? ```
sudo apt-get update
``` for example?

---

### Post by MarioFrick on 2005-12-31
[QUOTE=aysiu]Does your sudo password authenticate for other things? ```
sudo apt-get update
``` for example?[/QUOTE]
My sudo password always worked perfectly, and still does, but I set another password for the root user, and if I type "su" I use this second one and it works as well.

---

### Post by timczer on 2005-12-31
I had many issues with the Samsung installer as well with a different Samsung printer.  This thread: [http://www.ubuntuforums.org/showthread.php?t=31796&highlight=running+linux-config](http://www.ubuntuforums.org/showthread.php?t=31796&highlight=running+linux-config)
helped me get the drivers installed.  I did this in hoary, haven't tried it in Breezy to see if it works.

---

### Post by MarioFrick on 2006-01-01
[QUOTE=timczer]I had many issues with the Samsung installer as well with a different Samsung printer.  This thread: [http://www.ubuntuforums.org/showthread.php?t=31796&highlight=running+linux-config](http://www.ubuntuforums.org/showthread.php?t=31796&highlight=running+linux-config)
helped me get the drivers installed.  I did this in hoary, haven't tried it in Breezy to see if it works.[/QUOTE]
Thank you very much, it worked perfectly! :) :) :)

---

### Post by cvmostert on 2006-01-18
[QUOTE=MarioFrick]Thank you very much, it worked perfectly! :) :) :)[/QUOTE]
oh how i hope this works... i will look at the link... hopefully it works for me too...

also have a ML-1610 problem with root authentication...

!!!

---

### Post by pingvin on 2007-02-13
Okay I realise this thread has been untouched for quite a while, but having spent ALL MORNING trying to get my Samsung ML-1610 working with Ubuntu Edgy (I recently upgraded from Dapper) I thought I'd post my findings so no one else ever has to spend so much time on such a simple task. The answer is to use a set of drivers called Splix, which support Samsung's Printer Language (SPL)
So, you plug in the printer and go to [this]("http://openprinting.org/show_driver.cgi?driver=splix&fromprinter=Samsung-ML-1610") website. 
Right click on download link for Splix -> Save target as...
Install alien if you don't already have it, so you can convert RPM packages into Debian ones:
```
sudo apt-get install alien
```
Follow the "How to Install" instructions for Ubuntu/Debian on the website, which involve making new directories and setting up symbolic links, then:
```
alien --scripts *package_name.rpm*
dpkg -i *package_name.deb*
```

Now add a new printer in CUPS (go to localhost:631 in your browser) and point it towards the newly installed .PPD file for the ML-1610 when it asks for a driver, which should be in /opt/share/ppd/Splix/Samsung

That should be it.

Good luck, please let me know if I've left anything out.

Mike

---

