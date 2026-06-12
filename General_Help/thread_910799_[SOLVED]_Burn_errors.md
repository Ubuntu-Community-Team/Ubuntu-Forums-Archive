---
title: "[SOLVED] Burn errors?"
date: 2008-09-04
forum: General Help
---

### Post by Yezinki on 2008-09-04
Hi there......neither k3b or brasero would burn a blank new Verbatim DVD+RW........preformatting errors........why wouldn't my DVD-RAM drive accept Linux softwares..........it burns windows softwares awesome........all types?

---

### Post by Yezinki on 2008-09-04
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- unimplemented command-line option for this media.
- you have the option to re-run /usr/bin/dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -force=full /dev/scd0 


The errors I get.

Thanks!

---

### Post by Yezinki on 2008-09-04
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-846S F200 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
Unknown

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Embarrassed LOAD TRAY failed with SK=5h/ASC=24h/ACQ=00h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:672402 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m

---

### Post by Yezinki on 2008-09-04
Have a look using genomebaker.

---

### Post by editrix on 2008-09-06
This is a well-known bug: #149076.

You might want to check the last page of the sticky: Known Hardy bugs and workarounds. Or my post: How to burn a CD (and DVD) despite bug #149076
[http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)

---

### Post by Yezinki on 2008-09-06
Thanks again,

I keep getting a message at the last stage i.e Write file Image to burn........." Disc Needs Formatting".......its a blank new media but still get this error repeatedly even after it does a format?

Hoping to hear from you GENIUS!!

---

### Post by Yezinki on 2008-09-06
> **editrix said:**
> This is a well-known bug: #149076.

You might want to check the last page of the sticky: Known Hardy bugs and workarounds. Or my post: How to burn a CD (and DVD) despite bug #149076
[http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700)

[SIZE="4"][B]You are the Best of the BEST till now I have encountered!!

Wish you could guide me after 18 years with windows & 2 weeks of Linux.

An asset to the Ubuntu Forums...& King of Ubuntu!![/B][/SIZE]

---

