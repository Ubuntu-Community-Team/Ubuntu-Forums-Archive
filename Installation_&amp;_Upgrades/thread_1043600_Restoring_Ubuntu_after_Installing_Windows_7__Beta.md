---
title: "Restoring Ubuntu after Installing Windows 7  Beta"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by selman_akinci on 2009-01-18
Hello,
I had dual boot with vista for a long time, but i decided to triple boot with Windows 7 beta. But after installing Windows 7, I couldnt bring back the grub. 

I did everything this link said;
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It gave succesful install messages for grub, but still Windows Live Boot appears during start-up. I have brought ubuntu back lots of times in Vista and XP but this just fails to work for Windows 7. Please help me and I will gladly supply any information you ask.

---

### Post by Mark Phelps on 2009-01-19
That link provides several options regarding the windows boot loader.  Did you choose to overwrite it, or did you choose to preserve it?

I'm asking because I did a similar thing and discovered, quite by accident, that Windows 7 updated my Vista boot loader, not its own.  I was able to confirm that by booting into Vista, changing the boot loader options using easyBCD, and when I rebooted, the menu option names had been changed to match.

---

### Post by cariboo on 2009-01-19
I would suggest giving [Supergrub Disk]("http://www.supergrubdisk.org/") a try, that's what i used when Windows7 hosed my mbr.

Jim

---

