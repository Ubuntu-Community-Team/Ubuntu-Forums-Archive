---
title: "soundcard driver install: x-fi Extreme Gamer (creative)"
date: 2009-12-08
forum: Hardware
---

### Post by Odie007 on 2009-12-08
Hello,

I'm quite new to ubuntu and i'm trying to install my soundcard driver as mentionned above.  I looked it up at the manufacturer site and found myself the tarball for linux.  As commented in the install notes, I unpacked it, and then opened the readme file.  The readme file tells me the following:

=============================

Quick install
 
============= 
In terminal,
 
1) Goto source directory 
2) Execute make command as root 
   make 
   make install

=============================

And so I tried but I get some errors:s (I've marked my command and the output in bold and italic, respectively)

[B]root@kristof-desktop:/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00# make
[/B][I]make -C /lib/modules/2.6.31-16-generic/build M=/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2[/I]
[B]
root@kristof-desktop:/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00# make install[/B]
[I]Copy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1
root@kristof-desktop:/home/kristof/Downloads/XFiDrv_Linux_Public_US_1.00# [/I]

=========================================================

I've tried reading some of the ubuntu pocketguide (the one I was given by the forum founder Ubuntu-G33k Ryan :D ) but it isn't easy when you're completely new to this OS.  Though I must say, beyond the terminal commands, which is quite obvious you need to learn the commands first, the system works very much intuitively.

Please help me out here, thanks a lot ! ;)

---

### Post by michael-wd21 on 2009-12-20
Hi

It looks like the README does not tell you everything you need to know. You need to install the linux kernel headers and build-essential.

```

sudo apt-get install build-essential linux-headers-`uname -r`
```Note there is a howto and discussion thread here:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Good luck

Michael

---

