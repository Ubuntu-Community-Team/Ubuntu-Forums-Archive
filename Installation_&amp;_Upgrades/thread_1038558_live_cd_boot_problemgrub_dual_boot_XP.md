---
title: "live cd boot problem/grub dual boot XP"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by williamsjp2004 on 2009-01-12
I'm sorry if I have posted a resolved topic but I have searched all day to find the answer to my problem and have not found it.

I installed Ubuntu a while back and it would not boot to my XP installation. I would select to boot from grub and it would hang on the loading os screen.

I fixed the MBR with Windows XP cd and, as expected, it wiped grub. Now my problem is, when I try to boot from Ubuntu 8.10 live cd, it shows the splash screen with the Ubuntu logo then goes to something that LOOKS like a terminal screen then it tells me I have to mount the partition or something.

I want to boot to the live cd desktop so I can access the terminal and, as I understand it, give it the command to reinstall grub as follows:

sudo grub
root hd0,0
setup hd0
exit

I have tried bringning up terminal in the "command prompt" screen with ctrl+alt+F1 but to no avail.

If you can help it would be highly appreciated.

~James~

---

### Post by Pumalite on 2009-01-12
Memory? Graphics?
256 of RAM or below; better use the Xubuntu Alternate CD.

---

### Post by kranny on 2009-01-12
Dint you get the command prompt?Why dont you try booting into the safe mode

---

