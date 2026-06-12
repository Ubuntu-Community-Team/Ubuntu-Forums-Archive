---
title: "BusyBox v1.1.3: How do I get passed it?"
date: 2008-08-20
forum: General Help
---

### Post by TreadLight on 2008-08-20
I just updated my Ubuntu OS, then I restarted the computer, used Ubuntu aggain, restarted the computer and used Windows XP, then restarted again and tried to use Ubuntu. For some reason, BusyBox v1.1.3 pops up with this message:

"BusyBox v1.1.3 (Debain 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) ***I can type text here***"

How do I get past BusyBox to use my Ubuntu operating system?

Please give me step by step instructions instead of proposing for me to use some link. Please help!

---

### Post by kesman on 2008-08-20
Do you have multiple kernels installed in your system? I mean, do you get to choose from two or more kernels in the grub menu when you start? Try an older kernel, maybe it works.

---

### Post by TreadLight on 2008-08-20
The only two operating systems I have installed on my computer are Windows XP Home Edition and the newest version of the Ubuntu Linux operating system.

Windows XP works fine, though.

---

### Post by TreadLight on 2008-08-20
Please; can anyone help me?

---

### Post by gaurishpatil on 2008-10-10
i have the same problem..
still there is no any ans is found me....
I tried for new fresh installation of ubuntu8.04 on my machine which allready have windows xp2..
I tried different ways of installation by changing mode to safe, but error is same ...plz some one help us...
thanks in advance

---

### Post by geirha on 2008-10-10
How is ubuntu installed, by booting the live CD and run the installer? or by inserting the CD in windows and selecting the "Install inside windows" option (wubi)?

In the latter case, windows' boot loader is first used, where you can choose between windows and ubuntu. After selecting ubuntu, you'll get to the GRUB boot loader, and it probably says something like. Menu is hidden, type Esc to show it. Hit Esc when you see that, and you should see several menu choices for ubuntu. Try some of the entries further down and see if they work. Make a note of which kernel version doesn't work, and which ones work.

---

### Post by Sycron on 2008-10-10
The best opetion is to install from livecd. NOT inside Windows.

---

