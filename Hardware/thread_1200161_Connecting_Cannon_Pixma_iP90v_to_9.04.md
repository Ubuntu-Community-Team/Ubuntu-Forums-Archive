---
title: "Connecting Cannon Pixma iP90v to 9.04"
date: 2009-06-29
forum: Hardware
---

### Post by bm90 on 2009-06-29
Hi, I'm trying to connect a Cannon Pixma iP90v to 9.04 to a Novatech X15 GT, and haven't been having much luck.
I also tried it on a Dell 5000, and couldn't get it to work, so I don't think its the computer hardware thats causing the problem.


The problem is, I connect the printer, and add a new printer via the printer configuration. At the end of the setup, it states

> Missing Driver
Printer 'iP90' requires the 'pstocanonij' program but it is not currently installed. Please install it before using printer.


Searching around, I found two other threads where people have had issues with this printer, and I have found the solutions to not work.
[http://ubuntuforums.org/showthread.php?t=662002]("http://ubuntuforums.org/showthread.php?t=662002")
[http://ubuntuforums.org/showthread.php?t=1040088&highlight=ip90v]("http://ubuntuforums.org/showthread.php?t=1040088&highlight=ip90v")

When I try to print with it (after installing the driver mentioned [here]("http://ubuntuforums.org/showthread.php?t=662002") it gives the message 

>  Printer 'iP90':'cups-missing-filter

I know cups is something to do with a print server, but thats about the end of my knowledge on it.


Also, [this site]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP90")states that it works perfectly with linux, and offers recommended drivers, but I don't know how to try them out.

So, I was wondering if anyone can give me a hint what to do here, my older printers just pluged in a printed right away, this ones a bit more frustrating.

Thanks.


edit: also, just installed it through [this guide]("http://ubuntuforums.org/showthread.php?t=504643&highlight=ip90), and it still gives

> [http://ubuntuforums.org/showthread.php?t=504643&highlight=ip90](http://ubuntuforums.org/showthread.php?t=504643&highlight=ip90)

I think I still have the CDs shipped with it, would pstocanonij be on there somewhere?

---

### Post by speedygeo on 2010-03-14
I use with a sufficient satisfaction the driver included in every linux distribution I tried for my Canon PIXMA iP 90.
I use the Canon BJC-8200 Foomatic and works mostly well.

---

### Post by sangrey on 2011-02-13
> **speedygeo said:**
> I use with a sufficient satisfaction the driver included in every linux distribution I tried for my Canon PIXMA iP 90.
I use the Canon BJC-8200 Foomatic and works mostly well.
This works. I think there is a bug with the supplied driver for iP90v from the canon website. Just use Canon BJC-200 foomatic from the print settings menu and when it asks you whether to use the old or new PPD, use the old PPD that exists  in <path to ip90v install>/usr/share/cups/model/canonip90.ppd .

This file was created when I tried to install from Canon's driver website using cnijfilter-common-2.70-2.src.rpm download. See [http://ubuntuforums.org/showthread.php?t=662002](http://ubuntuforums.org/showthread.php?t=662002) for how to do the install. It might work on other people's systems, but at least you can extract the canonip90.ppd file.

---

### Post by cheech12 on 2011-09-16
> **sangrey said:**
> This works. I think there is a bug with the supplied driver for iP90v from the canon website. Just use Canon BJC-200 foomatic from the print settings menu and when it asks you whether to use the old or new PPD, use the old PPD that exists  in <path to ip90v install>/usr/share/cups/model/canonip90.ppd .

This file was created when I tried to install from Canon's driver website using cnijfilter-common-2.70-2.src.rpm download. See [http://ubuntuforums.org/showthread.php?t=662002](http://ubuntuforums.org/showthread.php?t=662002) for how to do the install. It might work on other people's systems, but at least you can extract the canonip90.ppd file.
  
 want to install

---

