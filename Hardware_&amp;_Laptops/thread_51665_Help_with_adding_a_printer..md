---
title: "Help with adding a printer."
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by pinual on 2005-07-24
I've been using linux for a couple months now and have always been able to install my printer.  I switched to ubuntu recently because I heard it was easy to use but still had the power of debian.  I wasn't dissapointed (in fact I love it, its awesome, and no more manually installing those nVidia drivers), but I really need to get my printer to work.  I have a very old Apple LaserWriter Select 360 that connects through a big printer port (sorry thats all I can describe, its not USB though), and whenever I go to install the printer its never detected and the only ports I can choose from are USB ports.  I was able to install my printer in Fedora Core 4 and in Debian Sarge so I am wondering why I am not able to install in Ubuntu. Help please.

---

### Post by David Haas on 2005-07-25
pinual--You probably have a parallel-port connection, but it should work fine.Fortunately for you, Ubuntu has the driver (PPD file) for your printer, by default. It's Apple-LaserWriter_Select_360-Postscript.ppd.gz. It's in the Apple directory at /usr/share/cups/model/foomatic-ppds/Apple. I'd install the printer with the Gnome printer manager at System>Administration>Printing. Sometimes it seems to help to turn on the printer before booting the computer. After selecting your printer, select the driver (PPD file), by clicking through the directories above in the file manger in the GUI. After selecting it, Linux should place an unzippeed copy in /etc/cups/ppd. Well, I hope this helps.
David
.

---

