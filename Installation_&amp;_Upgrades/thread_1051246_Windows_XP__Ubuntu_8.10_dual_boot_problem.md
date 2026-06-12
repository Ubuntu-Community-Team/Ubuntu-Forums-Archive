---
title: "Windows XP / Ubuntu 8.10 dual boot problem"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by eddie001 on 2009-01-26
Hi, 

Im new to Linux and really dont have much idea what I'm doing. 

New computer a few weeks ago, decided to got with Ubuntu 8.10 64bit as OS. Partitioned the HDD to leave a 30gb space for a later Windows XP install. Linux worked fine. 

Today i was a bit bored and decided to put XP on the 30gb partition. Installation went fine except now when i turn the computer on it boots straight into XP, no option of Ubuntu. 

Used the Ubuntu CD to boot into live cd and saw the main partition and all Ubuntu files are still on the HDD (thought I may have formatted the whole thing by mistake, it is the sort of thing I would usually do)

Anyway I tried googling for answers, used something called 'auto super grub disk' which failed. Now I'm stuck using XP as I don't really want to format the whole HDD again (especially since there must be a way of solving this)

Does anyone have any idiot proof suggestions i can follow please?

---

### Post by Pumalite on 2009-01-26
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kingmonkey on 2009-01-26
Windows deleted GRUB.

Second post of this thread will help:
[http://ubuntuforums.org/showthread.php?t=521388](http://ubuntuforums.org/showthread.php?t=521388)
or this blog:
[http://ranacse05.wordpress.com/2008/01/12/grub-recovery-after-installing-windows-xp/](http://ranacse05.wordpress.com/2008/01/12/grub-recovery-after-installing-windows-xp/)

---

### Post by eddie001 on 2009-01-26
Thanks for the quick replies, I tried booting again from the live cd only now Ubuntu wont boot iget something called BusyBox v1.10.2 and 'initramfs' and I have no idea what that means :eek:

---

### Post by Pumalite on 2009-01-26
Do it again and follow this guide:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

