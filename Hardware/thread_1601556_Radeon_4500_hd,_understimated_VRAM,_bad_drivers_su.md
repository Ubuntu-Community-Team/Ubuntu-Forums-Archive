---
title: "Radeon 4500 hd, understimated VRAM, bad drivers support?"
date: 2010-10-20
forum: Hardware
---

### Post by maseli on 2010-10-20
Hey guys,
I spent couple of days googling and trying to figure it out by myself, but I couldn't, therefore I resort to the forum-wisdom. If it's trivial and/or already answered, please do forgive me, I tried my best.

The problem is that while I've never had any problems with graphics during normal, day-to-day usage of my Ubuntu, an attempt to play a game ended up with failure. Since the game in question was PES2011, I was able to look up the problem (it has in-built requirement checking device). It turnes out that my Radeon 4500 hd is recognized as, quote:
GPU: Direct3D HAL (PS3.0/VS3.0)
VRAM: 128 MB

Both of those don't meet minimal requirements, hence the game crashes.
I think that I managed to install it properly (it doubtlessly starts to load), so I figured that there is a problem with drivers. I installed proprietary drivers. This is my current version:
radek@radek-laptop:~$ cat /var/log/Xorg.0.log | grep 'Driver Version'
(II) ATI Proprietary Linux Driver Version Identifier:8.77.5

I also tried to manually set up my VRAM in xorg.conf, to no avail.

My details are:
Ubuntu 10.04 (lucid) 32bit
GNOME 2.30.2
Kernel: 2.6.32-25-generic 
Wine 1.2
Dell Studio 1745 with Radeon 4500HD, 2GB VRAM

I would be grateful for any ideas how to fix it. By the way, the game works perfectly on the same notebook on WIN7. I want to switch completety to linux and this is the last thing that keeps me with M$. If the info I gave is incomplete, tell me what I should add.

Thanks in advance,
Radek

---

### Post by maseli on 2010-10-22
I tried many many things (downloading some stuff from winetricks, editing wine registry etc) and now I can go to main menu and even play in the training mode (although graphics look a bit like in FIFA 98 ) but it still hangs when I am trying to play a match. When I run it in the terminal it says:

Unhandled page fault on read access to 

and than some numbers, not always the same.

Interestingly enough, now the game recognizes my Video Card as Radeon HD 3200

Please, do you have any ideas what should I do?

---

