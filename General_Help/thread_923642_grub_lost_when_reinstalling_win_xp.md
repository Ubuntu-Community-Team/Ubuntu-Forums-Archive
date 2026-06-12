---
title: "grub lost when reinstalling win xp"
date: 2008-09-18
forum: General Help
---

### Post by arturieto on 2008-09-18
I been doing a dual boot for windows xp and ubuntu quite sometime.  However, I re-install my windows because it becomes slow on the same drive partition C:.  when I restart, everything goes to xp boot. there is no grub to select. why?  I need to boot to ubuntu because i have important files there.

please help!!

---

### Post by northern lights on 2008-09-18
Have a look at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by arturieto on 2008-09-18
i have tried to reboot as per instruction. the problem is that windows xp automatically boot. using functions did not lead to the booting of livecd. so i cannot use the terminal.

---

### Post by oilchangeguy on 2008-09-18
> **arturieto said:**
> I been doing a dual boot for windows xp and ubuntu quite sometime.  However, I re-install my windows because it becomes slow on the same drive partition C:.  when I restart, everything goes to xp boot. there is no grub to select. why?  I need to boot to ubuntu because i have important files there.

please help!!

you'll need to reinstall grub (GRand Unified Boot loader) as windows mbr (master boot record) overwrites it. simply type in the search box at the upper right of this page, reinstall grub. there are many threads on the subject.

---

