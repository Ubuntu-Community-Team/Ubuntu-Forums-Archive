---
title: "kernel make menuconfig: needs ncurses?"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by edderd on 2009-03-16
To build a kernel using make menuconfig, which ncurses package am I missing? The error indicates I'm missing ncurses-devel, but it's not available according to apt-get...

I have (from dpkg -S ncurses):
libncurses5: /usr/share/doc/libncurses5/README.Debian
ncurses-bin: /usr/share/doc/ncurses-bin
libncursesw5: /usr/share/doc/libncursesw5/changelog.Debian.gz
ncurses-base: /usr/share/doc/ncurses-base
libncurses5: /usr/share/doc/libncurses5

I'd like to build the Linux kernel using make menuconfig, but it fails with 

root@falcon:/usr/src/linux-2.6.28.7# make menuconfig
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[1]: *** [scripts/kconfig/dochecklxdialog] Error 1
make: *** [menuconfig] Error 2

I downloaded linux-2.6.28.7. 

It's been awhile since I built a kernel. What am I missing?

---

### Post by khelben1979 on 2009-03-16
Maybe [this guide]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html") can help you out?

---

### Post by bettlebrox on 2009-03-16
Hi edderd,

You need the development package libncurses5-dev:
[INDENT]sudo apt-get install libncurses5-dev[/INDENT]

---

### Post by edderd on 2009-03-16
> **bettlebrox said:**
> Hi edderd,

You need the development package libncurses5-dev:
[INDENT]sudo apt-get install libncurses5-dev[/INDENT]

that's what I needed to know. Thanks!

---

### Post by kaineos on 2010-06-21
Thank you.

---

### Post by dino99 on 2010-06-21
you can use one of the latest kernel built into the trusted ppa on launchpad: [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

---

### Post by MonkeyZazu on 2010-12-01
> **bettlebrox said:**
> Hi edderd,

You need the development package libncurses5-dev:
[INDENT]sudo apt-get install libncurses5-dev[/INDENT]

this also helped me, thank you

---

### Post by IceMetal on 2011-03-16
> **bettlebrox said:**
> Hi edderd,

You need the development package libncurses5-dev:[INDENT]sudo apt-get install libncurses5-dev[/INDENT]


This help me so much if we ever met I'll buy a drink!!!!:popcorn:

---

### Post by snarf77 on 2011-03-29
Same for me....

many thnks for the trick !!

---

### Post by sivakumarar on 2011-04-10
Thanks a lot it helped me.:)

---

### Post by mitalpritmani on 2011-10-07
> **bettlebrox said:**
> Hi edderd,

You need the development package libncurses5-dev:
[INDENT]sudo apt-get install libncurses5-dev[/INDENT]


Hey bettlebrox, Thnx.. :) It worked !!!

---

### Post by OsOsOs on 2011-10-22
I'm having the same problem. But after checking 

sudo apt-get install libncurses5-dev

it still gives "Couldn't find package libncurses5-dev"

---

### Post by iron_guitarist1987 on 2011-10-26
I used 
sudo apt-get install libncurses5-dev

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

And it still says that I require ncurses

---

### Post by gaby81 on 2012-01-08
Worked for me. Thanks

---

### Post by gaby81 on 2012-01-08
> **iron_guitarist1987 said:**
> I used 
sudo apt-get install libncurses5-dev

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```And it still says that I require ncurses

Try to reinstall those packages

---

### Post by agritool on 2012-01-14
> **bettlebrox said:**
> Hi edderd,

You need the development package libncurses5-dev:[INDENT]sudo apt-get install libncurses5-dev[/INDENT]

thanks, good information for me :D

---

### Post by reggler on 2012-04-18
> **bettlebrox said:**
> Hi edderd,

You need the development package libncurses5-dev:
[INDENT]sudo apt-get install libncurses5-dev[/INDENT]

Also helped me! Thanks! :)

---

### Post by achillesshiva on 2012-08-06
Thanks a lot.. This is what I needed. :)

---

### Post by LinuxRoad on 2012-08-20
I also have the same question:
 
> **iron_guitarist1987 said:**
> I used 
sudo apt-get install libncurses5-dev
 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```
 
And it still says that I require ncurses

---

