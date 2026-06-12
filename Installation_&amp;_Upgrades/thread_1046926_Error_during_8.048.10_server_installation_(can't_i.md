---
title: "Error during 8.04/8.10 server installation (can't install grub)"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by essdeeay on 2009-01-21
When I try to install 8.04/8.10 server, it's failing when trying to install grub.  It fails on lilo too.  I've checked the BIOS and boot sector protection is disabled.  The disk controller is a Mylex DAC960, has 4 x 73Gb HDDs in RAID-5.  dmesg shows them all being detected ok, as is the 210Gb logical drive.  What can I do?

Many thanks,
Steve

---

### Post by essdeeay on 2009-01-23
I resolved the problem, but can't remember my *exact* steps.  However, I'll post what I did in case it helps others.

1.
Go through the installation, and choose to continue without a boot loader when you see the error, but don't restart.

2.
Press ALT+F2 to get a console.

3.
Enter the following commands:
mount -o bind /proc /target/proc
mount -o bind /dev /target/dev
mount -o bind /sys /target/sys
chroot /target

4.
At this point I manually copied the a package from a memory stick (grub_0.97-29ubuntu21_i386.deb), but you could just as easily copy it using a floppy.

5.
dpkg -i grub_0.97-29ubuntu21_i386.deb

6.
Delete the directory /boot/grub

7.
Run install-grub or grub-update (or both - I can't remember!).  Basically it will copy the relevant files into the right place, and create a menu.lst file for you.

Incidentally I also found that using the rescue mode from the CD, and jumping straight to the install bootloader section, worked successfully once it could see that the bootloader had already been installed once before (but be careful not to allow the rescue CD to format your existing partitions as you go - you'll see what I mean!).

I hope this can help someone - because it was a major headache for me.

Steve :)

---

