---
title: "Quickcam problems!"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by SVen2000 on 2004-12-12
I tried to install qc-usb package .... lots of problems.

Has anyone got it ?

---

### Post by Soulman on 2004-12-14
I have mine working under Ubuntu.  Yet, I compiled my kernel as that allows me to have an easier time with installing outside drivers and also makes my system a lot quicker.  Anyway this is how I handle it, other than that though the install of the quickcam driver is very easy with a custom kernel.  Though if not then look through the forum to install the necessary packages using your current default kernel for compiling the quickcam driver.  Good luck!

---

### Post by firfurcio on 2004-12-16
[QUOTE=SVen2000]I tried to install qc-usb package .... lots of problems.

Has anyone got it ?[/QUOTE]

I have a Quickcam messenger and this driver don't  worked for me. 
I've searched a little and i found this:
[http://www.ketelhot.net/qcm/qc-usb-2004115.tar.gz](http://www.ketelhot.net/qcm/qc-usb-2004115.tar.gz)
And it worked for me.
Wish this could help you.

PD:Sorry for my really bad english. ;P

---

### Post by xavi on 2005-01-18
[QUOTE=firfurcio]I have a Quickcam messenger and this driver don't  worked for me. 
I've searched a little and i found this:
[http://www.ketelhot.net/qcm/qc-usb-2004115.tar.gz](http://www.ketelhot.net/qcm/qc-usb-2004115.tar.gz)
And it worked for me.
Wish this could help you.

PD:Sorry for my really bad english. ;P[/QUOTE]
 I cannot get my Quickcam messenger to work, following the instructions under the file (readme or readme.messenger). 

I downloaded the file, decompressed it, go into qc-usb dir, and run "make all", but got a long list of errors, and didn't make the "quickcam.ko" file as expected, according to [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/).

What do I need (I'm very newby) to compile the kernel myself, so that compiling the driver is a much easier process?

I'm using ubuntu warty with kernel 2.6.8.1. 

By the way, is there any easier way to compile the module with "apt-build" application?
[http://www.debtoo.org/apt-build.html](http://www.debtoo.org/apt-build.html)

---

### Post by Yukino on 2005-01-29
[QUOTE=xavi]I cannot get my Quickcam messenger to work, following the instructions under the file (readme or readme.messenger). 

I downloaded the file, decompressed it, go into qc-usb dir, and run "make all", but got a long list of errors, and didn't make the "quickcam.ko" file as expected, according to [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/).
[/QUOTE]

I downloaded the file too and I got (I suposse) the same long list of errors. I made an symbolic link to the kernel header files:

$ mkdir  /lib/modules/2.6.8.1-3-386/build/include
$ ln -s /usr/include/linux/ /lib/modules/2.6.8.1-3-386/build/include

but it doesn't work. The only error I get is

make -C "/lib/modules/2.6.8.1-3-386/build" SUBDIRS="/home/rosa/qc-usb-messenger-0.8" modules V=1 USER_OPT=""
make[1]: Entering directory `/lib/modules/2.6.8.1-3-386/build'
make[1]: *** No hay ninguna regla para construir el objetivo `modules'.  Alto.
make[1]: Leaving directory `/lib/modules/2.6.8.1-3-386/build'
make: *** [quickcam.ko] Error 2

"No hay ninguna regla para construir el objetivo 'modules'. Alto." = "No rules to buiild the target modules'. Stop"

Anybody can help?

(Sorry. I know my English is very bad)

---

### Post by cheleb on 2005-01-30
For all of you searching for quickcam messenger drivers look here
[http://home.mag.cx/messenger](http://home.mag.cx/messenger) ( sometimes down. find a mirror here [http://www.ee.oulu.fi/~tuukkat/quickcam/messenger](http://www.ee.oulu.fi/~tuukkat/quickcam/messenger) )

Get the latest qc-usb-messenger tarball, follow the instructions in _README_MESSENGER file and all should be well.

Cheers,
cheleb

---

