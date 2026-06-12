---
title: "[SOLVED] Lexmark Z815 experience report (failing)"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by mindhaq on 2005-10-15
Today I wanted to get my Lexmark Z815 USB scanner working. I tried to follow the instructions on [this page](http://cerqueira.org/software/z810/), but I can't get the procedure to finish properly :-(

Maybe someone in here has some clues or experiences to share.

What I did was:

Downloaded the RPM from Lexmark from here: [http://www.lexmark.com/US/products/info/linux/licenseZ800_rev2.html](http://www.lexmark.com/US/products/info/linux/licenseZ800_rev2.html)

Converted the rpm to a deb:
sudo alien z810llpddk-2.0-3.i386.rpm

Installed the deb:
sudo sudo dpkg -i z810llpddk_2.0-4_i386.deb

Downloaded the CUPS driver source from here: [http://cerqueira.org/software/z810/Z810CUPS-0.6.tar.gz](http://cerqueira.org/software/z810/Z810CUPS-0.6.tar.gz)

Extracted the source:
tar xzf Z810CUPS-0.6.tar.gz

Installed necessary packages for the build with Synaptic, as stated in the README contained in the archive (libcupsys2-dev) and "build-essentials" as I didn't have that before.

I compiled the binaries with a simple make. I got a few warnings (see below), but no errors:
```
g++  -I./ -c -g -Wall -O2 -funsigned-char cupsraster.cpp -o Objects/cupsraster.o
cupsraster.cpp: In member function »void CupsRaster::MirrorImage(unsigned char*, long int)«:
cupsraster.cpp:165: Warnung: Vergleich zwischen vorzeichenbehafteten und vorzeichenlosen Ganzzahlausdrücken
[ -d ../../bin ] || mkdir ../../bin
g++ -ldl -llexz810printjob -llxbshpep -lcups -lcupsimage -o ../../bin/rastertoz810 Objects/main.o Objects/z810filter.o Objects/cupsraster.o
/usr/bin/ld: warning: libstdc++.so.5, needed by /usr/lib/gcc/i486-linux-gnu/4.0.2/../../../../lib/liblxbshpep.so, may conflict with libstdc++.so.6

```

The I tried to installed the binaries with make install, but this was interrupted with an error:
```
Copying Lexmark Z810 files ...
Configuring system ...
Restarting CUPS ...
Adding Z810 printer queue ...
make: *** [install] Fehler 1

```

As I read the [FAQ]("http://cerqueira.org/software/z810/faq.html") before, I excpected this:

> **Q: I'm running "Ubuntu/Debian/Knoppix/other Debian-based distro" and I got an error in the installation after Restarting CUPS ...**
A: The install script was written for Fedora Core, sorry. The startup script in deb-distros has a different name, so the reload fails. Just run /etc/init.d/cupsys restart, followed by /usr/sbin/lpadmin -p Z810 -E -m Lexmark-Z810-lxz810cje-cups.ppd.gz -v z810:/dev/usb/lp0 and your installation will be complete.

Sadly, those instructions don't work. Restarting the service did, but the other command didn't, printing the following error message (with or withoud sudo):

```
lpadmin: add-printer (set device) failed: client-error-not-possible

```

Well, I don't fully understand what this command is suppossed to do. But I see a reference to /dev/usb/lp0. On my system, I do not have this entry; heck, I don't even have /dev/usb.
All my other USB devices (scanner, cardreader, MP3-stick) work fine, however.

I'd be glad to try every advice you have! I'm glad I made it that far, but as you see, I'm stuck now.

---

### Post by wwitthoff1 on 2006-04-25
having read around the net.  is the printer on and connected to your computer?

---

### Post by mindhaq on 2007-05-31
As I got messages concerning this printer, I'll post an update (came back to Ubuntu after one year).

This Wiki-Page [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ810) shows how to do it. I just printed a test page, and it works fine.

---

