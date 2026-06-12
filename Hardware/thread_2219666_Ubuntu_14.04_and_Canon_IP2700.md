---
title: "Ubuntu 14.04 and Canon IP2700"
date: 2014-04-25
forum: Hardware
---

### Post by ndDxpGY on 2014-04-25
Hello, I have installed Ubuntu 14.04 64 bits, everything is great.

Well, except for the installation of a printer Canon IP2700, I already have the drivers from Canon, but when I run "./install.sh", there's a dependency error for a libtiff4 library/file/whatever, and it says that this libtiff4 is uninstallable.
 
Then I tried to install the libtiff5 thinking it has to have retro compatibility, but it's already installed. I have searched the forum and tried some of the answers involving external repositories and it's always the same, the driver can't be installed.

Right now I don't know what to do, I'll appreciate any help regarding this problem.


BTW, the printer it's recognized by the system in lsusb.

---

### Post by pdc on 2014-04-25
gosh; libtiff4 has been a frequent dependency for such printer drivers; .........sounds like you have really checked it all out so > [COLOR="#FF0000"]sudo apt-get install libtiff4[/COLOR] doesn't work?

The gutenprint driver [http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php) seems to support ip2700 .............I wonder will your version of ubuntu discover your printer and offer a gutenprint driver?

The other thing you can try is turboprint as a trial: they offer a free trial download so you can at least get printing; while researching more if needed ..............

(You have a 64bit ubuntu you say; and the ip2700 came out in the days when there were only 32bit systems........so I don't think the canon driver goes well with a 64bit system.......... more senior printers like yours need heritage systems sometimes: drivers for current Canon printers have both 32bit and 64bit packages in them; I looked at the ip2700 and it is only 32bit ...)

---

### Post by ndDxpGY on 2014-04-25
AHHH, forget it, hey pdc, thanks man.

It has been many years since the last time I used a Linux, so maybe I'm too accustomed to an old way of work.

All I had to do was to go to the printer option in the general settings, and the system automatically recognized and installed the driver, almost plug and play, I'm very impressed actually.

---

### Post by pdc on 2014-04-25
great!! enjoy

---

