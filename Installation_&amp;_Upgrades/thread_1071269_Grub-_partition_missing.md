---
title: "Grub- partition missing"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by trepid666 on 2009-02-16
Hey everyone

I just installed Ubuntu 8.04 and Gentoo 2008 onto my external HD. Then I backed up my Ubuntu and it restored my old grub, which has Ubuntu and XP as options. Now I can't boot into my Ubuntu or Gentoo.

Grub installed to Hd0,0 but my OS's are on sdb

I would also like to keep the grub thats on hd0,0 for my internal.
Please help lol

---

### Post by utnubuuser on 2009-02-16
Just google "re-install grub from liveCD ubuntu.

It's easy enough to re-install grub.

Something along the lines of: > [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
or> 1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

The partition for grub is usually designated by a slash ( /  )


---

