---
title: "MP640 scanner LAN install 32bit"
date: 2010-06-27
forum: Hardware
---

### Post by vector on 2010-06-27
Hi all,
Successfully installed the Printer side of the MP640 using the forum posts.
[http://ubuntuforums.org/showthread.php?t=1313945&highlight=mp640+printer](http://ubuntuforums.org/showthread.php?t=1313945&highlight=mp640+printer)

But a little hesitant on the scanner side.
I downloaded the scangear driver according to the last posts but they dont say what to do with it.

I normally use sane and noticed the mention of upgrading sane to the new version using cvs but again im not up to speed on such things.

could some kind sole spell it out for me :)

Im running an uptodate Karmic 9.10.on a basic 32 bit machine.
the printer is installed using LAN cable.

---

### Post by IcarusR on 2010-06-27
To install scangear extract the archive, double click on it.
Open terminal & cd to the extracted directory & type install.sh this should install scangear.
Or double click on the common .deb file to install graphically, then the same with the other .deb.

---

### Post by vector on 2010-06-28
Ok I tried that
 sudo ./install.sh

==================================================

ScanGear MP Ver.1.40-1 for Linux
Copyright CANON INC. 2007-2009
All Rights Reserved.

==================================================
Error! Cannot specify package management system.

---

### Post by vector on 2010-06-29
ok I noticed a folder called packages and it had two debs in it I installed them with this.
sudo  dpkg -i scangearmp-mp640series_1.40-1_i386.deb
sudo  dpkg -i scangearmp-common_1.40-1_i386.deb

Which gives me a driver in Gimp.

Didnt work from zane but ill worry about that another day.

---

