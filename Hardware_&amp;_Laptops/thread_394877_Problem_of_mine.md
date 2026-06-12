---
title: "Problem of mine"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by Amit G on 2007-03-27
I had earlier asked a question on whether I could use both Windows XP and Ubuntu Linux 6.06 LTS on the same laptop by partitioning the hard disk  into two and whether it would lead to instability and got excellent replies and that problem of mine has been solved- I came to know about dual-booting and grub and several other answers which have helped me a lot in respect to that problem of mine . My next question is in continuation to that question since I am planning to get a laptop pretty soon and have an Ubuntu Linux 6.06 LTS with me, and my question is that even though Ubuntu is stable, Windows is not- is it possible that when I partition a hard disk into two parts one with Windows and another with Ubuntu and somehow Windows crashes, will it mean that it will affect the entire hard disk and Ubuntu might crash too because of Windows? if so, is it possible that I can have two internal hard disks on my laptop, one with Windows and another with Ubuntu and if somehow Windows XP crashes it will not affect the other hard disk with Ubuntu Linux 6.06 LTS on it. And this is a general question of hardware-can two internal hard disks work on a laptop as they do on a desktop computer? And which is the better bet- one hard disk partitioned into two parts with Windows on one and Ubuntu on the other or two separate hard disks one with Windows and the other with Ubuntu.

---

### Post by aysiu on 2007-03-27
> Windows is not- is it possible that when I partition a hard disk into two parts one with Windows and another with Ubuntu and somehow Windows crashes, will it mean that it will affect the entire hard disk and Ubuntu might crash too because of Windows? Unless Windows actually finds some way to damage the *hardware*, then it cannot affect Ubuntu's stability.

But... if you crash Windows and decide to reinstall it, the Windows installer will overwrite Ubuntu's boot loader (the one that easily allows a dual-boot), so you will have to reinstalled Ubuntu's boot loader (Grub) to the Master Boot Record in order to boot to both OSes (instead of just Windows).

> And which is the better bet- one hard disk partitioned into two parts with Windows on one and Ubuntu on the other or two separate hard disks one with Windows and the other with Ubuntu. Neither is better. Some people prefer two separate drives because they think the likelihood of messing up the other installation is lower (especially since you don't have to resize partitions). I've never had data loss from a partition resize.

---

