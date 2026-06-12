---
title: "cannot boot or install"
date: 2010-09-22
forum: Hardware
---

### Post by Hugin84 on 2010-09-22
Hi all,

I'm having quite a problem installing Ubuntu on a friend's computer.
Its an Intel Atom machine, mainboard is an Intel D945GCLF2.

Everytime I try to boot Ubuntu from CD or USB stick or try to install it I get tons of messages like the following:
[   61.112982] Currupted low memory at c0005d58 (5d58 phys) = 2ebc9001

according to [http://ubuntuforums.org/showthread.php?t=1436911&highlight=D945GCLF2]("http://ubuntuforums.org/showthread.php?t=1436911&highlight=D945GCLF2") there shouldn't be any problems with that board, so what am I doing wrong?
memtest reports 640k memory reserved (should checkt its own memory, right?) and runs without any problems, so I assume that the RAM is ok


thanks in advance for any help

---

### Post by wilee-nilee on 2010-09-22
When you startup the computer to boot the live cd hold down the shift key to get to a menu there is a memory check line try that to begin with it to see if maybe a card is broken. My computer has a built in 512, and a 512MB card and I just maxed it to 2 gigs though. 

Not sure which distro your trying to install so if it is jaunty or so I think it was the esc key for the same menu or any key I forget.

Upon looking closer the mem test you mention is this using the live cd.

The 649k available doesn't sound correct, is this a typo, should it be MB not KB.

---

### Post by Hugin84 on 2010-09-22
I was trying to install Ubuntu 10.04 and I used that CD's memtest86 to check the RAM.
I guess the problem is not Ubuntu specific but I'm gna vertify that tomorrow by trying to boot Damn Small and Gentoo minimal.


Memtest doesn't say there's 640k available but 640k reserved and like I said, I assume that the RAM is ok as memtest did not report any errors.

---

