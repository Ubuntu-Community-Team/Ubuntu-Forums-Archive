---
title: "[boot]Windows halts shortly after GRUB"
date: 2005-02-20
forum: Hardware &amp; Laptops
---

### Post by Acolyte on 2005-02-20
Here's the problem.
I have installed my config in the following order: Windows XP, Windows 98, Ubuntu.
I had lots of trouble dual-booting WinXP and Win98, but now with Ubuntu the troubles are even worse. During installation, Ubuntu tried to detect all the OS'es for grub, which he kinda failed to. He only detected WinXP but I thought "Oh well Win98 is not my first priority for now, we'll fix that later on. First I want to successfully dualboot between XP and Linux.". So I gave Ubuntu the Yes to configure grub with the detected OS.
Till this morning, I was perfectly able to boot to both OS'es with grub between it. But since an hour ago Windows won't fully boot anymore. You see the loading screen but quickly after that the hard drives shutdown and the system halts with the message something like "System Initialization Manager suddenly stopped" or so. If this is too unclear I will check it and remember the exact message.

My question is: How to fix this in a way so that I can boot to both again and (if possible) also configure grub to be able to boot to win98?

Thanks in advance :)

---

### Post by Acolyte on 2005-02-20
Well, the solution seemed to be quite easy: change the partition ID with fdisk from 17 (hidden ntfs) to 7 (ntfs) and you're done. I can now boot again between them. But still Windows98 is not recognized... How about that?

Any ideas?

---

