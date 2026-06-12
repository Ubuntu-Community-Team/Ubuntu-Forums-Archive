---
title: "Upgrade - not enough disk space?? (newbie)"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by mknee on 2009-08-30
Hi - I'm a newbie to Ubuntu - can anyone help me with a problem?

I have created a USB startup disk on an external HDD & booted into Ubuntu 8.1. Now I am trying to upgrade to 9.04 from update manager.

The problem is I am getting a message saying I only have 499MB of free space which isn;t enough to upgrade, yet df -h tells me I have 26GB of space.

I have googled a bit & ran DF - i which tells me I have zero iNodes?? my Linux knowledge kinda breaks down at this point - what am I doing wrong?

Thanks

Mike

---

### Post by VMC on 2009-08-30
The easiest fix is to use Gparted and use that program to resize you partition to a larger size. I would use a livecd like partedmagic. It has gparted on it.

What's the output of

```
sudo fdisk -l
```

---

