---
title: "Dual Booting: XP Fails to Start"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Ashly on 2009-10-31
Hi all,

After installing a fresh 9.10 system, dual booting with XP is broken. Grub has the right disk and XP starts booting fine, except it fails with the following error:

> Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.

I've found a bunch of threads around with the same problem, but nobody seems to have found a solution. It worked fine with 9.04, so I'm really not sure where to go from here.

---

### Post by sliketymo on 2009-10-31
> **Ashly said:**
> Hi all,

After installing a fresh 9.10 system, dual booting with XP is broken. Grub has the right disk and XP starts booting fine, except it fails with the following error:



I've found a bunch of threads around with the same problem, but nobody seems to have found a solution. It worked fine with 9.04, so I'm really not sure where to go from here.

I hate to tell you,but you hosed your windows MBR(Master Boot Record)
You will have to insert your xp installation CD,and repair your Boot.
Do this by booting the xp Disk.The files will load,as if you are re-installing.It will get to a point where it will ask you ask if you want to install,repair startup.fix my computer,etc:The last choice will be command prompt.Open a command prompt and code: bootrec.exe/FixMbr",Then do "bootrec.exe/FixBoot".close,and restart your computer.That should fix your windows boot problem.Then you will have to boot your Ubuntu disk,and re-install grub.Good luck!

---

