---
title: "Creative Audigy 2 ZS Notebook"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by RD1945 on 2007-02-03
I don't know if it is already posted on the Ubuntu forums (I didn't have the time to search), but I saw that a lot of people have problems with their Audigy 2 ZS Notebook. If the card is not working, try the following.

1) Download the latest alsa-driver, alsa-lib and alsa-utils packages from [www.alsa-project.org](www.alsa-project.org).
2) Install the alsa-driver first (just type ./configure --with-cards=emu10k1,(other cards in your pc) --with-oss=yes -> make -> make install).
3) Install the alsa-lib (./configure -> make -> make install).
4) Install the alsa-utils (./configure -> make -> make install).
5) Run alsaconf and select the Audigy card.
6) Run /etc/init.d/alsasound restart.

That's it... Now your Audigy should work!!!

I'm currently running Edgy, but I am sure it will work on dapper as well.

---

### Post by jsnelli2 on 2007-02-19
I'm fairly new to Linux, and I am trying to install my ZS Notebook, but I can't get past installing the drivers.  I have done everything that I have been able to find on here to do...but I can't get past it.  I have tried running both, sudo ./configure --with-cards=emu10k1 --with-oss=yes;make;make install and sudo ./configure --with-cards=emu10k1 --with-sequencer=yes;make;make install.  Both return this error.  I would appreciate any help you guys could give me!  Keep in mind, I'm new to Linux, but I'm loving it so far.  If I can get everything running right, I'm considering not dualbooting with Windows anymore...I'm running Edgy.  Thanks in advance



Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
ln: creating symbolic link `include/sound' to `../alsa-kernel/include': Permission denied
make: *** [include/sound/version.h] Error 1
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /usr/src/alsa/alsa-driver-1.0.14rc2/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
rm: cannot remove directory `/usr/include/sound': Permission denied
install: cannot change owner and/or group of `/usr/include/sound': Operation not permitted
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1

---

### Post by MyNameUhBorat on 2007-02-21
I've been running Ubuntu for a while now and I've had no problem with my Audigy 2 Zs. Except that I have to turn my Logitech Z-560 speakers practically all the way up just to get a volume that I like.

---

### Post by jsnelli2 on 2007-02-21
i just can't get the drivers compiled and installed...that's the error I keep getting...Talking about permissions...I run sudo and type the password, and it does quite a bit, but stops towards the end with that.

---

### Post by jsnelli2 on 2007-02-22
Well I got it working, Not sure what I did, seems like rebooting was all that I hadn't done...Because they worked unexpectantly..No complaining though. Thanks guys

---

### Post by RD1945 on 2007-02-25
When I install something I always use root account... (I'm getting tired of typing sudo every time)

---

### Post by e-ignite on 2007-03-24
Hi all,

I've been trying to install the alsa drivers for my Creative Audigy 2 ZS Notebook card.  However, following instructions both on this site and the alsa site itself, I keep getting the following error:

> checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

I've run the **modinfo soundcore** command and I get the following:
> filename:       /lib/modules/2.6.15-28-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-28-386 preempt 486 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92

Despite trying to include the option **--with-kernel=/lib/modules/2.6.15-28-386/kernel/sound/soundcore.ko** and **--with-kernel=/usr/src/linux**, I can't get past this error.  Unfortunately, web searches have been fruitless so far too!

Could anyone please try to explain what the problem may be and how I could possibly fix it?  I'm not an entire noob when it comes to Ubuntu, but I've not really installed or compiled too much from the Terminal.  I should say that I'm running Ubuntu Dapper Drake (6.06), and I'm trying to install the most recent alsa packages (at time of posting).

All advice appreciated! :)

---

