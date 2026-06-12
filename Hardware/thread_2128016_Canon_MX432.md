---
title: "Canon MX432"
date: 2013-03-21
forum: Hardware
---

### Post by hawkhock on 2013-03-21
Would like to return to Ubuntu, dual booting with Win7 as I need to keep Windows for work projects.
From brief Wubi install to check things out, already know that printer compatibility is an issue with Canon MX432. However, I may have found a potential solution. 
What other problems can I expect with Toshiba laptop?
Go with 12.04LTS? 32 bit or 64 bit?
OR go with 12.10?

---

### Post by bcbc on 2013-03-21
12.04 64bit is the best for your ram and for long term support. Otherwise you'll have to upgrade more frequently and see more major changes to the interface etc.

---

### Post by pdc on 2013-03-21
Canon provide a debian package driver for your MX430 series device; [COLOR="#008000"]**cnijfilter-mx430series-3.70-1-deb.tar.gz**[/COLOR]

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412601.html) 

it has an install script and debian drivers for both 32bit and 64bit so the commands to install the driver would be

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mx430series-3.70-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mx430series-3.70-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]

and that should be the printer driver installed

_______________________________________________

to run the scanner component, Canon provide ScanGearMP    **[COLOR="#008000"]scangearmp-mx430series-1.90-1-deb.tar.gz[/COLOR]**

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100413801.html)

the install commands are the same as above

to run ScanGearMP, type

> [COLOR="#FF0000"]scangearmp[/COLOR] in a terminal

enjoy Ubuntu

---

### Post by hawkhock on 2013-03-21
Much thanks for the prompt replies. Haven't used Ubuntu for a few years and may need help with the printer/scanner install but feel more confident about making the switch. Will order the DVD so I have adequate back up for re-installing if necessary.

---

### Post by pdc on 2013-03-22
enjoy

if you post back on this thread if MX432 issues I have subscribed to the thread so should get notification

---

### Post by mörgæs on 2013-03-22
Changed the title to a more informative one.

---

### Post by hawkhock on 2013-03-23
Thank you for the excellent instructions. Printer is installed and working beautifully. Also know I can count on this forum

---

### Post by pdc on 2013-03-23
well done; enjoy ubuntu and enjoy linux!

---

