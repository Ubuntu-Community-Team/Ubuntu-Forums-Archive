---
title: "ICH5 Sata Problems"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by ConH on 2006-08-20
Hi,

I have installed many different Linux distro's in an attempt to get mny sata working. Actiually Ubuntu is the first distrro that's able to run almost satisfactory. And it is a great distro besides!

I've read a lot on problems concerning sata support and the problems that occur, but I cannot seem to find a right answer for my situation. At the moment I run Ubunto in the compatible bios mode. In an attempt to get enhanced mode working, I compiled a 2.6.17 kernel (latest stable) which went wonderfully with the how to on this forum as leadway. My system runs much faster now, and sata support improved because even in compatible mode it recocnisez both my pata drives (DVD drives). Normally in compatible mode you have to chose on or the other pata channel.

However after changing the biosmode to enhanced, it still won't boot at all. My MB is an Asus from the Terminator barebone system (P4/478).

I think the throughput of this ICH5 controller will benefit greatly when running in enhanced mode. In MS Windows the differende is very noticable. Anyone an Idea on how to proceed?

Thanks in advance.
Con

---

### Post by ConH on 2006-09-29
To solve my problems regarding the SATA as decribed above, I bought a new IDE HD and switched it with my SATA drive. I still have problems installing Ubuntu, Dapper says: unable to mount root (it can't find the cdrom after starting the kernel), Edgy says: CDROM seems to be confused. I tried all setting in the Bios regarding the IDE interface, the only one that works is the compatible. So the enhanced setting does not work, even in PATA only system. I never thought problem would relate to ordinary ATA devices...

What is so special about the ICH5 Chip, that makes it still not supported in Linux? It is a pretty old damned thing!

So in the Bios I have to disable SATA and set the remaining PATA to compatible. That seems two steps back... I'm Not sure if I want to keep running Linux this way. Unfortunately my barebone board has no room for another SATA card.

Con

---

