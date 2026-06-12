---
title: "driver for pen on compaq tablet tc-1000"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by lewisdw on 2006-09-23
I'm trying to install the driver for the pen on a compaq tc-1000 (tablet).  I've installed kubuntu 6.06 (which is working great except for the pen).  I found instructions at [http://64.233.167.104/search?q=cache:W_fpyG5IdMYJ:bigsniff.no-ip.com/blog/%3Fp%3D8+ubuntu+fpi2002&hl=en&gl=us&ct=clnk&cd=5&client=firefox](http://64.233.167.104/search?q=cache:W_fpyG5IdMYJ:bigsniff.no-ip.com/blog/%3Fp%3D8+ubuntu+fpi2002&hl=en&gl=us&ct=clnk&cd=5&client=firefox).
I've followed those, and get to the first make, and it fails:

$ sudo apt-get install gcc
$ sudo apt-get install gcc-3.4
$ sudo apt-get install linux-headers-2.6.12-9-386 (modify this for your kernel version)
$ sudo apt-get install setserial
$ sudo wget [http://groundstate.ca/files/fpi2002-0.5.tar.gz](http://groundstate.ca/files/fpi2002-0.5.tar.gz)
$ sudo tar -xzf fpi2002-0.5.tar.gz
$ sudo cd fpi2002-.0.5/
$ sudo mv Makefile Makefile-2.4 < - backup make file for kernel 2.4
$ sudo mv Makefile-2.6 Makefile
$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/wayne/temp/fpi2002-0.5 modules
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386/build'
make: *** [fpi2002.ko] Error 2

Any help is appreciated.

---

