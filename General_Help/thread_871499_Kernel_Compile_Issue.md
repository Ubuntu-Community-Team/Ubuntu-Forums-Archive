---
title: "Kernel Compile Issue"
date: 2008-07-27
forum: General Help
---

### Post by Floppie on 2008-07-27
Hey, first time poster, ...first time reader as well I guess ;)

I installed Kubuntu on a friend's box, and everything has worked well with one exception - he has dial-up and the stock modem didn't work.  After some research, I found that the Broadcom modem's driver simply wouldn't work with a 2.6 kernel - so I ordered a Lucent (Agere) modem, that - according to [http://www.linmodems.org/](http://www.linmodems.org/) - is supported.  PCI ID 11c1:0620 for reference.

Before I tried searching online for a driver, I wanted to look through the kernel configuration to see if there was something built-in that just wasn't being compiled.  When I tried to run `make xconfig` I got the following issue:

```
$ sudo make xconfig
  CHECK   qt
*
* Unable to find the QT3 installation. Please make sure that
* the QT3 development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2
```

So I figured I'd locate a driver on the interweb.  After a while, I located the following repository - [http://linmodems.technion.ac.il/packages/ltmodem/](http://linmodems.technion.ac.il/packages/ltmodem/) - and tried downloading a handful of different packages from there.

First I tried downloading the Debian packages in [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/), but those are for an older kernel version (2.6.24-19-generic on the box).

Then I tried downloading some of the various source packages to compile them.  I grabbed [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/agrsm-20070804.tar.gz](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/agrsm-20070804.tar.gz), but I got errors and figured it was because it was an old version.  So I grabbed the ltmodem source tarball, same thing.  Then I grabbed a martian source package and compiled it without an issue, but it was for the wrong chipset.

Then, finally, I backed out of the kernel-2.6/ dir and decided to try the source packages in [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/) - both the ubuntu package and the latest dated package.  Every compiler error I got was the same:

```
$ sudo make
[sudo] password for ******:
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [module] Error 2
```

So I began to think that maybe it's not a driver issue.  Since I even got an error during `make xconfig` and `make gconfig` (the error was the same as earlier, but .tmp_gtkcheck rather than .tmp_qtcheck), but not `make menuconfig`.

That's when I decided to try posting here, to see if maybe someone else had had the same issue and resolved it.  I am, of course, talking about general driver compiling - the modem thing is way too obscure.  I've got pkg_config installed, but it's still giving me that same error from above.

---

### Post by Floppie on 2008-07-27
Oh yeah, forgot to mention - version of Kubuntu is Hardy Heron.

---

### Post by Floppie on 2008-07-27
Since this is down the sixth page where nobody who can help is likely, at all, to find it...bump ;)

---

### Post by Floppie on 2008-07-28
Anybody out there?

If more information is needed, I'd be happy to provide it, the box is currently in my custody until I can get it working properly - including the modem.

Or if this is in the wrong board I'd be happy to repost it (or have it moved) elsewhere.

---

### Post by ace007 on 2008-08-19
I hate to bring this old post up, but I had the same problem with make xconfig.  I solved it by

```

sudo apt-get install libqt3-mv-dev

```

---

