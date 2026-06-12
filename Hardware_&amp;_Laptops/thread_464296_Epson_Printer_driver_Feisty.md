---
title: "Epson Printer driver Feisty"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by westlye on 2007-06-04
Hello,
when I upgraded my Kubuntu to Feisty Fawn I lost my Epson Inkjet Photo R220 driver.
Surfing the web i found that:
[http://www.avasys.jp/english/linux_e/dl_ink.html](http://www.avasys.jp/english/linux_e/dl_ink.html)
has drivers, I downloaded the RPM version for Debian, then I used the utility alien
to create a .deb installation file.
Alien is a program that converts between the rpm, dpkg, stampede slp, and slackware tgz file formats to .deb and can be downloaded from: [http://kitenet.net/~joey/code/alien/](http://kitenet.net/~joey/code/alien/)

then a at a console type the command: sudo  dpkg -i filename.deb 
Viola, now the printer (among other missing Epson printers) showed up in the printer installation guide.

Hope this will help others that have problem after upgrade.
Regards//LW

---

