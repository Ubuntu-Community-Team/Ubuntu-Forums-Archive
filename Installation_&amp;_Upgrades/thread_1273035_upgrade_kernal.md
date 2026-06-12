---
title: "upgrade kernal"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by FreezWay on 2009-09-22
I love being up to date. I want to get the new Linux 2.26.31 kernel, but i have no clue how. how do you update your kernal? I am using a AMD64 architecture (intel quad core FTW)

---

### Post by ibuclaw on 2009-09-22
There you go: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Although it expects you to generally know what you are doing...

---

### Post by FreezWay on 2009-09-23
ermmm... that 2.26.30.... 2.26.31 was released right?

---

### Post by ibuclaw on 2009-09-23
> It was last updated Mon 17 Aug 2009 16:38:00 UTC EST.
It may be updated during the next few weeks...

In the meantime, a watered down version:
```

sudo apt-get install build-essential bin86 kernel-package wget libncurses5-dev
wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.tar.bz2
tar -xvjf linux-2.6.31.tar.bz2
cd linux-2.6.31
cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
make-kpkg clean

```
To change the name of the kernel:
```
gedit Makefile
```
and make a change to the 4th line so it looks something like this: (use your own name scheme, of course)
```

VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 31
**EXTRAVERSION = -tinikernel**
NAME = Man-Eating Seals of Antiquity

```
To compile/build a debian package:
```
INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd kernel_image kernel_headers modules_image
```
Two deb files will be created in the directory above.

To install after it has finished.
```
sudo dpkg -i ../*.deb
```


I'm pretty sure someone will pop in though and give you a ppa link ... that might be easier and save you 40 minutes of compile time. :)

---

### Post by FreezWay on 2009-09-23
meh, i have time and quad core 64 bit... plus i'll be able to say i compiled it myself

---

### Post by darco on 2009-09-23
Or you could update your sources.list to point to the karmic repos and then d/l and install the .31 kernel. That method worked for me.....dont forget to change the source list back!

darco

---

