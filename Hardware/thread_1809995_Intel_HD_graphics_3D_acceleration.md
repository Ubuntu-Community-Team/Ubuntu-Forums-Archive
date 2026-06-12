---
title: "Intel HD graphics 3D acceleration"
date: 2011-07-22
forum: Hardware
---

### Post by linuxisgreat on 2011-07-22
I recently replaced a desktop computer with a nvidia graphics card to a laptop computer which uses the intel HD graphics chipset. I am booting ubuntu from the same portable drive which I used on the old machine.

People on this forum say it should work fine out of the box but though I can use modes with high resolution it turns out it does not fully work because the 3D acceleration does not work and I cannot play games such as trigger a rally car game.

Games such as this will not load and they worked fine on the other nvidia desktop machine. Changing the video card is not an option as this is a laptop and I cannot remove it as it is soldered to the board.

There are no proprietary drivers to be activated and I would like to know how I can compile the driver for it or install it from a package.

Any help is appreciated.

---

### Post by Mcjohnnson on 2011-07-22
What is your CPU?
My Pentium U5400 does quite well. VA-API with VLC is not running properly.

---

### Post by linuxisgreat on 2011-07-23
My CPU is intel core i5-480M

---

### Post by jramshu on 2011-07-23
Have you looked on Intel's site for the newest version of Linux drivers? You probably have a generic installed and there may be a better one out there that you will have to get.

From their site:
> 2011-5-6: Intel®Open Source HD Graphics PRM (for 2011 Intel Core Processor Family, codenamed Sandy Bridge) posted.

[http://intellinuxgraphics.org/2011Q1.html](http://intellinuxgraphics.org/2011Q1.html)

You will have to verify exactly which one you need and it will have to be compiled.

---

### Post by linuxisgreat on 2011-07-24
Ok thanks for the help so far but I still have a few errors to work out.

I downloaded the intel mesa and libdrm git source drivers but when I tried to install the mesa driver I got an error saying that glproto was an older subversion in the command line output when I run autogen.sh in the mesa folder to create the makefile.

I'm not sure if this was the right thing to do but I installed the newer version of GLPROTO overwriting the version that was installed in ubuntu 10.04 I didn't even remove the original version using synaptic.

Nevertheless it doesn't say that error anymore but it turned out I had to install the libDRM driver first so I ran the autogen script on that and I got this error

```
user@user-desktop:~/mesa/drm$ ./autogen.sh
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 189.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf line 189.
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force -I m4 ${ACLOCAL_FLAGS}
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
intel/Makefile.am:33: Libtool library used but `LIBTOOL' is undefined
intel/Makefile.am:33:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
intel/Makefile.am:33:   to `configure.ac' and run `aclocal' and `autoconf' again.
intel/Makefile.am:33:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
intel/Makefile.am:33:   its definition is in aclocal's search path.
libkms/Makefile.am:6: Libtool library used but `LIBTOOL' is undefined
libkms/Makefile.am:6:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libkms/Makefile.am:6:   to `configure.ac' and run `aclocal' and `autoconf' again.
libkms/Makefile.am:6:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
libkms/Makefile.am:6:   its definition is in aclocal's search path.
nouveau/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
nouveau/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
nouveau/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
nouveau/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
nouveau/Makefile.am:8:   its definition is in aclocal's search path.
radeon/Makefile.am:32: Libtool library used but `LIBTOOL' is undefined
radeon/Makefile.am:32:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
radeon/Makefile.am:32:   to `configure.ac' and run `aclocal' and `autoconf' again.
radeon/Makefile.am:32:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
radeon/Makefile.am:32:   its definition is in aclocal's search path.
tests/Makefile.am:21: Libtool library used but `LIBTOOL' is undefined
tests/Makefile.am:21:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
tests/Makefile.am:21:   to `configure.ac' and run `aclocal' and `autoconf' again.
tests/Makefile.am:21:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
tests/Makefile.am:21:   its definition is in aclocal's search path.
Makefile.am:46: Libtool library used but `LIBTOOL' is undefined
Makefile.am:46:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Makefile.am:46:   to `configure.ac' and run `aclocal' and `autoconf' again.
Makefile.am:46:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
Makefile.am:46:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to disable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for working alloca.h... yes
checking for alloca... yes
./configure: line 4586: syntax error near unexpected token `2.2'
./configure: line 4586: `LT_PREREQ(2.2)'
```

not sure about this one but I think it's something to do with libtool.

So I'm asking two questions:

Was I right to overwrite the version of glproto which is included in the ubuntu packages?

and

What should I do about this libtool error?

---

### Post by Cadeyrn on 2011-10-01
If you're running 11.04 or greater, you'll find that Ubuntu's x.org server comes pre-installed with the correct versions of every component in that 2011Q1 driver. No point in trying to messily install it again outside of synaptic. And yet there's still no 3D acceleration. I have the same problem as you.

---

### Post by emilywind on 2011-10-01
Did you use the proprietary nvidia driver before? If so, remove that first. After that, try the following.

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-video-intel xserver-xorg

Then reboot. If that does not solve the problem, boot Ubuntu off a live USB drive and see if it works there. If so, the nvidia driver likely replaced more than the fglrx driver does and someone else may know more on that topic and how to get things working again. Cheers. :)

---

### Post by realzippy on 2011-10-01
> **emilywind said:**
> Did you use the proprietary nvidia driver before? If so, **remove that first**. After that, try the following.
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-video-intel xserver-xorg
```

+1 !!

Which Ubuntu version do you run?

A fully updated 11.04 works with Sandybridge graphics.
If it is 10.04 LTS,no need to compile the stuff,use glasen's ppa:

```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

```
reboot.

---

### Post by Cadeyrn on 2011-10-01
Thanks for the tip! It just so happens that my current installation was copied from the hard drive of my last laptop, which did use the nvidia proprietary drivers. I'll test your solution now.

EDIT: It didn't work. I still can't enable desktop effects or play games. I'm gonna see if the liveUSB has acceleration.

EDIT2: And the liveUSB DOES have 3D acceleration, and it works very smoothly, too! Crap. I don't want to reinstall my OS and have to reconfigure everything.

---

### Post by Cadeyrn on 2011-10-02
What if I reinstalled every x.org package? Would that wipe NVidia's crap? Is it otherwise dangerous to do? Screw it, I'm gonna back up my entire hard drive and then try it.

---

### Post by Cadeyrn on 2011-10-02
Ah, nevermind! It was still not working because fglrx was also installed somehow... don't know how that happened.

Anyway, I uninstalled fglrx and reinstalled those packages again and I now have 3D acceleration on my Intel HD graphics! Thanks for the help.

---

### Post by foresthill on 2011-10-02
If you want better 3D performance in games, when you log in choose "Classic Ubuntu Desktop, No Effects". Those desktop effects hog a ton of GPU cycles. 

My framerates in games literally doubled when I did this.

---

