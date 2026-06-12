---
title: "Epson c1100N laser printer &amp; Breezy"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by bogl on 2005-12-18
I have an Epson Aculaser C1100N (network version) directly connected into a router.  I have tried following Epson's advice: use the EPSON PM-740C option in cups and IPP.  The data light flashes whenever I try to print a test page, but nothing else happens.

Can anyone shed any light on this one??

Thanks,

bogl

---

### Post by bogl on 2005-12-20
Solved! For the record...

Ensure you have "gcc", "make", "makedepend" and "libcupsys2-dev" installed via Synaptic.

Get the driver tar from [http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html), called Epson-ALC1100-filter-1.0.tar.gz

unpack, ./configure, make, sudo make install

Then (V V IMPORTANT!)

sudo /etc/init.d/cupsys restart

In System > Administration > Printing, choose "AL-C1100"

Bob's your uncle (metaphorically speaking).

Three evenings of fiddling over.

---

### Post by wimek on 2006-07-15
I encountered the same problem: your solution works! Thanks a lot :-)

Wimek

---

### Post by foucher on 2006-10-24
hello !
excuse my english, i'm french and bad in you language.

i've the same problem, but when i write "make" in my terminal, i've this message :
sfoucher@M0102:~/Desktop$ ./configure
bash: ./configure: Aucun fichier ou répertoire de ce type
sfoucher@M0102:~/Desktop$ cd Epson-ALC1100-filter-1.0
sfoucher@M0102:~/Desktop/Epson-ALC1100-filter-1.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) mawk
checking for rpmbuild... no
./configure: line 2792: rpm: command not found
checking for cups-config... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
[B]sfoucher@M0102:~/Desktop/Epson-ALC1100-filter-1.0$ make
make  all-am
make[1]: entrant dans le répertoire « /home/sfoucher/Desktop/Epson-ALC1100-filter-1.0 »
make[1]: quittant le répertoire « /home/sfoucher/Desktop/Epson-ALC1100-filter-1.0 »
sfoucher@M0102:~/Desktop/Epson-ALC1100-filter-1.0$[/B]

i don't know why make didn't pass, have yout got solution ?

thank à lot.

---

### Post by Davidp on 2007-02-25
> **bogl said:**
> Solved! For the record...

Ensure you have "gcc", "make", "makedepend" and "libcupsys2-dev" installed via Synaptic.

Get the driver tar from [http://www.avasys.jp/english/linux_e/dl_laser.html](http://www.avasys.jp/english/linux_e/dl_laser.html), called Epson-ALC1100-filter-1.0.tar.gz

unpack, ./configure, make, sudo make install

Then (V V IMPORTANT!)

sudo /etc/init.d/cupsys restart

In System > Administration > Printing, choose "AL-C1100"

Bob's your uncle (metaphorically speaking).

Three evenings of fiddling over.



Brilliant works 100% I have this printer networked via SAMBA, struggled for week to get it going, took 5 minutes using the above.

---

### Post by bogl on 2007-05-01
And for the record, works well in Feisty too - but note the Epson package is now Epson-ALC1100-filter-1.2.tar.gz.

Otherwise, idential installation.

---

### Post by ]Nbx*cmD[ on 2007-05-18
i just love you

---

### Post by jd65pl on 2007-06-01
Thanks for the solution it was a great help!:D

---

### Post by Marc Higgins on 2007-11-11
out of interest has anyone had any success with getting this to work on Gutsy?

This is what did work for me

[http://ubuntuforums.org/showthread.php?p=3751422#post3751422](http://ubuntuforums.org/showthread.php?p=3751422#post3751422)

---

### Post by narcisgarcia on 2007-12-19
The procedure has been a solution for me too (with an USB local connection).
But now my computer sends every page as a color page.

If I print an only black&white document, and/or specify the "grayscale" option, the printer prints it as color pages, and doesn't run at the b&w speed.

Any idea?

---

### Post by Marc Higgins on 2007-12-23
> **narcisgarcia said:**
> The procedure has been a solution for me too (with an USB local connection).
But now my computer sends every page as a color page.

If I print an only black&white document, and/or specify the "grayscale" option, the printer prints it as color pages, and doesn't run at the b&w speed.

Any idea?

That is really strange, I just tested this on several machines here & it prints what ever it is told, colour or grayscale & the B&W prints are at the faster speed. 

Just out of interest what is your connection (parallel, usb, tcp/ip), what is your arch (i386/64), what is your environment (gnome/kde/xfce) & is this the same for all applications?

---

