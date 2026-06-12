---
title: "Installing RocketRaid 2320 drivers"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by Syzzer on 2006-07-12
Today, I got my RAID controller from the mailman, bat i'm having problems getting it installed ...

I downloaded the newest drivers from [http://www.highpoint-tech.com/](http://www.highpoint-tech.com/), to be specific:
[http://www.highpoint-tech.com/BIOS%20+%20Driver/rr2320/Linux/rr232x-linux-src-1.02-060328.tar.gz](http://www.highpoint-tech.com/BIOS%20+%20Driver/rr2320/Linux/rr232x-linux-src-1.02-060328.tar.gz)

Reading the manual it tells me:
> 
- For Linux kernel 2.6 -
     
     On most distributions based on kernel 2.6, an exploded source tree is not
     required to build a driver against the currently in-use kernel. As long
     as the system has kernel headers setup under /lib/modules/`uname -r`/build,
     you can simply run "make" to build the driver.

     If you want to build the driver against a custom kernel source, you must
     setup the kernel source manually and run "make" under kernel source tree
     to setup kernel headers.

So I ran 'make', but am getting the following errors:
> syzzer@syzzer-server:~/rr232x-linux-src-1.02/product/rr232x/linux$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-amd64-server'
  CC [M]  /home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.o
/home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.c: In function ârefresh_sd_flagsâ:
/home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.c:288: warning: implicit declaration of function âmutex_lockâ
/home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.c:288: error: âstruct inodeâ has no member named âi_mutexâ
/home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.c:294: warning: implicit declaration of function âmutex_unlockâ
/home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.c:294: error: âstruct inodeâ has no member named âi_mutexâ
make[2]: *** [/home/syzzer/rr232x-linux-src-1.02/osm/linux/os_linux.o] Error 1
make[1]: *** [_module_/home/syzzer/rr232x-linux-src-1.02/product/rr232x/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-amd64-server'
make: *** [rr232x.ko] Error 2

I've googled for the errors, but could not find anything usefull...

Please post anything you think that might help me into the right direction!

---

### Post by Edwin van Eggelen on 2006-07-15
I had the exact same problem. 
As far as I could see it is a problem in the driver. I checks for a kernel version. Depending on the version it uses a mutex instead of semaphores. According to their source code they assume that kernel version 2.6.15 and higher supports mutexes. 
I expect that kernel version higher than 2.6.16 supports them. At least the your and mine ubuntu kernel does not support the mutex function. 

Therefore I edited the os_linux.c in such a way that the driver does not use the mutexes and uses the “old” semaphores. Look for the define that checks the kernel version around line 288. You only need to edit 2 or 3 lines of code. 

This seems to work O.K. on my machine. The driver works O.K. now.

Hope this helps 
  Edwin

---

### Post by kiddyfurby on 2006-07-15
may i ask a few question?
do u install / and /boot onto the raid?
how do i install ubuntu when build-in support is unavailable?

i have rocketraid 1640, and i compiled the driver successfully
how do i install ubuntu then?

thanks in advance!

---

### Post by hkgonra on 2006-10-02
I would love to know how to do this as well. I have a RocketRaid 1820 and Rocket Raid 2220 card. I would like to get both of them up and running with Ubuntu but I am totally clueless as to how to get that done.

---

### Post by dootch on 2006-11-15
> **Edwin van Eggelen said:**
> I had the exact same problem. 
As far as I could see it is a problem in the driver. I checks for a kernel version. Depending on the version it uses a mutex instead of semaphores. According to their source code they assume that kernel version 2.6.15 and higher supports mutexes. 
I expect that kernel version higher than 2.6.16 supports them. At least the your and mine ubuntu kernel does not support the mutex function. 

Therefore I edited the os_linux.c in such a way that the driver does not use the mutexes and uses the “old” semaphores. Look for the define that checks the kernel version around line 288. You only need to edit 2 or 3 lines of code. 

This seems to work O.K. on my machine. The driver works O.K. now.

Hope this helps 
  Edwin

I am having the same problem with the 2220 card where may I find the os_linux.c file and what changes are to be made? Please

---

### Post by jzlharvey on 2007-08-31
> **hkgonra said:**
> I would love to know how to do this as well. I have a RocketRaid 1820 and Rocket Raid 2220 card. I would like to get both of them up and running with Ubuntu but I am totally clueless as to how to get that done.

I would love to see a how-to on the Rocket Raid 2220.  I am looking to get one and setup an array but dont want to dive in without assurance that everything will work as planned.

---

### Post by h0ax on 2007-12-31
Edwin, pls post that code you modified?
I can't seem to get this to work right.
Trying Ubuntu 7.1 RocketRaid 2220

---

