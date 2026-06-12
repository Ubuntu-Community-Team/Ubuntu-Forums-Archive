---
title: "MAKE command not found"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by bruce147 on 2005-11-23
bruce@ubuntu:/usr/src/rfswitch-0.1$ make
bash: make: command not 

I can not get my wireless to work on my Averatec 5110h. It has a hardware switch to turn on the wireless broadcast. This has lead  me to 
[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)
By my reading, this site suggests I need to install some rfswitch module for my laptop.

While trying to do this, I need  the make command. But as my terminal shows, it is not found. 

Where is the make command????? 


This shows that ubuntu 5.1 has found my centrino card:
localhost kernel [4294706.296000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
localhost kernel [4294707.224000] eth1: Radio is disabled by RF switch.

---

### Post by aysiu on 2005-11-23
I think you need to ```
sudo apt-get install build-essential
``` Follow the instructions in my sig first, though.

---

### Post by bruce147 on 2005-11-25
STILL having trouble with the make command. I followed the advice of Aysiu (thankyou!) and his link on updating.
However, I get the following error after sudo make
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.

Here is a review of what I have done (in addition to Aysiu's recommendations). Because I thought this problem might stem from not having the proper files installed for compiling, I followed "HOWTO: Kernel Compilation for Newbies."
sudo apt-get install kernel-package
sudo apt-get install gcc (this will install gcc-4.0 for kernel 2.6.13 or superior)
sudo apt-get install gcc-3.4
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev
cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
##sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux ##I didn't do this. I did the following instead:
sudo ln -s /lib/modules/2.6.12-10-386/build /usr/src/linux-source-2.6.12 ##Edit: Arguments reversed!!! See my reply below
/usr/src$ cd rfswitch-0.1
/usr/src/rfswitch-0.1$ sudo make clean
	rm -f *.mod.c *.mod *.o *.ko .*.cmd .*.flags
	rm -rf /usr/src/rfswitch-0.1/tmp
/usr/src/rfswitch-0.1$ sudo make
	make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/usr/src/rfswitch-0.1 MODVERDIR=/usr/src/rfswitch-0.1 		modules
	make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
	make: *** [modules] Error 2

BUT, when I also get the following, which says "/lib/modules/2.6.12-10-386/build" DOES exist.
/usr/src/rfswitch-0.1$ sudo ln -s /lib/modules/2.6.12-10-386/build /usr/src/linux-source-2.6.12
ln: `/usr/src/linux-source-2.6.12/build': File exists

Why can't I run MAKE?

Here is a section of the makefile which might be important. This shows why I changed the ln -s step.

# KSRC should be set to the path to your sources
# modules are installed into KMISC
KVER  := $(shell uname -r)
KSRC := /lib/modules/$(KVER)/build
KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/

Why can't I run MAKE?

---

### Post by bruce147 on 2005-11-25
I have made a big step forward. There is an error in the steps of my previous post. The ln -s command has the arguments reversed. That is why my make command was failing. In the work above I had been following the blog [http://www.flamingspork.com/blog/?p=338](http://www.flamingspork.com/blog/?p=338)
which had notes on installing. That blog also had the arguments reversed and that is how I got into trouble. 
From the man pages
NAME
       link - call the link function to create a link to a file

SYNOPSIS
       link FILE1 FILE2
       link OPTION

DESCRIPTION
       Call  the  link  function  to  create a link named FILE2 to an existing
       FILE1.

Here at last is the fruit of my labors:
sudo ln -s /usr/src/linux-source-2.6.12 /lib/modules/2.6.12-10-386/build
make clean
	rm -f *.mod.c *.mod *.o *.ko .*.cmd .*.flags
	rm -rf /usr/src/rfswitch-0.1/tmp
make
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/usr/src/rfswitch-0.1 MODVERDIR=/usr/src/rfswitch-0.1 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /usr/src/rfswitch-0.1/av5100.o
  CC [M]  /usr/src/rfswitch-0.1/pbe5.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/rfswitch-0.1/av5100.mod.o
  LD [M]  /usr/src/rfswitch-0.1/av5100.ko
  CC      /usr/src/rfswitch-0.1/pbe5.mod.o
  LD [M]  /usr/src/rfswitch-0.1/pbe5.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'

I will be working on the next step of this process. I will gladly take any advice!

---

