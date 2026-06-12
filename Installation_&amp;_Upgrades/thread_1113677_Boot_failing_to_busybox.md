---
title: "Boot failing to busybox"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by xaiks on 2009-04-01
I've taken a look around and seen a lot of other people having problems while booting and failing to busybox. I've tried everything mentioned in those threads but have yet to find anything that helps, though I likely haven't read every single thread pertaining to the subject.

I'm running 8.10, though it happened with 8.4 as well. I have no solid info on most of the hardware, it's a bit old, but it shouldn't be too bad, as it's a dual Xeon P4 with a gig of ram. The problem still exists after re-installing.

What happens for me is, while booting from grub, ubuntu will make it to the "bouncing" loading screen. A little while later it will fail to busybox saying something along the lines that it can't find the root drive. This starts off as a UUID, I check through busybox and it's fully correct, and present. Restarting, I then change this to the old /dev/sdaX method and it still gives the error.

However, I figured out a small workaround. Typing exit in busybox will allow it to continue to boot as normal and run just fine. Since I was able to exit busybox and continue, I figured it was a timing issue. Sure enough, adding rootdelay= allows it to boot just fine. Unfortunately, it currently only works with an absurdely huge delay (I have it set at 45 at the moment, it doesn't always work at 40).

So, I'm wondering, did i miss a thread somewhere that has an obvious answer to my problem? Or is there someone that could explain where my ancient hardware might be causing it to take nearly a minute to find the hard drive during boot, and why it can't be fixed, and put my mind at rest?

Thanks in advance to anyone that might respond. :)

---

### Post by TyMan210 on 2009-04-01
I have this problem too.
Every time it boots it goes to BusyBox, so if you find anything please pm me. :mrgreen:

---

### Post by Slyder0244 on 2009-05-09
i'm currently trying to boot into a live session with ubuntu 9.04 and it just keeps showing me the busybox screen i tried typing exit like you said worked for you but all i got was this 

```
cp: cannot create '/root/var/log/': No suck file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.
```
but maybe it's because i don't have ubuntu installed on the drive and i'm just trying to get into the live session

---

### Post by TyMan210 on 2009-12-03
I fixed mine. It was a the hard drive, so I just got a new one.

---

