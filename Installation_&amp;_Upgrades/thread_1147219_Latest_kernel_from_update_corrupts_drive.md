---
title: "Latest kernel from update corrupts drive"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by vetch101 on 2009-05-03
Hi all,

I've recently upgraded to Ubuntu Server 9.04.

When booting with the 2.6.28.11 kernel, it finds loads of errors on the drive.

If I boot with the 2.6.27.11 kernel, it's ok...

I am wondering what I should do about the 2.6.28.11 kernel...
Should I uninstall it? 

Should I set the default to be 2.6.27.11 so that when there are updates, I can test it again...?

I certainly don't want to find that after an update I'm left with, e.g. 2.6.29.11 and 2.6.28.11 and no 2.6.27.11...

What is the best way to manage this?

Cheers,

Jx

---

### Post by kaliif on 2009-05-03
There is a bug in 2.6.28-11 kernel. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)

I suggest you don't use it. Gave me more than one gray hair.

kaliif

---

