---
title: "Faster Way To Wubi"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by PGHammer on 2009-04-24
Okay; you want to dual-boot Windows and a *buntu of your choice, but you don't have (or don't want to burn) a CD (this issue would primarily be for netbooks and other portables, but it's also an issue with some older desktops).  If you have Windows XP or later in place, you're not out of luck.

Mount your *buntu ISO using the virtual-drive program of your choice (I use VirtualCloneDrive, a free such utility, for this), and run Wubi.exe from your freshly-mounted "drive".

No disc-burning needed, faster than burning a CD-R or RW, and no futzing around with GRUB, either (WUBI works with the boot loader from Windows XP/2003/Vista/2008/7 and creates an entry, properly configured, for the *buntu you chose.)  Yes, it works; I checked it out with the last pre-RC beta of Jaunty, and used it again with both the RC of Jaunty and the just-released ISO (from which I'm typing these words; Kubuntu, in my case).

---

