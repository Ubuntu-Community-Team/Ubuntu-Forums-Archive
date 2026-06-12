---
title: "Touchpad Edge Scrolling Problem"
date: 2010-10-01
forum: Hardware
---

### Post by Sojurner on 2010-10-01
I am on an Acer laptop. In windows my edge scrolling works fine, however in LL my edge scrolling only half works. I can scroll down just fine, however when i try to scroll up, the screen scrolls all the way down. Even if i make the slightest updward motion on the edge scrolling it scrolls all the way to the bottom.

If anyone has any idea why this is or how to fix it please let me know. BTW the multitouch works just fine, im just having a problem with the edge scrolling

---

### Post by xinematik on 2010-10-03
I'm having the same problem, using an Acer Aspire 5536-5236. The scroll works fine under a previous kernel version (I need to reboot to see wich one works), after you apply some updates (included the kernel ones) the scroll is buggy, when you scroll down works ok; but when you scroll up it's messed up.

It's good to know that I'm not the only one, btw, i've tried passing arguments to the kernel but none worked, so if you get it to work fine, let me know.

---

### Post by xinematik on 2010-10-03
> **xinematik said:**
> I'm having the same problem, using an Acer Aspire 5536-5236. The scroll works fine under a previous kernel version (I need to reboot to see wich one works), after you apply some updates (included the kernel ones) the scroll is buggy, when you scroll down works ok; but when you scroll up it's messed up.

It's good to know that I'm not the only one, btw, i've tried passing arguments to the kernel but none worked, so if you get it to work fine, let me know.

well, i changed kernel but the module has changed (or something like that) and it won't load video acceleration or trackpad scroll

Linux laptop 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

---

### Post by Denver Dave on 2011-09-29
I'm running ubuntu 11.04 on an Acer Aspire 7741.  In the mouse preferences, edge scrolling is enabled.   However, while edge scrolling works on touchpad with windows 7, does not seem to work with ubuntu 11.04 on my laptop.

Found this bug report for a different laptop that indicates fixed for 11.04, but I can't seem to get the touchpad edge scrolling to work.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803005](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803005)

Edge scrolling working for other Acer laptop users?

---

