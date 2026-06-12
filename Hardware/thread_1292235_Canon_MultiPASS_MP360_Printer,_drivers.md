---
title: "Canon MultiPASS MP360 Printer, drivers?"
date: 2009-10-15
forum: Hardware
---

### Post by DougieFresh4U on 2009-10-15
I know the printer is old. Canon MultiPASS MP360
I did a search and was presented with an older thread, outdated.
I really don't know what driver as it doesn't list the EXACT numbers in the list when installing. I have chosen  a few of the drivers and when printing, it is only using the top left quarter of the paper. . If you need more clarification,please ask me.
Also, just a side note - I booted my Windows 7 partition and hooked the printer and it found it and got the driver and put all in great working order, scanner and all.
Thanks

---

### Post by andrewabc on 2009-11-02
Using driver S600 works for this printer.

Scanning is another problem as in past I've had to compile driver for some reason even though xsane detects it.

I'll be copy/pasting my compiled scanner driver from 9.04 install to 9.10 install. If it works, I could upload it to you.

---

### Post by DougieFresh4U on 2009-11-02
> **andrewabc said:**
> Using driver S600 works for this printer.

Scanning is another problem as in past I've had to compile driver for some reason even though xsane detects it.

I'll be copy/pasting my compiled scanner driver from 9.04 install to 9.10 install. If it works, I could upload it to you.

Thank you :p

---

### Post by andrewabc on 2009-11-19
To get scanning working in canon mp360:

I got my mp360 to start scanning. Had to do same thing I've done in previous releases.

Download
[http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/)
version 0.13.1
Put it in your /home folder, extract which will create a folder. 

Make sure you have package build-essential installed.

Open terminal, change directory to the mp150-0.13.1 folder type
./configure
make
sudo make install

The ./configure did not work for me, but make and sudo make install did. It creates a new file libsane-pixma.so Copy it to your /home directory (restart terminal).
Type
# mv /usr/lib/sane/libsane-pixma.so.1.0.20 /usr/lib/sane/libsane-pixma.so.1.0.20.old
# cp libsane-pixma.so /usr/lib/sane/libsane-pixma.so.1.0.20

Sources to figuring it out:
[http://mp610.blogspot.com/2007/11/new-sane-scanner-driver-for-canon-mp610.html](http://mp610.blogspot.com/2007/11/new-sane-scanner-driver-for-canon-mp610.html)
[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)
[http://forums.linuxmint.com/viewtopic.php?f=49&t=8813](http://forums.linuxmint.com/viewtopic.php?f=49&t=8813)

---

### Post by Julientroploin on 2011-11-01
Hello,

My SmartBase MP360 was working fine (B&W and color) on 11.04 with the BJC-8200 driver but on a fresh 11.10 install, i saw a MP360 driver was proposed by the system but it ontly worked in B&W. :(

BJC-8200 driver doesn't work any more.

Have someone succed using this printer on 11.10 ?

---

