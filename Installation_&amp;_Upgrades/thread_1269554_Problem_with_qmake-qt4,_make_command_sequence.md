---
title: "Problem with qmake-qt4, make command sequence"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by myxomatosii on 2009-09-18
I've been getting errors installing a number of programs from source since the start but this is the first time I have no other option and really want toe software bad enough to take the extra step and ask for help on the forums.

I'm trying to install acetoneiso from the source and here's how it goes..

So the readme file says to

[I]a) You must have libqt4-dev and the standard gcc compiler (gcc,g++,make) installed.


b) open a terminal inside /src/ folder and type:

 [B]  qmake-qt4 (if it gives errors simply type "qmake" instead)
   make[/B]
   make install (must be run as root user)


c) it is now time to add your user to fuse group.
   open a terminal, login as root user and type:[/I]


I run through the qmake-qt4 with no errors but when I run make I get the error

myxo@myxopc:~/Desktop/acetoneiso_2.0.3/src$ make
/usr/bin/uic-qt4 ui/acetoneiso.ui -o build/ui_acetoneiso.h
make: /usr/bin/uic-qt4: Command not found
make: *** [build/ui_acetoneiso.h] Error 127
myxo@myxopc:~/Desktop/acetoneiso_2.0.3/src$ 

I've googled around for error 127 when using the make command and tried a number of fixes including installing extra software (without adding shady repositories) and have had no luck so far, perhaps someone can shed some light on this?

---

### Post by bulletxt on 2009-09-18
First thing: get latest 2.1.1 release at official website [http://www.acetoneteam.org](http://www.acetoneteam.org)

Then, install libqt4-dev and build-essential packages.


Then inside the acetoneiso folder type qmake-qt4 and then make (and then follow the rest of the readme).


You can also find an official deb of version 2.0.4 always at [http://www.acetoneteam.org](http://www.acetoneteam.org)

---

