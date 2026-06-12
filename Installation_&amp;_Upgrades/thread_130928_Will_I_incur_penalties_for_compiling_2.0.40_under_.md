---
title: "Will I incur penalties for compiling 2.0.40 under Breezy?"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by K.Mandla on 2006-02-15
I want to drop back to kernel 2.0.40 and see if some hardware issues disappear. 

Will I run into any other, unforeseen issues? Will other stuff mysteriously break? 

Will my friends leave me and my family disown me? Will my dog stop worshipping me? :cry: 

Okay, just kidding. :rolleyes: The original question is a serious one, though. Thanks.

---

### Post by tseliot on 2006-02-15
I think it's doable. Perhaps you won't be able to use Ubuntu's splash screen therefore you might see a black screen at boot but in the end you woul get to the login manager and everything would be fine; you might want to disable the bootsplash if you experimented this problem.

I think everything else should be fine. You won't have any restricted modules though

---

### Post by K.Mandla on 2006-02-15
Actually, I've already run into a hitch. I was following your guide for newbies, and ran into this error when I told it to *sudo make menuconfig*. 

> rm -f include/asm
( cd include ; ln -sf asm-i386 asm)
make -C scripts/lxdialog all
make[1]: Entering directory `/usr/src/linux-2.0.40/scripts/lxdialog'
gcc -O2 -Wall -fomit-frame-pointer -DLOCALE  -DCURSES_LOC="<ncurses.h>"   -c -o lxdialog.o lxdialog.c
lxdialog.c: In function ‘main’:
lxdialog.c:126: error: assignment of read-only location
lxdialog.c: In function ‘j_inputbox’:
lxdialog.c:212: warning: pointer targets in passing argument 2 of ‘fprintf’ differ in signedness
make[1]: *** [lxdialog.o] Error 1
make[1]: Leaving directory `/usr/src/linux-2.0.40/scripts/lxdialog'
make: *** [menuconfig] Error 2
I'm afraid I'm too new at this to decode that. Sorry. Any suggestions? :confused:

---

