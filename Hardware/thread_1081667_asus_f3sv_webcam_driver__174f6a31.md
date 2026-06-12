---
title: "asus f3sv webcam driver  174f:6a31"
date: 2009-02-26
forum: Hardware
---

### Post by didntpickaname on 2009-02-26
hello i'm new in ubuntu. I have problem with my webcam driver.
When:lolflag: i open camoroma it says "could not connect to video device (/dev/video0)

I've followed the instructions in [http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html](http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html)

However it doesnt help me...

when i try to use:

make -f Makefile-syntekdriver install

on the terminal. It says:

make: Makefile-syntekdriver: No such file or directory
make: *** No rule to make target `Makefile-syntekdriver'.  Stop.

I m working on /syntek/driver

my driver's code is 174f:6a31 which is on the list and i can see it with lsusb

Bus 003 Device 002: ID 174f:6a31 Syntek Web Cam - Asus A8J, F3S, F5R, VX2S, V1S

Anyone help please

---

### Post by didntpickaname on 2009-02-27
please help!!!

---

### Post by blablabla212 on 2009-08-07
Kubuntu 3 minutes method: 1-download stk11xx-1.4.0.tar.gz 2-$mkdir syntek 3-untar stk11xx-1.4.0.tar.gz in @syntek@ 4-$cd syntek 5-paste file in @syntek@ @Makefile-syntekdriver@:  ifneq ($(KERNELRELEASE),)     obj-m    := stk11xx.o     stk11xx-objs := stk11xx-bayer.c  stk11xx-buf.c  stk11xx-dev.c  stk11xx-sysfs.c  stk11xx-usb.c  stk11xx-v4l.c else     KDIR    := /lib/modules/$(shell uname -r)/build     PWD        := $(shell pwd)     VERSION = 0.42     DISTFILES = stk11xx.h stk11xx-bayer.c  stk11xx-buf.c  stk11xx-dev.c  stk11xx-sysfs.c  stk11xx-usb.c  stk11xx-v4l.c Makefile README COPYING INSTALL     DISTNAME = stk11xx-$(VERSION)  all:     $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules  clean:     rm -f *.o *.ko .*.o.d *~ .stk11xx*.cmd *.mod.c     rm -rf $(DISTNAME) .tmp_versions     rm -f $(DISTNAME).tar.bz2  install:     mkdir -p $(DESTDIR)/lib/modules/$(shell uname -r)/kernel/drivers/usb/media     install -m 644 -o 0 -g 0 stk11xx.ko $(DESTDIR)/lib/modules/$(shell uname -r)/kernel/drivers/usb/media     depmod -a  dist:     [ -d $(DISTNAME) ] && rm -rf $(DISTNAME) || true     mkdir $(DISTNAME)     cp -aR $(DISTFILES) $(DISTNAME)     tar cjvf $(DISTNAME).tar.bz2 $(DISTNAME)     rm -rf $(DISTNAME) endif   6-$make -f Makefile-syntekdriver 7-$sudo make -f Makefile-syntekdriver install 8-$sudo modprobe stk11xx 9-$ dmesg |tail 10-$ sudo lsusb -v|grep -A 8 Syntek  That's all

---

### Post by gnimsh on 2009-10-31
Well Didntpickaname, i think the formatting of the only reply made it almost impossible to be of any use...

First, download both driver packages: [http://sourceforge.net/projects/syntekdriver/files/syntekdriver/Release%202.1.0/stk11xx-2.1.0.tar.gz/download](http://sourceforge.net/projects/syntekdriver/files/syntekdriver/Release%202.1.0/stk11xx-2.1.0.tar.gz/download) and [http://sourceforge.net/projects/syntekdriver/files/syntekdriver/stk11xx-1.4.0/stk11xx-1.4.0.tar.gz/download](http://sourceforge.net/projects/syntekdriver/files/syntekdriver/stk11xx-1.4.0/stk11xx-1.4.0.tar.gz/download) 

Make sure to leave the version name on the folders once you extract them.  Find the file named stk11xx-v4l.c in v 1.4.0 and copy it, then go to 2.1.0 and paste that file to overwrite the one in the newer package (there is an error in the code that keeps the new package from compiling correctly, and this solves it).  


Now you need a terminal.  Keep it open for the remainder of this tutorial. Run this command to make sure you have everything you need to build the driver: sudo apt-get install linux-headers-`uname -r`

I also recommend using a special makefile, as I've never had luck with the included one. Once you have the old file copied into 2.1.0, type cd stk11xx-2.1.0 (or stk11xx-2 and hit tab for autocomplete) and then paste either of these lines: wget [http://bookeldor-net.info/merdier/Makefile-syntekdriver](http://bookeldor-net.info/merdier/Makefile-syntekdriver) or this alternate copy: [http://www.katicomp.co.nz/files/binary/Makefile-syntekdriver](http://www.katicomp.co.nz/files/binary/Makefile-syntekdriver)  That will download the special makefile to the folder you are in.

Now type: make -f Makefile- and hit tab to autocomplete with the special makefile. Hit enter.  This should all hopefully complete without any errors.  Once that has finished, type this: sudo make -f Makefile-syntekdriver install

This should also hopefully work with no errors.  Then you can type: sudo modprobe stk11xx and your webcam should light up (if it has an LED). Don't worry if it doesn't, mine sometimes does not.  

Last step: type sudo addgroup $USER video
This gives your user access to the webcam.  Then restart.  In my experience this works with skype and some other programs, but not all (like cheese).

I pulled all this info from here: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/269123](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/269123) and here: [http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html](http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html) Good luck.

---

