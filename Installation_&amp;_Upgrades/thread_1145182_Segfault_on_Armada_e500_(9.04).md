---
title: "Segfault on Armada e500 (9.04)"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by Whateverist on 2009-05-01
I have tried to install Xubuntu (9.04 alternate install CD) on an Armada e500 (P3, 128mb ram), thinking I might switch to Fluxbox later. The hardware works, as it used to have a working (but cripplingly slow) copy of XP installed. The install went fine, but when the laptop rebooted I got a screen full of "segmentation fault" messages, as well as this:

```
rm: cannot remove '.tmp/.clean': read-only file system
(more lines of "segmentation fault")
init: rc-default main process (1565) terminated with status 139
```

The same message appears every time I try to boot; the progress bar under the Xubuntu logo crawls to the right and the error pops up when it's nearly finished.

I've Googled the error message and searched the forums but haven't been able to find anything.

One thing that *might* be related - by virtue of me not knowing what it actually does - is something called an Intel Boot Agent that I haven't been able to get rid of. I checked the install CD and it is not corrupted. 

How do I proceed from here to diagnose and fix the problem?

---

### Post by tromas on 2009-05-13
Your post was the only one i found when googeling on this error as i got the excect same one, after installing (upgrading) xubuntu to 9.04 on a old Dell laptop.

I solved the problem by disabling all the powersaving in the  BIOS, got to be lucky sometime:p

---

