---
title: "help installing printer"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by bionnaki on 2005-08-28
hello. 

here is my printer: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_P1115](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_P1115)

and here are the instructions for installing the driver: [http://hpinkjet.sourceforge.net/install_hpijs.php](http://hpinkjet.sourceforge.net/install_hpijs.php)

following the instructions:

> # tar xzvf hpijs-1.x.tar.gz
# cd hpijs-1.x
# ./configure
# make
Log in as root on your machine
# make install

I receive this error:

> root@ubuntu:~# cd /home/bill/hpijs-2.1.4
root@ubuntu:~/hpijs-2.1.4# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yeschecking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for jpeg_set_defaults in -ljpeg... no
configure: error: "cannot find libjpeg support"
root@ubuntu:~/hpijs-2.1.4# make
make: *** No targets specified and no makefile found.  Stop.


Any ideas?
Thanks

---

### Post by bionnaki on 2005-08-28
oh, and when I hpijs -h, I receive this:

> root@ubuntu:~/hpijs-2.1.4# hpijs -h

Hewlett-Packard Co. Inkjet Server 2.1.2
Copyright (c) 2001-2004, Hewlett-Packard Co.

does this mean the driver is installed?

When I try to go to [http://localhost:631](http://localhost:631) - the page never loads...

---

### Post by mbjbdc on 2005-08-28
you can installl hplis with synaptic
then go to system/administration and add printer
that how installed my hp

---

### Post by bionnaki on 2005-08-28
wow - that worked. I guess I was doing it the hard way. thanks!

---

