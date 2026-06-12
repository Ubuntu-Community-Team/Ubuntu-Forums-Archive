---
title: "Intel Mobile Graphics Chipset 4, i915 drivers and Linux Kernel 2.6.38 to 3.0.0"
date: 2011-12-09
forum: Hardware
---

### Post by Atomic-Fanboy on 2011-12-09
I really need some help with this problem.

Situation - I have been using Ubuntu for about 2 years - and for the last year I have used it almost exclusively, but I have had (and am having) serious graphics problems. If I do anything that replaces or updates the file grub.conf, my computer screen flickers horrendously and renders my computer unusable until I edit grub.conf to add "i915.powersave=0" to each option entry. 

I have coped and struggled with this for a very long time. However after the kernel 2.6.38 was released as an update, if I tried to boot from 2.6.38 (or 3.0.x, come to think of it...) my computer display simply turns blank and black, and I have to use "Ctrl + Alt + System Request - R, E, I, S, U, B" to restart cleanly. 

Please help me, somebody...

Thanks

---

### Post by Atomic-Fanboy on 2011-12-29
No longer an issue.

---

### Post by wildmanne39 on 2011-12-29
Hi, please share with us how you fixed your problem.
Thanks

---

### Post by Atomic-Fanboy on 2012-01-11
First off - sorry for the late reply.

It turned out that my computer was actually booting fine, but for some reason the screen's default brightness was at the lowest possible setting instead of the brightest possible setting (which is normal). 

Hopefully this should help. It doesn't fix the problem completely, but it helps a great deal.

[http://crashcourse.ca/blog/2011/02/workaround-intel-i915-black-screen-linux-boot-problem](http://crashcourse.ca/blog/2011/02/workaround-intel-i915-black-screen-linux-boot-problem)

---

