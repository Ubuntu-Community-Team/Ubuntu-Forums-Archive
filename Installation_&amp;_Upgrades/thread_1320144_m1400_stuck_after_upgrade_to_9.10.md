---
title: "m1400: stuck after upgrade to 9.10"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Ben63 on 2009-11-08
Hi,
I have a quite hold computer m1400 that was working fine with Jaunty.
Though it was working only with the kernels 2.6.24, not upper.
Then I had the will to upgrade to karmic 9.10 ; it kept my kernel 2.6.24, but it seams karmic would not want to boot with it (I get a mountall:/proc: unable to mount Device or resource busy) :( I read somewhere it is due to the fact karmic would not want to boot on the kernel 2.6.24.
So now I am stuck, and I did not wisely make backup of my jaunty installation.
Basically the kernels upper than 2.6.24 will just block at the very beginning of the start.
Any idea?

---

### Post by Ben63 on 2009-11-09
up

---

### Post by duckling9 on 2009-11-13
maybe similar to mine?
(I also have no replies....)
 
[http://ubuntuforums.org/showthread.php?t=1319891](http://ubuntuforums.org/showthread.php?t=1319891)

---

### Post by duckling9 on 2009-11-13
are you trying to boot using the most recent kernel, or is grub still pointing to the old kernels (eg because you chose to keep menu.lst?) is so,
maybe something like this may work?
[http://ubuntuforums.org/showthread.php?t=1318129&highlight=mountall](http://ubuntuforums.org/showthread.php?t=1318129&highlight=mountall)
 
it just did for me :)

---

