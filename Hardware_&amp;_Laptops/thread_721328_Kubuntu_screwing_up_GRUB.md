---
title: "Kubuntu screwing up GRUB?"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by AdiNX on 2008-03-11
Hi. I have a Toshiba L40-18W laptop, and have been using Kubuntu 7.10 on it since i bought it. Today I decided I want to dual boot Kubuntu and XP, so I installed XP, the necessary drivers and all. Next I started reinstalling Kubuntu (because XP rewrote the MBR, and i could only boot XP). The installation of Kubuntu was successful, but as soon as I restarted and entered the boot loader menu, i was shocked to see that there wasn't an option to boot XP. I should mention I have installed multiple times K and XP on my desktop PC, and there was no problem at all with K screwing up the boot loader. I also ran the grub setup in Konsole, but nothing happened. XP is installed on sda5, so that means i have to put (hd0,4) in the menu.lst file in /boot/grub if want to do it manually, but this doesn't work either.
By the way, this is my second attempt, as the first time I installed XP on a separate partition from K, and then used a LiveCD to run grub setup in Konsole (this method didn't work)
Please help :|

---

### Post by Zorael on 2008-03-11
I'm not sure I understand.
> I also ran the grub setup in Konsole, but nothing happened.
> XP is installed on sda5, so that means i have to put (hd0,4) in the menu.lst file in /boot/grub if want to do it manually, but this doesn't work either.
> By the way, this is my second attempt, as the first time I installed XP on a separate partition from K, and then used a LiveCD to run grub setup in Konsole (this method didn't work)

Could you please elaborate? In what way does "nothing happen", and how do things "don't work"? It's all a bit vague to work on, see.

I'm particularly concerned about that last piece. Are you saying you installed Kubuntu onto your XP partition?

---

### Post by AdiNX on 2008-03-12
> **Zorael said:**
> I'm not sure I understand.




Could you please elaborate? In what way does "nothing happen", and how do things "don't work"? It's all a bit vague to work on, see.

I'm particularly concerned about that last piece. Are you saying you installed Kubuntu onto your XP partition?

It went like this:
new laptop (no OS installed)
got home -> installed Kubuntu
some other day ->installed xp, tried restoring grub with the kubuntu live cd with the intention of dual booting (didn't work - only kubuntu could be booted)
yesterday morning -> installed xp AND kubuntu afterwards, with the intention of dual booting (result: only kubuntu could be booted)
yesterday evening -> completely formated HDD, installed xp
today -> posting from xp; wandering if now dual boot would work, as xp is installed on (hd0,0); too angry on yesteday to try again

---

### Post by AdiNX on 2008-03-14
Ok... I just wanted to say I can dual boot Kubuntu and XP now. It seems XP has to be installed on sda1 so dual boot could work.
So if anyone else has this problem, all you have to do is completely format your HDD and make new partitions (I have a 20GB partition for C: where I installed XP, a 100GB partition for installing games, multimedia and which also works as a safe parition for Kubuntu, where I can save my work, and a 10GB partition where I installed Kubuntu, and other programs I need for programming). Then you have to install XP first and Kubuntu second.

---

