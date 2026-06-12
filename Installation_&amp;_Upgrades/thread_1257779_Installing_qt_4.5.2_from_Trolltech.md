---
title: "Installing qt 4.5.2 from Trolltech"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by afhx on 2009-09-04
Problems trying to install qt4.5.2 from Trolltech. I have looked for previous queries but none answered my questions. I am trying to work through Blanchette and Summefield book on qt and C++/Output from configure( done in dir where I downloaded and unpacked). BASIC Xlib functionality failed!. You might need to modify the include and library search paths by editing QMAKE_INCID_X11 & QMAKE_LIBDIR_XX in /home/bbw/qt-x11-opensource-src -4.5.2/mkspecs/linux++. these entries don't appear and I have no clue what to put.
Output from make:
***No targets specified and no makefile found.
Output from make install -n
cd /src/tools/bootstrap/ & d /usr/bin/qmake/bootstrap .pro -unix -o Makefile
cannot find file: bootstrap. pro (it was there)
make***[/src/tools/bootstrap/Makefile] Error 2
Details of my operating system:
ubuntu 9.04
kernel 2.6.28-14-generic
gcc 4.3.3
I tried installing all packages via Synaptic mentioning qt but was unable to get pass the make stage when running programs.
I would appreciate any help.

---

### Post by tachyon4 on 2010-07-28
same problem.  any luck?

---

### Post by Vinnare on 2010-08-06
> **afhx said:**
> Problems trying to install qt4.5.2 from Trolltech. I have looked for previous queries but none answered my questions. I am trying to work through Blanchette and Summefield book on qt and C++/Output from configure( done in dir where I downloaded and unpacked). BASIC Xlib functionality failed!. You might need to modify the include and library search paths by editing QMAKE_INCID_X11 & QMAKE_LIBDIR_XX in /home/bbw/qt-x11-opensource-src -4.5.2/mkspecs/linux++. these entries don't appear and I have no clue what to put.
Output from make:
***No targets specified and no makefile found.
Output from make install -n
cd /src/tools/bootstrap/ & d /usr/bin/qmake/bootstrap  .pro -unix -o Makefile
cannot find file: bootstrap. pro (it was there)
make***[/src/tools/bootstrap/Makefile] Error 2
Details of my operating system:
ubuntu 9.04
kernel 2.6.28-14-generic
gcc 4.3.3
I tried installing all packages via Synaptic mentionung qt but was unable to get pass the make stage when running programs.
I would appreciate any help. I only have a dongle for internet access. My email account is via a library five miles away. I only allowed one hour per visit/

same problem here!!!
ne solutions?

---

### Post by afhx on 2010-08-18
I tried the same procedure with the latest version. No problems whatsover. To be precise 
I had no trouble installing qt-everywhere-opensource-src-4.6.2. Allow a couple of hours for compiling.

---

