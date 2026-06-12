---
title: "Dual boot machine keeps restarting on boot"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by jamoo1980 on 2009-01-24
Hello

I am trying to set up my machine as a dual boot to dual boot between WinXP and Ubuntu 8.10. I've tried to install both OS's on a single SATA drive. First, I partitioned the drive using an Ubuntu LiveCD. Then, I installed WinXP on the first partition; this worked fine, I booted into Windows and everything was working as expected. I then used the LiveCD to install Ubuntu. Everything *seemed* to be fine; the install process completed without errors.

However now, when I boot the machine, it instantly restarts itself as soon as it reaches the GRUB menu. I don't have time to make any selection; in fact I only see "GRUB 1.5" for a fraction of a second before the machine re-starts; and this continues infinitely.

I've tried booting using Super Grub. If I try to boot XP, it hard freezes. If I try to boot Linux, I get "Error 13 : Invalid or unsupported executable format."

I don't think it's a hardware incompatibility, because XP was running fine, and Ubuntu runs fine when I boot it from the LiveCD (I can even browse the install of Linux on the hard drive; the one that won't boot).

Any ideas?

Thanks :)
James

---

### Post by lemming465 on 2009-01-25
The first thing I'd try is re-installing grub using the live CD.  Open a terminal window, mount the linux root partition off the hard drive, say on /media/sda3, and run something like **sudo grub-install --root-directory=/media/sda3 /dev/sda**.  I'm assuming your primary hard drive identifies as sda and you didn't make /boot be a separate partition.

---

