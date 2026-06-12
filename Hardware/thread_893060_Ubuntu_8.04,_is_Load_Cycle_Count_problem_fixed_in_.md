---
title: "Ubuntu 8.04, is Load Cycle Count problem fixed in this version?"
date: 2008-08-17
forum: Hardware
---

### Post by vasili on 2008-08-17
I read a lot of opinions about this problem and most of them are quite long with command line explanation that it is not easy for newbie, like me, to understand.

I just want to know that is this problem solved already in Ubuntu 8.04 (without any special change in BIOS or Ubuntu's command)?

If it is safe for my hard drive, I will back to use Ubuntu again.

Thank you in advance.

---

### Post by sergiom99 on 2008-08-17
nope, its not solved.
but there is an easy fix for it, so YES its safe to use Ubuntu.
Check: [http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

---

### Post by kegie on 2008-08-17
I recently bought a Dell Studio 17 laptop to run ubuntu on, and it had the Load_Cycle problem despite being brand new. Since mine came with vista (they don't sell with linux outside the US unfortunately) I could confirm that the drive was load cycling heavily in Windows as well, so this is not a Linux problem.

As far as I can tell, this is a firmware problem on (my guess) ALL Western Digital 2.5" laptop drives. Essentially, they have made a concious decision to let the drive die within ~1.5 years to save power consumption and lower the risk of damaging the drive when moving the laptop around (that's why it is parking the heads all the time). I'll be writing them a letter for sure...

However, fixing it was easy: In the BIOS, I could choose to ignore the drive firmware setting and either set the drive in power save mode or performance mode. Setting it to performance mode means virtually zero load cycling, and the drive is running fine under roughly the same temperature. Of course the risk of damaging the drive is somewhat increased, so be careful when moving it around if you change this setting.

---

