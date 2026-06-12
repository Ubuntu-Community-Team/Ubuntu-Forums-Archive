---
title: "Unable to compile driver for my Ricoh SD card (sdricoh_cs)"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by sup on 2007-05-07
I found ([here]("http://www.georgo.org/denicek/konecne-mi-funguje-ctecka-karet-v-linuxu/") - only in Czech, so do not bother) that it is possible to make my ricoh SD card working under linux using [sdricohcs]("http://sourceforge.net/projects/sdricohcs/") driver. I tried to compile it but I somehow fail:-(, both the only release (0.1) and the svn version.
README says taht requirements are as follows: 
kernel-default >= 2.6.18
gcc
make
kernel-source
kernel-syms

I have got linux-headers make and gcc, as well as the latest Feisty kernel, but the build fails: ```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tom/Desktop/sdricohcs/sdricoh_cs modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.o
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:39:32: error: linux/mmc/protocol.h: No such file or directory
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c: In function &#8216;sdricoh_reset&#8217;:
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:228: error: &#8216;MMC_GO_IDLE_STATE&#8217; undeclared (first use in this function)
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:228: error: (Each undeclared identifier is reported only once
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:228: error: for each function it appears in.)
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:234: error: &#8216;MMC_APP_CMD&#8217; undeclared (first use in this function)
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c: In function &#8216;sdricoh_request&#8217;:
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:321: error: &#8216;SD_APP_SEND_SCR&#8217; undeclared (first use in this function)
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:354: error: &#8216;MMC_SELECT_CARD&#8217; undeclared (first use in this function)
/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.c:355: error: &#8216;MMC_APP_CMD&#8217; undeclared (first use in this function)
make[2]: *** [/home/tom/Desktop/sdricohcs/sdricoh_cs/sdricoh_cs.o] Error 1
make[1]: *** [_module_/home/tom/Desktop/sdricohcs/sdricoh_cs] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

```
It cannot find mmc/protocol.h, which is nowhere on my system (I checked with locate). How do I get it, do I need to compile my own kernel with something enabled (probably MMC stuff as suggested in [gentoo wiki]("http://http://gentoo-wiki.com/HOWTO_SD_and_MMC_card_readers")? Or any other idea? I would rather not use compiled kernel, because it seems that for driver issues I need only to compile drivers, not the kernel...
Thanks for any advice.

---

### Post by evilmonkey on 2007-05-11
If you're still having this problem, you can follow the resolution to it here (I'm certainly having the same problem): [http://www.linuxquestions.org/questions/showthread.php?t=552086](http://www.linuxquestions.org/questions/showthread.php?t=552086)

If you have figured it out, do let me know. :) Thanks.

---

### Post by sup on 2007-05-12
I actually gave up and hoped this would get included in Gutsy. However, when I read your thread, I filed a [bug]("http://www.linuxquestions.org/questions/showthread.php?t=552086") on launchpad.
I really do not understand where that protocol.h file went:-/

---

### Post by evilmonkey on 2007-05-14
Alright, let's see if the bug squashing people (or the author of this driver, I emailed him) can shed some light on this problem.

---

### Post by evilmonkey on 2007-05-14
Wow, it really helps to raed the development forums sometimes. Here's what you do:
-Download the latest SVN version
-Open the sdricoh_cs.c file
-find the reference to protocol.h
-comment out all the if kernel_version stuff around it
-make sure that sd.h is not commented out
-make, sudo make install

Basically, as of kernel 2.6.20+, protocol.h is named sd.h. The author put in a procedure to check the kernel version, but it only checks kernel 2.6.22 and above. It just so happens that feisty uses 2.6.21. So make sure that all that if/elseif/else stuff is commented out and only sd.h and not protocol.h is uncommented. This works like a champ. =)))

---

### Post by sup on 2007-05-14
Great, it worked for me, even if I have to wait till I get to a card to test it, it installed though.
The devs (correctly) closed my bug, as it was a duplicate of another, which in turn I closed, since this is not a bug in Ubuntu but in the driver.

---

