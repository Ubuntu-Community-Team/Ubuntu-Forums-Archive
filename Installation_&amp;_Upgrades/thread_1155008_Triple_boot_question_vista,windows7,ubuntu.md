---
title: "Triple boot question vista,windows7,ubuntu"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by crawdad3 on 2009-05-10
Hi I am new to the world of Ubuntu but recently installed the 64 bit version on a seperate partition and dual boot with my Vista. Everything went flawlessly and am really enjoying Ubuntu and don't want to ruin what is working hence my question. I would like to create another partition and install Windows7 RC1. Is there a noob-proof simple way to do this and triple boot vista,ubuntu and windows7? I installed ubuntu on a 250gb partition which is way more than I need so am thinking of shrinking that. Any advice would be appreciated.

---

### Post by Yurebis on 2009-05-10
I have a similar setup. I did this:

-Created a new ntfs partition of ~14gb or more (That's what the Win7 setup recommended I think, despite the actual size it takes being ~7gb...). I use gparted because it's easy.

-Setup a GRUB chainload to that partition. If you don't know how to do this there's tons of guides out there, for LILO too. Mine is like this:

```
title Windows 7 RC1 (build 7100)
rootnoverify (hd0,1)
chainloader +1
```

-Went ahead and booted into the Windows7 install disc and "custom installed" into the partition (sda2 in my case, or hd0,1). There's only two modes of instalation, one is upgrade, and the other is "custom". The custom one formats whatever partition it is pointed to, so be careful.

-Booted through a live cd to take back my MBR with grub since widnows just overwrites it on a whim without even considering other poor, defenseless OS's. You type into a console:
```
grub
```
you will enter the grub console mode. next:
```
root (hd0,0)
```
that will tell grub you want your MBR to point to the first partition in your first hard drive. My partition setup is oldschool where the first partition is a boot dedicated one. You gotta point grub to wherever you keep your /boot/ in your case.
And then commit:
```
setup (hd0)
```

Thats from the top of my head but the general idea is safe. There's guides out there if in doubt.

One thing I would advise to keep this a s safe as possible is to make sure your disk image or media isnt corrupted. In my first try, windows setup failed midway and left em with a garbage partition table which i had to fix. Thank God there's testdisk. Anyway, check your OS's disks before you install them.

---

