---
title: "trouble installing printer driver on server"
date: 2010-01-18
forum: Hardware
---

### Post by db34803 on 2010-01-18
I'm a newbie to Linus.  I'm having trouble installing a printer driver for a Canon MP830 on my server running 8.0.4.  CUPS recognizes the USB printer when I use the Web interface.  I've run
 
  dpkg -i openprinting-gutenprint_5.2.4-1lsb3.2_i386.deb  . 

The command appears to complete successfully.   I don't know where to find the .ppd file so that I can use lpadmin to install the printer.  It is not in the /etc/cups/ppd directory.  Guidance appreciated.      :(

---

