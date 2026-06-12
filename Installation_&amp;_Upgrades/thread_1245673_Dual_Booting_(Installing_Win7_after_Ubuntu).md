---
title: "Dual Booting (Installing Win7 after Ubuntu)"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by TJ1234 on 2009-08-20
I think this is the right place to post this and that someone knows how to help with this. Ok, so here's how it goes I downloaded my copy of Windows 7 pro from the MSDNaa for the past year Ubuntu has been my only OS. I partitioned my hard drive and installed 7 and everything went fine. Only now when my computer starts it loads directly into 7 instead of giving me an option to go into Ubuntu or 7. I checked and both partitions are alive and well. What can I do to get the boot options back?

---

### Post by running_rabbit07 on 2009-08-20
You will have to reinstall Grub. [Check this thread out.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by presence1960 on 2009-08-20
> **running_rabbit07 said:**
> You will have to reinstall Grub. [Check this thread out.]("http://ubuntuforums.org/showthread.php?t=224351")

+1

Windows always overwtites the MBR when you install it. So Win 7 overwrote your GRUB. No biggie as running_rabbit says. Follow that tutorial and you'll be up and running. You may have to add the windows entry after Ubuntu kernels in menu.lst. post back if you need help with that.

---

