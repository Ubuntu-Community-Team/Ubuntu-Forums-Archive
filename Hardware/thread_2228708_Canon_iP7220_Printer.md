---
title: "Canon iP7220 Printer"
date: 2014-06-09
forum: Hardware
---

### Post by jmarsz on 2014-06-09
I need a bit of help with my printer.  It's a Canon PIXMA iP7220 printer, and I can get linux to recognize the printer, and associate a "close" driver with the printer (iP 7100 Series), but when I try to print to the printer, nothing prints.  It will send the job to the printer, and even say "Rendering complete", but nothing on the printer happens.  Any suggestions?  Thanks!

---

### Post by pdc on 2014-06-09
Can I suggest you install the linux drivers that Canon supply for your very good printer?

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html) you will be downloading [COLOR="#008000"]cnijfilter-ip7200series-3.80-1-deb.tar.gz[/COLOR] and if you elect to **SAVE** it as it comes down; and by default it will be in your [COLOR="#0000FF"]Downloads[/COLOR] directory

If you open a terminal; and copy and paste the commands into the terminal: use your mouse and the top line of the terminal

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-ip7200series-3.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-ip7200series-3.80-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

that final command runs an install script; it looks to see if you have 32 or 64bit and installs the appropriate; it will also ask if usb or network install

________________

that should create a printer entry and it should work!

---

### Post by jmarsz on 2014-06-10
That worked for me!  How did you find that printer driver?  When you look on Canon's USA website, it says that there's no linux driver for this printer.

---

### Post by pdc on 2014-06-10
> That worked for me!          ...........great.........enjoy.........

> How did you find that printer driver? When you look on Canon's USA website, it says that there's no linux driver for this printer. 

I guess whilst Canon is global; they are from Japan, so the Canon Asia website; and the Canon Europe site both have the full range of Canon linux drivers;

one would think the US site would just link to the Asia resource........

---

### Post by MepisReign on 2014-07-19
Hello, a quick question, will this driver allow to print to compact discs?

Thank you,

MepisReign

---

