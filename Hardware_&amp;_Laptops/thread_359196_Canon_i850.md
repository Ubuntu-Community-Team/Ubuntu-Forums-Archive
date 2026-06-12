---
title: "Canon i850"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by feelinggood on 2007-02-11
Hi, I am a newbie and have the Canon I850 printer and need to know the correct drivers and how to install them properly.  I have a driver installed but the printing is poor at best.  Any help would be great.  Thanks, Steve

---

### Post by feelinggood on 2007-02-16
bump up for some help

---

### Post by namko on 2007-08-14
Hello,
There are two ways that I found to get the printer working. I run Kubuntu 7.04.

1) Download and install TurboPrint from [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html). With TurboPrint you can print with a resolution of 300dpi for free, but if you choose to print with higher resolution (up tp 2400dpi) TurboPrint logo will be printed on each page unless you get a key for about $38.

2) Will allow you to print with a resolution of 600dpi for free, but is a little more involved. Go to [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon) and follow the directions for Ubuntu (the apt-line should be added to /etc/apt/sources.list, after adding the line run apt-get update). Once the installation completes, run the cupsys configuration by going to [http://127.0.0.1:631/](http://127.0.0.1:631/) .If you try to add the printer by going into "system settings", i850 will not show up.

Good luck.

---

