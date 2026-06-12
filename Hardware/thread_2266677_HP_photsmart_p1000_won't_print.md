---
title: "HP photsmart p1000 won't print"
date: 2015-02-24
forum: Hardware
---

### Post by peter118 on 2015-02-24
My printer will not print even though lubuntu  14.04,1 sees it. Do I need to load some kind of driver for it to work. I tried it on my windows 7 cpu and it works although I have to use a 970cxi driver since HP does have a driver for Windows 7. Any help would be appreciated. The printer also works with its own functions. If I need to install a driver could someone please show me a step by step. I am still new to this OS and have difficulty navigating around. Thank you all

---

### Post by ajgreeny on 2015-02-24
Check to see if hplip is installed, and if not add it to your system along with hplip-gui.

That will give you both the drivers needed and a terrific configuration and control application.

You can add and configure printers with the [CUPS Printing Webmin]("http://localhost:631/") interface as well, so try both if necessary.

---

