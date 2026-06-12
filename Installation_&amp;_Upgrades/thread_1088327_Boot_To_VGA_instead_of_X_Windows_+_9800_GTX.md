---
title: "Boot To VGA instead of X Windows + 9800 GTX"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by nova47 on 2009-03-05
I was wondering how to have my computer boot into a VGA console rather than immediately booting to X Windows. I'm installing the Nvidia 9800 gtx drivers (that's the nvidia version 177 drivers) manually and I want a fail safe in case something goes wrong. Just for reference this is the tutorial I'm looking at:

[http://us.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-04.html](http://us.download.nvidia.com/XFree86/Linux-x86/180.29/README/chapter-04.html)

From what I understand there is no longer a /etc/inittab file so I'm assuming there is an alternate method.

---

### Post by martrn on 2009-03-05
Ubuntu uses [upstart]("http://upstart.ubuntu.com/") which is n event-based replacement for init.

Also see thred [/etc/inittab replacement for respawn]("http://ubuntuforums.org/showthread.php?t=668137")  for a discussion, and someone waiting to join a thred.

I have particular problems with this myself.

---

