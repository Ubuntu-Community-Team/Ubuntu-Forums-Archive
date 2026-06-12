---
title: "help with HP color laserjet 5"
date: 2009-02-21
forum: Hardware
---

### Post by pHuXx on 2009-02-21
hey.

so after a lot of time and trouble, i still haven't managed to get my hp colorlaserjet 5 to work on my ubuntu 8.10

ive installed the ppd files and CUPS and everything.

is there any specific nuances i may have overlooked? 

thanks

---

### Post by cariboo on 2009-02-21
According to the [OpenPrinting Database]("http://www.openprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_5") you printer works perfectly, with drivers installed by default. I would suggest you install hplip-gui to help you install the printer. Hplip-gui is in the repositories.

Jim

---

### Post by linux6994 on 2009-02-21
I use hplip it automatically detects and installs hp printers.

sudo apt-get install hplip hplip-gui

Go to System > Administration > HP

---

### Post by pHuXx on 2009-02-21
thanks guys, i have HPLIP and i can print a test page from it, but when i goto print something else, say the google homepage [61K] it says "40 I/O error" on the printer 

:S

---

