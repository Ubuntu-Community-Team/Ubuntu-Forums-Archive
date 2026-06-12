---
title: "[SOLVED] Would ubuntu install a Gcc.EXE on a windows partition and run it?"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by mfische4 on 2008-12-22
Hello,

I have recently installed ubuntu 8.10 on a new partition that already had windows xp on the remaining part of the disk. Since installing ubuntu I have seen on the xp system a file called Gcc.EXE in the "\Program Files\Linksys\Wireless-G Notebook Adapter" directory.  I have checked with Linksys and they said do not own this file. The file from windows says that it is: 
File Version = 1.0.0.4
Internal Name = Gcc
Language = English
Original Filename = Gcc.EXE
Product name = Gcc Application
Product version = 1.0.0.4

Would ubuntu installed such a file and have it run when I'm running windows XP?  What would it do?

Thank you

---

### Post by snova on 2008-12-22
It's a compiler, and is of no use unless you're a programmer.

I don't know where it came from, but Ubuntu would not have installed it, as it doesn't touch your Windows partition (except to resize it if necessary).

---

### Post by Shazaam on 2008-12-22
As an aside, there are files/folders that are so-called "SuperHidden" in Windows. When you get access to Windows through other operating systems these files sometimes become accessable.

---

### Post by mfische4 on 2008-12-29
:oops:
It seems that when I installed an older version of the driver to support the WPC54GS card (Version 1) this driver has a process called Gcc.EXE.  I had re-installed this correct driver version about the same time I installed ubuntu.  

Sorry, it seemed too much of a coincidence to see that there.

Thank you

---

