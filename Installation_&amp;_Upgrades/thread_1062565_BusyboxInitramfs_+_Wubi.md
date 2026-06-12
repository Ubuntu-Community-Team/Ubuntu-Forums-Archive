---
title: "Busybox/Initramfs + Wubi"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by plitanium on 2009-02-07
I'm trying to install Ubuntu 8.10 using Wubi through the Desktop ISO in the same directory. I reboot -> Ubuntu -> Start installer in normal mode. Here is the log:

Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1 ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _


Even 'exit' is not working. What is going wrong ??

---

### Post by tkoWD on 2009-10-24
How many partitions do you have on your HDD?

I had the same problem, then i changed the ubuntu folder (c:\) to the other partition and it booted up normally.

---

