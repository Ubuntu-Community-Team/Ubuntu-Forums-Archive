---
title: "Dual-Booting with WinXP."
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by SamShambles on 2006-02-18
Hi there,

I've been trying out ubuntu on a LiveCD and now I want to have it dual-bootable with windows XP. I was wondering if there's a guide out there that has step by step instructions? I only have one hard drive, a 40GB IDE. And another thing, will I have to format my hard drive? 'Cos there's a lotta school work on there that I'd need to back up if I did.


Thanks in advance,
Sam.

---

### Post by lukee on 2006-02-18
[QUOTE=SamShambles]Hi there,

I've been trying out ubuntu on a LiveCD and now I want to have it dual-bootable with windows XP. I was wondering if there's a guide out there that has step by step instructions? I only have one hard drive, a 40GB IDE. And another thing, will I have to format my hard drive? 'Cos there's a lotta school work on there that I'd need to back up if I did.


Thanks in advance,
Sam.[/QUOTE]

The Ubuntu installer allows you to nondestructively partition your hard drive, so you can keep Windows XP. It'll also walk you through getting set up for dual-booting.

---

### Post by SamShambles on 2006-02-18
Okie dokie. I think I'll backup all my school stuff anyway, incase I screw it up! Thanks for the help, I'll report back with my result.

---

### Post by SamShambles on 2006-02-18
Well, I just tried it. And I got to the partitioning bit and selected the guided option, I chose to make a 15gb partition. But it gave me an error saying I'd need to do it manually. What's the go?

---

### Post by Herman on 2006-02-18
If you have your Windows XP on an NTFS file system, [here]("http://users.bigpond.net.au/hermanzone/p3.htm") is an example you can follow if you like, it shows you how to create a fat32 logical partition at the same time as your install for sharing files between Ubuntu and Windows.

If you have Windows XP or 98 with the FAT32 filesystem (makes a better dual boot computer), you might prefer [this one]("http://users.bigpond.net.au/hermanzone/p2.htm") better. This is my favorite, it's the easiest, and the best.

Some people also like [this one]("http://users.bigpond.net.au/hermanzone/p14.htm"). It makes a seperate partition for your /home for those who may want to use Ubuntu for a while and then maybe try other Linux distro's without re-installing all their files every time.

Before you begin, you should read and [this]("http://users.bigpond.net.au/hermanzone/p17.htm"), about things you should do first.

Actually, you should start [here]("http://users.bigpond.net.au/hermanzone/index.htm"), at the home page, it's more of a guide to the whole site.
                            I hope that helps you install a little easier, :-D (Herman)

---

