---
title: "can't upgrade linux kernel in 9.04"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by 4ugeistr on 2009-06-17
Hello all.
I've posted the bug on the launchpad and was asked to try to reproduce it under newer kernel version:
"You are using the intrepid kernel (2.6.27-11-generic x86_64)
Can you please test with the jaunty kernel (2.6.28-11-generic) and let us know if that works?"
After googling a bit I found that it really must solve the problem.

The reason i wrote here is that I couldn't get my kernel upgraded.

The only kernel update howtos i found where with commands
$ apt-cache search kernel-image
$ sudo apt-get install kernel-image-x.x.x-xx

But when i try that i get
> 
$ apt-cache search kernel-image
comedi-source - Comedi kernel module source
$ sudo apt-get install linux-image-2.6.28-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.28-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

and afterwards I run:
> $ uname -a
Linux 4ugeistr-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux

So I still have the 27 version while it says that my 28th is already the newest. Doesn't make sense to me, or more likely i do not understand something.:(
Thanks in advance ;)

---

### Post by lemming465 on 2009-06-18
Assuming you are booting using *grub*, do you get a menu that offers a choice of multiple kernels when you boot?  If so, see if a non-default one is the 2.6.28-11 version.  Try *fgrep 2.6.28 /boot/grub/menu.lst* to see if it is listed at all.

---

### Post by 4ugeistr on 2009-06-23
Right.
That's all because of my ignorance.

I ignored the proposal to update my *menu.lst* after upgrade, that is why I hadn't any alternative boot options. 

When I checked **/boot** directory i figured that i had 2.6-28-11 and 2.6-28-13 kernel images, so I added an option in my *menu.lst* to boot using another kernel and it worked.:popcorn:

---

